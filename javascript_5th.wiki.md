  * 일시 : 2014.3.27 (목) 11:00~12:00 / 개나리
  * 발제 : 김영
  * 교제 : Javascript : the good part
  * 진도 : Chapter 4 Funtion p58~70
  * 내용 :

1. 예외처리:별거없음. 자바와다르게 catch구문 여러게 못씀.

2. 재귀: 자바스크립트는 tail recursion 최적화가 안되니 stack overflow 조심해야함

3. scope:block스코프X, function스코프를 가짐

ex)
```
function f1(){
    for(var i = 0 ; i < 3 ; i++){
        var sum+=i;
    }
    alert(sum); //3
}
```
> 블록 스코프라면 alert에서 undefined가 뜰 테지만
> function스코프라 for문 block 밖에서도 조회가 가능하다.

4. closure:function 스코프를 가진 변수를 function 밖에서도 접근이 가능하게 해 줌. 은닉성.인캡슐레이션에 이용됨


  * 밑줄
    * 소윤
      * Recursive functions can be very effective in manipulating tree structures such as the browser's Document Object Model(DOM).
      * Unfortunately, JavaScript does not currently provide tail recursion optimization. Functions that recurse very deeply can fail by exhausting the return stack.
      * JavaScript does have function scope.
      * So, it is best to declare all of the variable used in a function at the top of the function body.
    * 민규
      * An inner function also enjoys access to the parameters and variables of the functions it is nested within. The function object created by a function literal contains a link to that outer context. This is called **closure**.


---

참조

  * 자바스크립트의 클로저 (JavaScript's Closure) http://blog.javarouka.me/2012/01/javascripts-closure.html

  * 클로저(Closure) 사용에는 주의가 필요합니다 http://blog.javarouka.me/2012/01/closure.html

  * Javascript try catch 구문
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch