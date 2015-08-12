# SVN Repository에서 통계 뽑기

# 내용

statsvn을 이용하여 SVN Repo에서 통계를 뽑아 html 화일로 추출할 수 있다.

# 방법

1. statsvn 다운로드

2. 소스코드 체크아웃

> svn co svn://server/repo/trunk/modulename

3. 로그화일 생성

> svn log -v --xml > logfile.log

기간을 지정해줄 경우엔

> svn log -v --xml -r {2007-02-19}:{2007-02-12} > logfile.log

4. statsvn 실행

> java -jar /path/to/statsvn.jar /path/to/module/logfile.log /path/to/module -charset utf-8


---


# 참조

http://wiki.statsvn.org/