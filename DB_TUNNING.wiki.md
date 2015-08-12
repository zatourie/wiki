일시 : 2013.6.5 (수) 11:00~12:00

작성자 : 이정훈, 심민규, 김형태

# DB 튜닝

## DB 튜닝이란?

개발/운영단에서 할 수 있느 DB 튜닝은 주로 쿼리 튜닝임.

쿼리 튜닝의 목적은 가장 효율적으로 정확한 데이터를 빠르게 조회하는 것.


## 튜닝에 필요한 기초지식

### Database의 동작

INSERT/UPDATE/DELETE시에 그냥 데이터를 고치는 것만이 아니다.

트랜잭션 처리나 복구를 위해 처리하는 부분이 있음

참고로 INSERT/UPDATE/DELETE 중 UPDATE가 가장 Database의 비용을 많이 소모

### Optimizer, query plan, index, scan/seek

Optimizer : 사용자의 쿼리를 받아서 어찌저찌 가장 효율적인 계획(Plan)을 세워서 실행하는 녀석

Query Plan : 그 계획(Plan)

Index : 색인 (인덱스와 데이터의 관계는 포인터와 실제 instance의 관계와 흡사)

Index Scan / Seek : Scan? Seek?

Query의 실행계획 : Schema 정보와 통계정보를 이용하여 실행계획을 세운다.

### Tuning의 기본

쿼리 Tuning의 기본은 Index를 사용하는 것이다.

어떤 index를 어떻게 사용하는지가 중요하다.

### Index 란

Index는 목차와 같은 것

Unique Index와 Non-Unique Index가 있다. (가능하면 Unique Index를 사용하자)

**MSSQL에서는 Clustered index, Non clustered index**

### Index가 빠른 이유

데이터의 양이 적으니까(목차니까 당연히 데이터 양이 적다)

정렬되어 있으니까(다 안찾아보고, Binary Search 가 가능하다.)

### Index 선정 시 주의사항

분포도를 체크한다. (분포도가 좋지 않은 것은 인덱스를 써도 크게 효율이 안 날 수 있다)

중복된 Index가 있나 체크한다. (중복된 Index는 공간의 낭비로, 그 경우 컬럼을 묶어 Composite Index를 사욯하는 것이 좋다)


### 지양해야할 것들

  * 묻지마 Distinct : 중복 데이터를 제거하기 위한 비용이 들어간다.
  * 섣부른 Sort : 정렬을 위한 비용이 (꽤많이, 불필요하게) 들어간다.
  * 나몰라 Heap Table : 인덱스를 적절히 활용하자.
  * 일편단심 Cursor : Table 단위의 insert, update가 더 성능이 좋다.
  * 별을 따줘 Select `*` : Table schema 변경에 쿼리가 영향 받지 않을 수 있는 장점이 있으나, 성능상 문제가 있을 수 있으니 잘 판단할 것.

Heap Table : 인덱스가 없는 테이블


### Index를 사용하지 못하게 하는 쿼리(Oracle 기준)
  * Index 컬럼의 수식이 걸려 있는 경우
```

-- sal에 index가 걸려있으나 사용하지 못함
select name from emp
where sal * 1.2 > 1000

-- 사용할 수 있게 수정
select name from emp
where sal > 1000 /1.2
```


  * Index 컬럼의 함수 연산이 있을 경우
```

-- name에 index가 걸려있으나, 사용 불가
select name from emp
where substr(name, 1, 1) = 'S'

-- index 사용 가능
select name from emp
where name like 'S%'
```


  * OR 등으로 컬럼 연산을 할 경우
```

-- tel1, tel2, tel3에 index가 걸려 있으나 사용 불가
-- 이 경우는 업무적으로 풀어야 함
select name from emp
where tel1||tel2||tel3 = '0101234456'
```


  * 컬럼 type 이 다를 경우 (number, date 가 우선)
```

-- cust_no는 varchar 타입이고, index가 걸려있다.
-- 하지만 조건의 12345는 number 타입으로, 이 경우 12345 -> '12345'로 변하지 않고,
-- cust_no가 먼저 number type으로 변경 후 비교한다. 그래서 index를 사용하지 못한다.
select * from customer
where cust_no = 12345
```

## 여기서부터는 MSSQL Management Studio만해당

### 유용한 TIP

1. 테이블명을 선택하고 ALT+F1하면 테이블 정보를 볼 수 있음

혹은

```
sp_helpindex 테이블명
```


2. CPU Intensive Queries

CPU를 많이 사용하는 쿼리를 통계에서 뽑아 보여준다. 튜닝 포인트라고 생각하면 된다.

```
SELECT TOP (30)
        RANK() Over (ORDER BY deqs.total_worker_time DESC) As [Rank],
        CONVERT(decimal(38,2), CONVERT(float, total_worker_time) / 1000) AS [Total CPU Time (ms)],
        execution_count AS [Execution Count],
        CONVERT(decimal(38,2), (CONVERT(float, total_worker_time) / execution_count) / 1000) AS [Average CPU Time (ms)] ,
        SUBSTRING(execText.text,
          -- starting value for substring 
          CASE WHEN deqs.statement_start_offset = 0 
             OR deqs.statement_start_offset IS NULL 
               THEN 1 
               ELSE deqs.statement_start_offset/2 + 1 END,
          -- ending value for substring
          CASE WHEN deqs.statement_end_offset = 0 
            OR deqs.statement_end_offset = -1 
            OR deqs.statement_end_offset IS NULL 
               THEN LEN(execText.text) 
               ELSE deqs.statement_end_offset/2 END - 
                 CASE WHEN deqs.statement_start_offset = 0 
                   OR deqs.statement_start_offset IS NULL 
                     THEN 1 
                     ELSE deqs.statement_start_offset/2  END + 1
        ) AS [Query Text],
        execText.text AS [Object Text]
FROM    sys.dm_exec_query_stats deqs
        CROSS APPLY sys.dm_exec_sql_text(deqs.plan_handle) AS execText
ORDER BY deqs.total_worker_time DESC ;
```

3. 쿼리 플랜 보기

<a href='http://www.youtube.com/watch?feature=player_embedded&v=LXyxDvznVaY' target='_blank'><img src='http://img.youtube.com/vi/LXyxDvznVaY/0.jpg' width='425' height=344 /></a>

4. SQL Server Management Studio 2012 Column Mode

쿼리 에디트 창에서 Alt키를 누르고 마우스 Drag

5. CROSS APPLY

6. WITH (NOLOCK) Hint

Dirty Read 혹은 Read Uncommitted

7. Common Table Expression

8. View with schemabinding

9. Temp table vs. Table variable

10. Prefer System function to user defined function

특히, 날짜 계산 같은 것.

```
SELECT LEFT(CONVERT(CHAR(8), getdate(), 112),4) -- output : 2014

SELECT DATENAME(year, GETDATE()) -- output : 2014

SELECT YEAR(GETDATE()) -- output : 2014
```

11. Filtered Index (SQL Server 2008 + )

특정 데이터에만 인덱스를 걸어서 인덱스 테이블 크기를 줄이는 기법

```
CREATE NONCLUSTERED INDEX FIBillOfMaterialsWithEndDate
    ON Production.BillOfMaterials (ComponentID, StartDate)
    WHERE EndDate IS NOT NULL ;
```

12. nonkey (or include) columns

https://code.google.com/p/zatouri/wiki/mssqlindexinclude

`SQL Server 2005 provided a new feature for nonclustered indexes, the ability to include additional, non-key columns in the leaf level of the nonclustered indexes. These columns are technically not part of the index, however they are included in the leaf node of the index. SQL Server 2005 and SQL Server 2008 allow up to 1023 columns to be included in the leaf node.`

https://www.simple-talk.com/sql/learn-sql-server/using-covering-indexes-to-improve-query-performance/


## 10/22일 스터디 내용

발제자 : SHAPE

1.     Sql Server 재부팅 후 성능저하 이슈 관련 토론
A.     쿼리 수정으로 극복 가능한 경우 일 수 있음
B.     재부팅 전 만든 인덱스가 잘못 되었을 가능성 있음
C.     이와 관련된 통계, 인덱스 관련 쿼리

```
/* 테이블 조각화 조회 - 밀도가 90%에 미치지 못하면 인덱스 재생성을 해야한다고 함 */
DBCC showcontig(tb_mst_quot)
 
/* 인덱스 조각모음 - 테이블 크기가 클경우 인덱스 단위로 실행 */
DBCC dbreindex(tb_mst_quot)
 
/* 통계 Update */
UPDATE STATISTICS tb_mst_quot
 
/* 전체 통계 Update */
EXEC sp_updatestats;
 
/* 인덱스 Rebuild */
ALTER INDEX PK_TB_MST_QUOT_1 ON tb_mst_quot
REBUILD;
```

2.     CrossApply 시연 (서브쿼리와 성능비교 및 Multi Unpivot) – 지난 주 메일 첨부 참고
3.     파라미터 스니핑 및 극복방안 – 추후 좀더 자세히 정리할 필요성 있음.
4.     시스템 상에서 사용자가 Excel로 데이터를 Upload 하는 방법 토론
A.     우선, Excel을 Local에서 읽을 것이냐, FTP를 이용하여 서버에 Upload 한 후 처리할 것인지 결정
B.      일반적으로 Excel을 DataTable로 만들어서 Row를 하나씩 Insert 쿼리로 태움 à SP Call 이 많아져 성능이 낮고, Timeout발생할 수 있음
C.      **DataTable을 XML로 변환하면, SP Call 1번으로 데이터 저장이 가능
D.** 엑셀을 서버에 올린 경우 Openrowset을 이용하여 DB상에서 Table로 읽어서 Insert 할 수 있음
5.     SP, FN 등 장문의 쿼리에서 튜닝포인트 잡아내는 요령
A.     Print 문을 이용하여 구분자를 표시한다.
B.      쿼리 실행 옵션을 이용하여 쿼리 실행

```
set statistics io on
set statistics time on 
--쿼리문..
exec USP_HEDGE_FRM301300_SELECT '2014','20140806'
set statistics time off        
set statistics io off
```

C.      문제 부분을 발췌하여 실행계획 분석(인덱스를 타는지 여부, 어떤 인덱스를 타는지 여부 등)

파라미터 스니핑(Parameter Sniffing)

http://www.brentozar.com/archive/2013/06/the-elephant-and-the-mouse-or-parameter-sniffing-in-sql-server/