# 두번째 주제: Client/Server vs WEB

일시/장소 : 4/4(목) 11:00~ / 튜울립

## **Web은 새로운 C/S다.**

Client-Server Model

> 클라이언트 서버 시스템(Client/Server System, 약칭 C/S 시스템)은 클라이언트와 서버로 나뉘는 네트워크 아키텍처를 나타낸다. 웹 시스템도 확장된 '클라이언트 서버 시스템'으로 분류되나, 일반적으로는 클라이언트 서버 시스템이라고 하면 웹 시스템이 나오기 이전의, 사용자 PC에는 클라이언트가 설치되어 화면을 처리하고 서버에서는 자료를 처리하는 시스템을 일컫는다.

![https://upload.wikimedia.org/wikipedia/commons/thumb/c/c9/Client-server-model.svg/468px-Client-server-model.svg.png](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c9/Client-server-model.svg/468px-Client-server-model.svg.png)

<sub>그럼 C/S가 아닌건 뭐냐?</sub>

![http://blog.gogrid.com/wp-content/uploads/2009/05/image-thumb.png](http://blog.gogrid.com/wp-content/uploads/2009/05/image-thumb.png)

http://en.wikipedia.org/wiki/TCP/IP

![http://i.technet.microsoft.com/dynimg/IC213263.gif](http://i.technet.microsoft.com/dynimg/IC213263.gif)


## Web의 특징

Web Browser / Server 아키텍처 (그림있으면 좋겠는데...)

  * Protocol : HTTP/HTTPS
  * Client : 웹브라우저
  * Data : HTML
  * Presentation : CSS
  * Behavior : Javascript

### Hyper Text Transfer Prococol (HTTP)

Internet Engineering Task Force (IETF)와 the World Wide Web Consortium (W3C)에서 관리

http://tools.ietf.org/html/rfc2616


### Hyper Text Markup Language(HTML)

W3C에서 관리

  * 4.01 Stable http://www.w3.org/TR/1999/REC-html401-19991224/
  * 5.1 draft http://www.w3.org/html/wg/drafts/html/master/

궁금해서 현재 영향력있는 인터넷 기업들의 메인 페이지를 W3C Validator로 돌려보았습니다.

구글도 20개 정도의 오류가 있구요. MS는 ㅎㅎㅎ
오픈소스 재단답게 Mozilla는 Pass 입니다.
그리고 놀랍게도 (다음 직원들께 죄송!) 다음 메인 페이지도 Pass!


![http://zatouri.googlecode.com/files/google.png](http://zatouri.googlecode.com/files/google.png)

![http://zatouri.googlecode.com/files/ms.png](http://zatouri.googlecode.com/files/ms.png)

![http://zatouri.googlecode.com/files/mozilla.png](http://zatouri.googlecode.com/files/mozilla.png)

![http://zatouri.googlecode.com/files/naver.png](http://zatouri.googlecode.com/files/naver.png)

![http://zatouri.googlecode.com/files/daum.png](http://zatouri.googlecode.com/files/daum.png)





### Javascript

Ecma International에서 관리하고 ECMAScript라고도 불립니다.

http://en.wikipedia.org/wiki/Ecma_International


### CSS

W3C에서 관리
현재 Published 버전 CSS2.1
CSS4작업중

http://tools.ietf.org/html/rfc2318


---


# Quiz

Equals?

```java

String str1 = new String("I'm string");
String str2 = new String("I'm string");

if(str1 == str2){
System.out.println("Hi");
}else {
System.out.println("Hoy");

}
//Hi일까요 Hoy일까요?
```

힌트: Value vs. Reference

위 코드를 자바에서 실행시키면 Hoy가 나옵니다.
C#에서 비슷한 코드를 실행시키면 Hi가 나오죠.

이것은 "==" 연산자가 string 값을 만나면 서로 다르게 동작하기 때문이에요.
Java에서 "==" 연산자는 참조비교(reference comparison)을 하는 반면,
C#에서 "==" 연산자는 값비교(Value comparison)을 합니다.

이것을 두고 프로그래머들 사이에 논쟁이 많은데요. Java string도 "=="연산을 하면 값비교를 해야한다는 의견이 많습니다. 그도 그럴 것이 string을 비교하는데 참조비교를 하는 경우가 과연 있을까 싶기 때문에 수긍이 가는 주장이기도 합니다.

하지만 반면, 아래와 같은 반박도 있습니다. Java에서 모든 객체에서 "=="연산자가 일관되게 동작한다는거죠. C#에서는 string은 객체이지만 다른 객체들과 "==" 연산자가 다르게 동작하므로 혼란스러울 수 있단 겁니다. 일각에서 주장되는 연산자 오버로딩 기능으로 해결될 문제가 아니라 컴파일러가 string을 값비교하도록 해결하는게 좋겠다는 아이디어도 좋네요.

I guess it's just consistency, or "principle of least astonishment". String is an object, so it would be surprising if was treated differently than other objects.

At the time when Java came out (~1995), merely having something like String was total luxury to most programmers who were accustomed to representing strings as null-terminated arrays. String's behavior is now what it was back then, and that's good; subtly changing the behavior later on could have surprising, undesired effects in working programs.

As a side note, you could use String.intern() to get a canonical (interned) representation of the string, after which comparisons could be made with ==. Interning takes some time, but after that, comparisons will be really fast.

Addition: unlike some answers suggest, it's not about supporting operator overloading. The + operator (concatenation) works on Strings even though Java doesn't support operator overloading; it's simply handled as a special case in the compiler, resolving to StringBuilder.append(). Similarly, == could have been handled as a special case.

Then why astonish with special case + but not with ==? Because, + simply doesn't compile when applied to non-String objects so that's quickly apparent. The different behavior of == would be much less apparent and thus much more astonishing when it hits you.

http://programmers.stackexchange.com/questions/193638/why-didnt-operator-string-value-comparison-make-it-to-java/193640#193640


---

Reference

https://en.wikipedia.org/wiki/Client%E2%80%93server_model

https://ko.wikipedia.org/wiki/%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8_%EC%84%9C%EB%B2%84_%EC%8B%9C%EC%8A%A4%ED%85%9C

http://en.wikipedia.org/wiki/TCP/IP

https://www.alljoyn.org/about