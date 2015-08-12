# Encoding (인코딩)

## 한눈에 보는 한글 인코딩

![http://heartonbit.byus.net/tc/attach/1/2036217031.png](http://heartonbit.byus.net/tc/attach/1/2036217031.png)


## ASCII (American Standard Code for Information Interchange)

0 ~ 127 : 128개 Binary code에 문자를 매핑한 것

![http://www.ncus.org.uk/images/CHARS.gif](http://www.ncus.org.uk/images/CHARS.gif)

## Extended ASCII

128 ~ 255 의 나머지 128개 code에 문자를 매핑한 것

![http://www.webopedia.com/FIG/EXT-ASC.gif](http://www.webopedia.com/FIG/EXT-ASC.gif)


## ASCII의 특징

  * ASCII문자셋은 1 Bytes를 한 문자로 표현 (예 a -> 0x61 97)
  * 256개의 문자를 표현가능
  * 한국어, 중국어, 일본어 (통칭 CJK)는 표현할 수 없음

**ASCII문자셋에 없는 외국어는 어떻게하나?**

## 한국어의 문자열 표현방법

### 2 바이트 완성형

한글 한글자를 2 Bytes 에 매핑하는 방식

예) 가 -> 0xB0A1 45217

  * ASCII 영역과 겹치지 않도록 첫 번째 비트 값을 1로 규정하였으므로, KS C 5601 표준안은 0xA1A1부터 0xFEFE까지의 영역(94x94, 8,836글자)만을 사용
  * 이중 한글에 2,350코드 할당
  * 표현 불가능한 한글 존재 예) 뷁

### 확장 완성형

MS에서 독자적으로 만든 방식. 2바이트 완성형에 8,822자를 추가

### EUC-KR vs CP949

  * EUC-KR은 2바이트 완성형
  * CP949는 확장 완성형

참고 : Java에서는 CP949와 MS949를 다르게 취급한다. CP949는 IBM에서 처음 지정한 코드 페이지(sun.nio.cs.ext.IBM949)가 기준이고 Microsoft가 제정한 확장 완성형은 MS949(sun.nio.cs.ext.MS949)를 기준이다. 그러므로 Java에서는 CP949와 EUC-KR이 사실상 같으며, 확장 완성형을 사용하기 위해서는 MS949로 지정해야 한다.




### 기존 문자표현 방식의 문제

  * 2가지 이상의 코드페이지를 동시에 표현할 수 없음
  * 그래서 만들어진 **유.니.코.드**

### 유니코드란?

  * 전 세계적으로 사용되는 모든 문자 집합을 하나로 모아 탄생시킨 것
  * 유니코드는 공식적으로 31비트 문자 집합이지만 현재까지는 21비트 이내로 모두 표현이 가능

예) A -> U+0041 혹은 \u0041

  * 표현가능한 문자수 : 1,111,998 개
  * 현재 문자수 : 109,384 (6.0버전 기준)

### UTF-8? UTF-16

  * 유니코드의 인코딩 방식
  * ASCII와 호환이 가능하면서 유니코드를 표현할 수 있는 UTF-8 인코딩이 가장 많이 사용된다.
  * 다음 표는 코드 포인트 범위에 따른 UTF-8 인코딩 방식을 보여준다.

```
U+0000~U+007F     그대로 인코딩 (US-ASCII)

U+0080~U+07FF     110xxxxx 10xxxxxx

U+0800~U+FFFF     1110xxxx 10xxxxxx 10xxxxxx (한글 완성형)

U+10000~U+1FFFFF  11110xxx 10xxxxxx 10xxxxxx 10xxxxxx
```


참고 : UTF-16(16-bit Unicode Transformation Format)은 유니코드 문자 인코딩 방식의 하나이다. 주로 사용되는 기본 다국어 평면 (BMP, Basic multilingual plane)에 속하는 문자들은 그대로 16비트 값으로 인코딩이 되고 그 이상의 문자는 특별히 정해진 방식으로 32비트로 인코딩이 된다.


---


참고자료

한글 인코딩의 이해 1편: 한글 인코딩의 역사와 유니코드
http://helloworld.naver.com/helloworld/19187

한글 인코딩의 이해 2편: 유니코드와 Java를 이용한 한글 처리
http://helloworld.naver.com/helloworld/76650

Wikipedia Charset detection
http://en.wikipedia.org/wiki/Charset_detection

위키피디아 한글 인코딩
http://ko.wikipedia.org/wiki/%EB%AC%B8%EC%9E%90_%EC%9D%B8%EC%BD%94%EB%94%A9

What Every Programmer Absolutely, Positively Needs To Know About Encodings And Character Sets To Work With Text
http://kunststube.net/encoding/
