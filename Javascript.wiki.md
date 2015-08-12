일시/장소 : 4/10 (수) 1100~1200 / SK서린

# DOM (Document Object Model)

## DOM이란?

DOM : Document Object Model

```
<HTML>
<BODY>
<P ALIGN="right">
This is a <B>paragraph</B>
</P>
</BODY>
</HTML>
```

```
             <BODY>
               | 
              <P> ----------------
               |                  |
         --------------         ALIGN
        |              |          |
    This is a         <B>         |
                       |        right
                       |
                    paragraph

```




&lt;B&gt;

태그를 가져오려면
```
var b = document.firstChild.firstChild.lastChild;
혹은
var b = document.firstChild.childNodes[0].lastChild;
혹은
var b = document.firstChild.childNodes[0].childNodes[1];
```

### 어둠의 시절(백가항쟁) : DOM Level 0

  * document.write()
  * innerHTML()

```
var b = document.all["B_TAG"];
b.innerHTML("new bold paragraph");
```

### 표준의 등장 : DOM Level 1 혹은 W3C DOM

  * document.getElementById()

```
//<B ID="B_TAG"> 라고 가정하면
//객체 얻기
var b = document.getElementById("B_TAG");
//값세팅
var node=document.createTextNode("new bold paragraph");
b.appendChild(node);
```

### 브라우저별 다른 동작의 예 : Box Model

W3C 표준과 IE가 서로 다르게 동작함.

W3C 표준은 Content만 width, height를 잡지만, IE는 padding과 border를 포함.

![http://minicube.kr/blog/attach/1/1352638279.gif](http://minicube.kr/blog/attach/1/1352638279.gif)

### jQuery & more

  * W3C DOM이 등장했지만 각 브라우저 개발업체들은 여전히 자사의 하위호환성을 위해 비표준 기술을 채택하고 있고
  * W3C DOM 스펙이 각 브라우저 별로 다르게 동작하는 경우도 있어
  * 개발자로서는 모든 브라우저에서 동일한 동작을 보장하기엔 여전히 어려움이 있었음
  * 거기다 DOM 표준 코딩은 뭔가 딱딱하고 길고 Verbose함
  * 그래서 등장한 라이브러리들이 **jQuery**, **prototype**, **mootools**

```
var b = $("#B_TAG");
b.html("new bold");

혹은

$("#B_TAG").html("new bold paragraph");

```

### JavaScript: 세상에서 가장 오해가 많은 프로그래밍 언어

```
<html>
<head>
<title>JavaScript Sandbox</title>
<script type="text/javscript" src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
<script type="text/javascript">
trace("START");
var c = new Container("abc");
trace(c);
c.service(); //this와 that이 같은 객체임
var f = c.service;
f(); //this와 that이 서로 다른 객체임

function Container(param) {
    this.member = param; //public
    var secret = 3; //private
    var that = this; //convention for inner functions to access outer context

    //private function
    function dec() {
        if(secret > 0){
            secret -= 1;
            return true;
        } else {
            return false;
        }
    }
    
    this.service = function() {
        trace(this);
        trace(that);
        return dec() ? that.member : null;
    }
}

function trace(msg) {
    try{console.log(msg);}catch(e){}
}
</script>
</head>
<body>
<div id="main"></div>
</body>
</html>
```

### undefined 유령

```
var a;
trace2(a); //undefined
trace2(typeof a); //'undefined'
trace2(a == undefined); //true
trace2(a === undefined); //true
trace2(typeof a == undefined); //false
trace2(typeof a === undefined); //false
trace2(typeof a == 'undefined'); //true
trace2(typeof a === 'undefined'); //true

var a, b;
trace2(a == b); //true
trace2( a === b); //true
trace2( typeof a == typeof b); //true
trace2( typeof a === typeof b); //true

var c = {};
trace2(c); //Object{}
trace2(c == undefined); //false
trace2(typeof c == object); //not defined error
trace2(typeof c === object); //not defined error
trace2(typeof c == 'object'); //true
trace2(typeof c === 'object'); //true

var a = "abc";
var b = "abc";
trace2(a == b);
trace2(a === b);

var a = 1, b = '1';
trace2(a == b); //true
trace2(a === b); //false!

var a = null;
trace2(typeof a); //object!!!
trace2(a); //null
trace2(a == undefined); //true!!!
trace2(a === undefined); //false
trace2(typeof a == undefined); //false and wrong usage since typeof return a string
trace2(typeof a === undefined); //false and wrong usage since typeof return a string

trace2(typeof a == 'undefined'); //false
trace2(typeof a === 'undefined'); //false
```


---

DOM스크립트, 제레미 키스 저/윤석찬 역, [[링크](http://www.aladin.co.kr/shop/wproduct.aspx?ISBN=8960770035)]

[더글라스 크록포드 할아버지 홈페이지](http://www.crockford.com/)

더글라스 크록포트 할아버지 책

[국문](http://www.aladin.co.kr/shop/wproduct.aspx?ISBN=8979145985)
[영문](http://foreign.aladin.co.kr/shop/wproduct.aspx?ISBN=0596517742)

자바스크립트 엔진 벤치마크 [[링크](http://www.crockford.com/javascript/performance.html)]


세상에서 가장 오해가 많은 프로그래밍 언어[[링크](http://home.postech.ac.kr/~skyul/javascript.html)] ~~링크깨짐~~ 링크살아남;

DOM 호환성 테스트
http://www.quirksmode.org/dom/w3c_html.html

추천 자바스크립트 웹싸이트 하나더
http://www.quirksmode.org/js/contents.html

IE Box Model Bug
http://en.wikipedia.org/wiki/Internet_Explorer_box_model_bug

자바스크립트의 클로저
http://atconsole.com/2013/04/17/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%9D%98-%ED%81%B4%EB%A1%9C%EC%A0%80-javascripts-closure/