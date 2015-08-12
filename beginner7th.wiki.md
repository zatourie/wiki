일시/장소 : 2013.6.26(수), 튜울립

# 웹서비스(Web Service)

## 웹서비스란?

웹 서비스(web service)는 네트워크 상에서 서로 다른 종류의 컴퓨터들 간에 상호작용을 하기 위한 소프트웨어 시스템이다. 웹 서비스는 서비스 지향적 분산 컴퓨팅 기술의 일종이다. 웹 서비스 프로토콜 스택은 SOAP, WSDL, UDDI 등으로 이루어진다. 모든 메시징에 XML이 사용되어 상호운용성이 높다.

![http://upload.wikimedia.org/wikipedia/commons/4/4a/Webservices.png](http://upload.wikimedia.org/wikipedia/commons/4/4a/Webservices.png)

from wikipedia, http://ko.wikipedia.org/wiki/%EC%9B%B9_%EC%84%9C%EB%B9%84%EC%8A%A4

## 어디에 쓰는가?

분산환경에서 시스템간 통신을 위한 기술 : CORBA(Java), DCOM(Microsoft), RFC(SAP 등), WEB SERVICE

## 다른 기술들과 Web Service의 차이점 : **XML**



## XML을 사용했을 경우 장점

  * 디버깅 용이
  * Self-descriptive한 데이터
  * 이기종간 통신 용이(다 String이니까!)

## XML의 단점

  * performance
  * verbosity(데이터량 증가, 같은 데이터를 보내는 JSON과 크기 비교)

## Web Service의 종류

> SOAP, REST

## REST에서 주로 사용하는 datatype : JSON


### JSON의 장점

  * 가볍다 (XML보다 데이터량 적음)
  * Javascript에서 받아서 바로 객체로 활용가능


### RESTful API 예시

  * Facebook Graph API,  http://youtu.be/WteK95AppF4