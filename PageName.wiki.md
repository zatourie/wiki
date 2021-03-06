2015.05.06	심민규,이정훈	한글->로마자 변환, 세벌식 자판

# DB쿼리로 한글 이니셜화하기

## 환경
  * MS SQL Server 2012+

## Rominiser
```

/*
 * 한글을 로마표기로 바꿔주는 함수
 * 작성자 : 심민규 
 * 작성일 : 2015.4.30
 * 참  조 : 국립국어원 로마자표기법 : http://www.korean.go.kr/front/page/pageView.do?page_id=P000149&mn_id=99
 *          한글 모음 유니코드 :  http://hanpsy.tistory.com/2
 *          aliencube Hangeul Romaniser : https://github.com/aliencube/Hangeul-Romaniser
 */
CREATE FUNCTION dbo.FN_ROMANISER (
   @pLetter NCHAR (1)
)
   RETURNS VARCHAR (1)
AS

BEGIN
	DECLARE @RETURN_DATA VARCHAR (5)
      
	SET @RETURN_DATA = ''
  
	SELECT @RETURN_DATA = 
		CASE ( (UNICODE(@pLetter) - 44032)  / (21*28) ) --초성코드 구하기
			WHEN 0 THEN 'K'   --ㄱ
			WHEN 1 THEN 'KK'   --ㄲ
			WHEN 2 THEN 'N'   --ㄴ
			WHEN 3 THEN 'D'   --ㄷ
			WHEN 4 THEN 'T'   --ㄸ   
			WHEN 5 THEN 'R'   --ㄹ   
			WHEN 6 THEN 'M'   --ㅁ   
			WHEN 7 THEN 'B'   --ㅂ   
			WHEN 8 THEN 'P'   --ㅃ   
			WHEN 9 THEN 'S'   --ㅅ   
			WHEN 10 THEN 'S'  -- ㅆ  
			WHEN 11 THEN ''   --ㅇ   
			WHEN 12 THEN 'J'  --ㅈ   
			WHEN 13 THEN 'J'  --ㅉ
			WHEN 14 THEN 'CH'  --ㅊ
			WHEN 15 THEN 'K'  --ㅋ
			WHEN 16 THEN 'T'  --ㅌ
			WHEN 17 THEN 'P'  --ㅍ
			WHEN 18 THEN 'H'  --ㅎ
			ELSE ''
		END

	SELECT @RETURN_DATA = @RETURN_DATA + 
		CASE ( ((UNICODE(@pLetter) - 44032)  % (21*28)) / 28 ) --중성코드 구하기
			WHEN 0 THEN 'A'   --ㅏ
			WHEN 1 THEN 'AE'   --ㅐ
			WHEN 2 THEN 'YA'   --ㅑ
			WHEN 3 THEN 'YAE'   --ㅒ
			WHEN 4 THEN 'EU'   --ㅓ   
			WHEN 5 THEN 'E'   --ㅔ
			WHEN 6 THEN 'YEO'   --ㅕ  
			WHEN 7 THEN 'YE'   --ㅖ   
			WHEN 8 THEN 'O'   --ㅗ   
			WHEN 9 THEN 'WA'   --ㅘ   
			WHEN 10 THEN 'WAE'  --ㅙ  
			WHEN 11 THEN 'OI'  --ㅚ  
			WHEN 12 THEN 'YO'  --ㅛ 
			WHEN 13 THEN 'WOO'  --ㅜ   
			WHEN 14 THEN 'WUE'  --ㅝ
			WHEN 15 THEN 'WAE'  --ㅞ
			WHEN 16 THEN 'YUI'  --ㅟ
			WHEN 17 THEN 'YU'  --ㅠ
			WHEN 18 THEN 'E'  --ㅡ
			WHEN 19 THEN 'EU'  --ㅢ
			WHEN 20 THEN 'I'  --l
			ELSE ''
		END

	SELECT @RETURN_DATA = @RETURN_DATA + 
		CASE ( (UNICODE(@pLetter) - 44032) % 28 ) --종성코드 구하기
			WHEN 0 THEN ''   --X
			WHEN 1 THEN 'K'   --ㄱ
			WHEN 2 THEN 'KK'   --ㄲ
			WHEN 3 THEN 'K'   --ㄳ
			WHEN 4 THEN 'N'   --ㄴ
			WHEN 5 THEN 'N'   --ㄵ   
			WHEN 6 THEN 'N'   --ㄶ   
			WHEN 7 THEN 'T'   --ㄷ   
			WHEN 8 THEN 'L'   --ㄹ   
			WHEN 9 THEN 'L'   --ㄺ   
			WHEN 10 THEN 'L'  --ㄻ   
			WHEN 11 THEN 'L'  --ㄼ  
			WHEN 12 THEN 'L'   --ㄽ  
			WHEN 13 THEN 'L'  --ㄾ   
			WHEN 14 THEN 'L'  --ㄿ
			WHEN 15 THEN 'L'  --ㅀ
			WHEN 16 THEN 'M'  --ㅁ
			WHEN 17 THEN 'P'  --ㅂ
			WHEN 18 THEN 'P'  --ㅄ
			WHEN 19 THEN 'T'  --ㅅ
			WHEN 20 THEN 'T'  --ㅆ
			WHEN 21 THEN 'NG'  --ㅇ
			WHEN 22 THEN 'T'  --ㅈ
			WHEN 23 THEN 'T'  --ㅊ
			WHEN 24 THEN 'CH'  --ㅋ
			WHEN 25 THEN 'T'  --ㅌ
			WHEN 26 THEN 'P'  --ㅍ
			WHEN 27 THEN 'H'  --ㅎ
			ELSE ''
		END
        
	RETURN @RETURN_DATA
END

```

## Initializer

```

/*
 * 한글 문자열을 영문 이니셜로 바꿔주는 함수
 * 작성자 : 심민규 
 * 작성일 : 2015.4.30
 */
CREATE FUNCTION dbo.FN_GET_INITIAL (
   @pString NVARCHAR (10)
)
   RETURNS VARCHAR(10)
AS
BEGIN

	/* Declare variables */
	DECLARE @letter NCHAR(1)
	DECLARE @pos INT
	DECLARE @RETURN_DATA VARCHAR(10)

	/* Initialize variables */
	SET @pos = 0
	SET @RETURN_DATA = ''
	
    WHILE @pos != LEN(@pString)
	BEGIN
		SET @pos = @pos + 1			
		SET @letter = SUBSTRING(@pString, @pos, 1)
		SET @RETURN_DATA = CONCAT( @RETURN_DATA, LEFT(dbo.FN_ROMANISER(@letter),1) ) --이니셜을 위해 앞 한글자만
    END  
	

	RETURN (@RETURN_DATA)
END

```

## 사용법

```
SELECT dbo.FN_ROMANISER('홍') --HONG
SELECT dbo.FN_GET_INITIAL('홍길동') --HKD
```