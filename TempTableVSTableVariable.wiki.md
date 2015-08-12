# SQL Server에서 임시테이블과 테이블변수의 차이점

## 공통점

  * tempdb에 생성된다.

  * Clustered 인덱스를 생성할 수 있다.

  * 트랜잭션 로그가 생성된다.

  * 일반테이블처럼 select, insert, update, delete 쿼리문을 실행할 수 있다.


## 차이점

  * 테이블변수에는 Non-clustered 인덱스를 만들 수 없다.

  * 테이블변수에는 FK와 같은 제약조건을 만들 수 없다.

  * 테이블변수에는 기본값을 설정할 수 없다.

  * 통계정보가 만들어지지 않는다.


## 성능

많은 데이터를 처리할 경우, 임시테이블이 조금 더 나은 성능을 보인다.


---


http://www.mssqltips.com/sqlservertip/1556/differences-between-sql-server-temporary-tables-and-table-variables/

http://www.mssqltips.com/sqlservertip/2825/sql-server-temp-table-vs-table-variable-performance-testing/