정리예정

Done

  * Maven 설치 및 설정
  * Maven 안드로이드 플러그인 설치 및 설정
  * Maven에서 안드로이드 프로젝트 생성하기
  * 생성된 안드로이드 프로젝트 SVN에 import하기
  * Maven에서 안드로이드 빌드하기
  * Maven에서 안드로이드 서명된 apk 만들기
  * 위 과정이 들어있는 maven스크립트를 허드슨에 등록하기

> 허드슨에서 빌드버튼을 누르면 폰에 설치할 수 있는 apk를 얻을 수 있었음.

To do

  * 위의 과정에서 얻어진 apk화일을 외부로 Open된 URL에 업로드하기

여기까지 하면 개발하고 SVN에 커밋한다음 허드슨에서 빌드하면 폰으로 다운받아 테스트할 수 있는 apk를 얻을 수 있음 (폰 - PC 연결 불필요)


---


http://stand.spree.de/wiki_details_maven_archetypes

http://www.vogella.com/articles/AndroidBuildMaven/article.html

https://code.google.com/p/maven-android-plugin/wiki/GettingStarted


mvn archetype:generate -DarchetypeArtifactId=android-quickstart -DarchetypeGroupId=de.akquinet.android.archetypes -DarchetypeVersion=1.0.11 -DgroupId=zatouri -DartifactId=Retro2013