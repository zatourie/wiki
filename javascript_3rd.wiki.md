  * 일시 : 2014.3.12 (수) 11:00~12:00 / 개나리
  * 발제 : 이소윤
  * 교제 : Javascript : the good part
  * 진도 : Chapter 3 Object 뒷부분
  * 내용
    * 
  * 밑줄
    * Every object is linked to a prototype object from which it can inherit properties. All objects created from object literals are linked to Object.prototype, an object that comes standard with JavaScript
    * The prototype link is used only in retrieval.
    * If we try to retrieve a property value from an object, and if the object lacks the property name, then JavaScript attempts to retrieve the property value from the prototype object. And if that object is lacking the property, then it goes to its prototype, and so on until the process finally bottoms out with Object.prototype. If the desired property exists nowhere in the prototype chain, then the result is the undefined value. This is called **delegation**.
    * Functions in JavaScript are objects. **Objects are collections of name/value pairs having a hidden link to a prototype object**.



---

Reference