  * 일시 : 2014.3.5 (수) 11:00~12:00 / 개나리
  * 발제 : dony
  * 교제 : Javascript : the good part
  * 진도 : Chapter 3 앞부분
  * 내용
    * JavaScript에서의 Object Literal의 이해
    * Immutability 란?
  * 밑줄
    * 민규
      * **The || operator can be used to fill in default values:
```
var middle = stooge["middle-name"] || "(none)";
```
      *** Attempting to retrieve values from undefined will throw a TypeError exception. This can be guarded against with the && operator:
```
flight.equipment.model //throw TypeError
flight.equipment && flight.equipment.model //undefined
```
      * **Objects are passed around by reference. They are never copied.**


---

Reference

Javascript Immutability

http://stackoverflow.com/questions/16115512/understanding-javascript-immutable-variable