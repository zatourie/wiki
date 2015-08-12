# 일시/장소

2014.7.9 (수) 11:00~13:00 / 종로제이알스터디

# 발제자

심민규

# 주제

간단한 예제로 보는 Native DOM, jQuery, AngularJS의 코딩 스타일 차이와 장단점.

# 피드백

  * https://ko.surveymonkey.com/s/TLLM2PC

# 내용

# Native DOM

```
/*jsonp 예제*/
jsonp("http://jeehamenu.appspot.com/hq", function(data){
    var element;
    element = document.getElementById("date");
    element.innerHTML = data.date;
    
    element = document.getElementById("breakfast");
    element.innerHTML = data.breakfast;

    element = document.getElementById("lunch");
    element.innerHTML = data.lunch;
    
    element = document.getElementById("dinner");
    element.innerHTML = data.dinner;
});
   
function jsonp(url, callback) {
    var callbackName = 'jsonp_callback_' + Math.round(100000 * Math.random());
    window[callbackName] = function(data) {
        delete window[callbackName];
        document.body.removeChild(script);
        callback(data);
    };

    var script = document.createElement('script');
    script.src = url + (url.indexOf('?') >= 0 ? '&' : '?') + 'callback=' + callbackName;
    document.body.appendChild(script);
}

```
  * http://jsfiddle.net/heartonbit/5V3FE/



# jQuery

```
/*jQuery 예제*/
$(document).ready(function(){
   
    var xhr = $.ajax({
        type: 'GET',
        url: "http://jeehamenu.appspot.com/hq",
        dataType: 'jsonp',
        success: function(json) {
            $("#date").text(json.date);
            $("#breakfast").text(json.breakfast);
            $("#lunch").text(json.lunch);
            $("#dinner").text(json.dinner);
        }
    });

});
```
  * http://jsfiddle.net/heartonbit/7BE4b/

# AngularJS

```
/*AngularJS 예제*/
var app = angular.module("cantine",[]);

function menuCtrl($scope, $http){
    //var url = "http://localhost:11080/?callback=JSON_CALLBACK";
    var url = "http://jeehamenu.appspot.com/?callback=JSON_CALLBACK";
    $http.jsonp(url)
         .success(function(data){
             $scope.menus = data;        
         })
         .error(function(error){
             trace(error);
         });
}
```
  * http://jsfiddle.net/heartonbit/pg9Rq/


---


![http://heartonbit.byus.net/img/CAM00137s.jpg](http://heartonbit.byus.net/img/CAM00137s.jpg)

![http://heartonbit.byus.net/img/CAM00138s.jpg](http://heartonbit.byus.net/img/CAM00138s.jpg)