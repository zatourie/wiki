  * 일시 : 2014.4.2 (수) 11:00~12:00 / 개나리
  * 발제 : 심민규
  * 교제 : Javascript : the good part
  * 진도 : Chapter 4 Function 챕터 남은 부분
  * 내용 :
    * Callback
    * Module
    * Cascade
    * Curry
    * Memoization
  * 밑줄

```
var Module = (function(){
    var privateProperty = 'foo';
    
    function privateMethod(args){
        // do something
    }

    return {

        publicProperty: "",

        publicMethod: function(args){
            // do something
        },

        privilegedMethod: function(args){
            privateMethod(args);
        }
    }
})();
```

---

참조

  * http://en.wikipedia.org/wiki/Currying

  * http://ryanmorr.com/understanding-scope-and-context-in-javascript/

  * https://developers.google.com/chrome-developer-tools/docs/javascript-debugging