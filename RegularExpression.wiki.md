몰라도 상관 없지만, 알면 좋은(?) RE에 대해서 정리하겠습니다.

# 1장. 정규표현식(Regular Expression) 소개

  * 정규표현식(앞으로는 RE 라 표기)이란? : 텍스트를 찾고 조작하는 데 쓰는 문자열
  * 왜 필요한가요?
    1. 원하는 정보가 어디에 있는지 찾거나(검색),
    1. 정보를 찾은 뒤에 편집(치환)하기 위해서

> e.g) 이럴 때 사용합니다!
    1. 대소문자를 구별하지 않고 car 라는 텍스트가 포함된 파일을 찾는데, 단어 중간에 car가 들어있는 경우를 제외하고 싶다(scar, carry, incarcerate 등).
    1. 소스코드를 수정하다가 size라는 글자를 모두 iSize로 치환하고자 한다. 하지만 다른 단어 사이에 size라는 철자가 포함된 경우는 제외하고 오직 size라는 단어만 치환하고 싶다.
    1. 날짜나 전화번호, 주민등록번호 같은걸 찾을때도 유용합니다. 특히 들어오는 데이터의 양식이 다를 수 있을때 매우 유용합니다. 예를 들어 010-1234-5678 이라고 입력되었거나, 01012345678 이라고 입력되어있을때 둘 모두 전화번호로 찾도록 할 수도 있지요. 예를 들여, 정규표현식 **010-?[0-9]{3,4}-?[0-9]{4}**는 010-1234-5678, 010-4567-8415, 010-123-4568, 01078945562 과 같은 표현들을 한번에 찾을 수 있고, 000-4526-5687를 제외시킵니다.

> c.f) http://www.forta.com/books/0672325667/ (웹기반RE 검사기 소스 다운로드)

> http://www.sweeting.org/mark/html/revalid.php (온라인 검사기)

# 2장. 문자 하나 찾기

> - 정규 표현식 혹은 패턴은 문자들로 이루어진 문자열이다. 이러한 문자들은 그냥 의미 그대로의 문자(text)일 수도 있고 메타문자(특별한 의미를 지닌 특수 문자)일 수도 있다. 문자열에서 한 문자를 찾는 방법은,

  * 모든 문자 찾기 : . (마침표)
> > - 마침표 문자는 아무 문자 하나와 일치한다. (c.f. 도스에서의 ?(물음표)문자)
  * 특수 문자 찾기 : \ (역슬래쉬)
> > - 마침표를 찾고 싶을 때 \.
> > - 역슬래쉬를 찾고 싶을 때 \\

> - 메타문자(특수문자)는 6장에서 조금 더 나옵니다.

# 3장. 문자 집합으로 찾기
_to-be continued 하루에 한 장씩 (총 10장)_


---

참조 : 손에 잡히는 정규 표현식, 인사이트, 벤 포터 지음, 김경수 옮김