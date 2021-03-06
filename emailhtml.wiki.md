5/13 (수) 발제 : 심민규

# Email HTML & DB에서 쿼리로 HTML 생성하기

## Email HTML

### 개요

  * 이메일 클라이언트들이 preprocessing해서 메일내용을 수정하기 때문에 보낸 html의 양식이 깨지게 됨.
  * preprocessor를 피해가려면 inline css를 써야함.


### 아름다운 이메일을 위한 TIP

  * 엑셀이나 파워포인트에서 아름답게 그린다.
  * outlook에 붙여넣고 메일로 보낸다음, 소스보기하여 아웃룩이 만들어준 Email HTML을 활용
  * css로 되어있는 스타일을 태그에 밀어넣어주는 서비스 활용 http://templates.mailchimp.com/resources/inline-css/

## 쿼리로 HTML 생성하기

```
CREATE TABLE dbo.USER_TABLE
(
USER_ID varchar (20) COLLATE Korean_Wansung_CI_AS NOT NULL,
USER_NM varchar (200) COLLATE Korean_Wansung_CI_AS NULL
) 

insert into dbo.USER_TABLE (USER_ID, USER_NM) values ('1111','John Do')
insert into dbo.USER_TABLE (USER_ID, USER_NM) values ('2222','Jane Do')

--Generate TR, TD
DECLARE @table_html NVARCHAR(MAX) = (
  SELECT 
    USER_ID 'tdleft', ''
    , USER_NM 'tdright', '' 
  FROM dbo.USER_TABLE
  FOR XML PATH ('tr')
)
--Replace for Inline CSS
SET @table_html = REPLACE(@table_html, '<tr>', '<tr style="box-sizing:border-box;" >')
SET @table_html = REPLACE(@table_html,'<tdleft>', '<td style="border:solid gray 1.0pt;border-top:none;text-align:left;font-size:9.0pt;">')
SET @table_html = REPLACE(@table_html,'<tdright>', '<td style="border:solid gray 1.0pt;border-top:none;text-align:right;font-size:9.0pt;">')
SET @table_html = REPLACE(@table_html,'<tdcenter>', '<td style="border:solid gray 1.0pt;border-top:none;text-align:center;font-size:9.0pt;">')

SET @table_html = REPLACE(@table_html, '</tdleft>','</td>')
SET @table_html = REPLACE(@table_html, '</tdright>','</td>')
SET @table_html = REPLACE(@table_html, '</tdcenter>','</td>')

SELECT @table_html
```

http://sqlfiddle.com/#!6/740ef/8/0

## Reference

코드스쿨 Email HTML 강의
https://www.codeschool.com/courses/unmasking-html-emails

이메일 테스트 서비스 litmus.com 유료 월 8만원 정도 7일 무료