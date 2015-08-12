![http://upload.wikimedia.org/wikipedia/commons/5/5f/Cloud9IDE.png](http://upload.wikimedia.org/wikipedia/commons/5/5f/Cloud9IDE.png)

발제 : 심민규
일시/장소: 2014.7.30 (수) / 장미

# 내용

참고에 있는 글을 참고하여 Cloud IDE인 Cloud9과 Git를 이용하여 Google App Engine에 App을 배포하는 프로젝트를 만들어봅니다.

# Git란

DVCS (분산형상관리시스템, Distributed version control system). Local repo로 commit하고, remote repo로 push하는 방식. 브랜칭과 머징이 굉장히 빠르다.

# Google App Engine

구글이 서비스하고 있는 코드실행 서비스. 자바, 파이선 등의 언어로 코딩한 후 GAE에 올리면 웹으로 서비스할 수 있다.

# Cloud9

일명 Cloud IDE 중 하나. 웹싸이트로 구현된 개발환경으로 웹브라우저에서 개발 가능.

# 개발라이프사이클

  1. Cloud9에서 코딩 및 Github로 push
  1. Github로 push된 소스코드를 GAE로 배포
  1. GAE에서 서비스


# 순서

  1. Github에 Repo 만들기
  1. Cloud9에 New project 만들기
  1. Google App Engine에 new project 만들기
  1. Cloud9에 Github 연결
  1. Google App Engine에 Github 연결
  1. Cloud9에서 개발하고 push 하면 deploy 됨.


## Github Project
> https://github.com/zatourie/appengine-guestbook-python

## Cloud9 Project
> https://ide.c9.io/zatourie/appengine-guestbook-python

## Google App Engine Project
> https://console.developers.google.com/project/apps~fluid-catfish-656

## GAE Service URL
> http://fluid-catfish-656.appspot.com/



---


참고

Cloud9 + Git + Google App Engine

https://c9.io/site/blog/2013/07/deploy-to-google-app-engine-with-cloud9-and-git/#sthash.gaNxi98n.dpbs

90% of Python in 90 Minutes

http://www.slideshare.net/MattHarrison4/learn-90