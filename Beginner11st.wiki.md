# Node.js를 이용한 Midas 접근제한 해제 + mRemoteNG

![http://www.codersgrid.com/wp-content/uploads/2013/05/nodejs-image-processing.png](http://www.codersgrid.com/wp-content/uploads/2013/05/nodejs-image-processing.png)

## 1. 내용

Node.js에서 제공하는 node.exe와 request 모듈을 이용하여 midas의 접근제한 해제 요청을 윈도우 Command line에서 할 수 있음

## 2. 방법

1) http://www.nodejs.org/ 에서 node.js 인스톨


!!!인스톨시 주의 : Default 설치위치가 C:\Program files\nodejs 인데 c:\nodejs 로 변경할 것을 권장함. 이후에 Program files 사이에 있는 스페이스로 인해 문제가 발생할 수 있음.

2) midas.js c:\nodejs 혹은 nodejs 설치 폴더로 복사

3) midas.js 를 텍스트 에디터로 열어서 username과 password 수정

```
var username = "00000";
var password = "00000";
```

4) 설치완료


## 3. 사용법

해제시

```
node release midas.js {접속제한을 해제할 서버의 호스트네임(대소문자구분함)}
혹은
node midas.js {접속제한을 해제할 서버의 호스트네임(대소문자구분함)}
```

ex) node midas.js server1

락 걸시
```
node lock midas.js {접속제한을 해제할 서버의 호스트네임(대소문자구분함)}
```

ex) node lock midas.js server1

# mRemoteNG과 연계하기

![https://dc080p1pxrpu1.cloudfront.net/screenshots/6211/optimal.png](https://dc080p1pxrpu1.cloudfront.net/screenshots/6211/optimal.png)

## 1. mRemoteNG란?

윈도우즈 원격터미널 접속프로그램 (mstsc) 접속정보를 저장해놓을 수 있어 많은 서버를 관리하는데 편리하다.

## 2. 뭘 하려고?

mRemoteNG에서 해당 서버에 연결하면 자동으로 Midas에 접속제한을 해제한 다음 연결되도록 함.

## 3. 방법

1) http://www.mremoteng.org/download 에서 mRemoteNG를 설치한다. (인스톨버전을 설치해도 되지만 미인증소프트웨어이므로, 포터블 버전을 사용해도 된다.)

2) 상단 메뉴 > Tools > External Tools 선택


3) New External Tool 선택

![http://widget.digestzone.com/uploadfiles/widgetdigestzonecom-1349904419/mremoteng-establish-rdp-ssh-telnet-connections-in-multiple-tabs_2.png](http://widget.digestzone.com/uploadfiles/widgetdigestzonecom-1349904419/mremoteng-establish-rdp-ssh-telnet-connections-in-multiple-tabs_2.png)

4) External Tool 작성


5) Connection의 External Tool Before/after에 해당 Task 바인딩


6) Enjoy!