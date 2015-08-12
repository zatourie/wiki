# 안드로이드 빌드, 서명, 최적화

## 개요

안드로이드 앱은 배포되기 전에 빌드, 서명, 최적화의 세단계가 필요하다.

많이 쓰이는 방법으로 Eclipse ADT(Android Developer Tools)와 ANT를 이용하는 방법이 있으며, 용도에 따라 Debug, Release로 나눌 수도 있다.

개인키가 있는 상태면, 위 세단계를 한번에 처리할 수도 있다.

## 빌드(BUILD)

1. Eclipse  이용시

빌드는 자동, 에뮬레이터나 폰에서 실행시켜보려면 Run As Android Application 선택

_스크린샷 및 사용법 작성필요_

2. ANT 이용시, Android project 위치로 가서

```
$ ant debug 
```
혹은
```
$ ant release
```

## 서명(SIGN)

### Debug

개발시 사용할 수 있는 용도. Android SDK에서 제공하는 key로 서명한다. 배포는 불가.

### Release

개발자 개인키(private key)로 서명한다. self-signed 관계없음. 배포 가능.

### 먼저, 개인키(private key) 만드는 방법

JDK에서 제공하는 keytool  이용한다.

```
$ keytool -genkey -v -keystore my-release-key.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 10000
```

위 명령을 실행하면 개인키 발급의 위해 필요한 패스워드와 이름, 조직, 국가 정보를 묻는데 모두 입력하고 나면 10000일동안 유효한 keystore가 my-release-key.keystore라는 이름으로 생성한다. keystore와 key는 입력한 패스워드로 보호된다.


### 서명하는 방법

JDK에 들어있는 jarsigner 이용

```
$ jarsigner -verbose -sigalg MD5withRSA -digestalg SHA1 - keystore my-release_key.keystore my_app.apk alias_name
```

### 서명된 apk 유효성검사

```
$ jarsigner -verify -verbose my_app.apk
```

## 최적화(OPTIMIZING)

JDK에서 제공하는 zipalign 이용

```
$ zipalign -v 4 your_projefct_name-unaligned.apk your_project_name.apk
```

## 좀 더 쉬운 방법

Eclipse 에서 Android project 위에 마우스 오른쪽 클릭하고 signed 혹은 unsigned 선택하거나 File > Export, Android folder>Android Application 선택

빌드,서명,최적화까지 가능한 Wizard 화면뜸.

_보완필요_

ANT 이용시는

ant.properties에 아래 서명관련 property를 지정해주고

```
key.store=path/to/my.keystore
key.alias=mykeystore
```

```
$ ant release
```
하면 서명된 apk화일 얻을 수 있음. 이 경우 최적화는 따로 실행해야함.


---

# Reference

  * http://developer.android.com/tools/publishing/app-signing.html
  * http://developer.android.com/tools/building/building-cmdline.html