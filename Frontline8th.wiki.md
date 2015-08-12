# PhoneGap

## PhoneGap이란?

**PhoneGap is an application container technology that allows you to create natively-installed applications for mobile devices using HTML, CSS, and JavaScript.   The core engine for PhoneGap is also 100% open source, under the Apache Cordova project.**


PhoneGap App은 브라우저엔진을 이용한다.

![http://phonegap.com/uploads/2012/05/web-view_updated.png](http://phonegap.com/uploads/2012/05/web-view_updated.png)

Plugin을 통해 Device의 기능들을 이용할 수 있다.

![http://phonegap.com/uploads/2012/05/API_updated.png](http://phonegap.com/uploads/2012/05/API_updated.png)

HTML5, CSS, JavaScript를 사용한다.

![http://phonegap.com/uploads/2012/05/export_updated.png](http://phonegap.com/uploads/2012/05/export_updated.png)

## PhoneGap vs Apache Cordova

Apache Cordova는 아파치의 오픈소스 프로젝트

PhoneGap은 Apache Cordova을 기반으로 Adobe에서 서비스하고 있는 것.

PhoneGap의 documentation에 가면 cordova의 document를 그대로 가져다 쓰고 있어 헷갈린다. Remote Build를 쓸 일이 없다면, 그냥 Cordova를 쓰도록 하자.

## Command Line Interface (CLI)

command line에서 프로젝트 생성, 플랫폼 추가, 빌드, 배포 등을 한다.

## 설치해보자

### 필요한 것
JDK
Android SDK
Ant
node.js

### cordova 설치

```
npm install cordova
```

### 프로젝트 생성

```
cordova create hello com.example.hello HelloWorld
```

### 플랫폼 추가


```
cd hello
cordova platform add android
```

### Android용으로 빌드

```
cordova build android
```

### 안드로이드 폰으로 배포

AVD를 띄워놓거나 폰 연결

```
adb devices
cordova run android
```

### Plugin?

### 참고자료

PhoneGap 홈페이지: http://phonegap.com/

http://www.tricedesigns.com/2013/01/18/my-workflow-for-developing-phonegap-applications/

http://phonegap.com/2012/05/02/phonegap-explained-visually/