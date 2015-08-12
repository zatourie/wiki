# 레드마인 설치 및 설정방법

# 레드마인(Redmine)이란?

![http://redmine.rubyforge.org/screenshots/rdm-gantt.png](http://redmine.rubyforge.org/screenshots/rdm-gantt.png)

  * 레드마인은 웹으로 되어있는 프로젝트 관리 어플리케이션이다. 여러 프로젝트를 관리할 수 있고, 역할 베이스의 권한 관리 기능, 간트차트, 일정, 뉴스, 문서, 파일, 위키, 포럼 등을 제공한다. 소스 형상관리와 연결하여 사용할 수 있다.
  * 레드마인은 루비로 만들어져있고, GPL v2로 라이센스 되어있다.
  * website : http://www.redmine.org
  * 이 글에서는 레드마인을 쉽게 설치하도록 패키지화 해놓은 Bitnami Redmine을 사용한다.

# 필요한 것

  * Bitnami Redmine : Redmine과 Redmine을 설치하는데 필요한 DB, Web Server 등의 제품들을 패키지화하여 한번에 설치할 수 있도록 해놓은 설치본. 기본으로 MySQL, Apache Web Server가 설치된다.
  * 다운로드 페이지 : https://bitnami.com/stack/redmine

# 설치순서

  1. Bitnami Redmine Stack 설치 (Redmine, MySQL, Web Server)
  1. 메일서버 연동 (optional)
  1. 프로젝트 생성 및 SVN 연결 (optional)
  1. Redmine 백업 스크립트 걸기 (optional)

# 설치 (동영상)

그냥 설치하기

<a href='http://www.youtube.com/watch?feature=player_embedded&v=yyfQ9gl_iXQ' target='_blank'><img src='http://img.youtube.com/vi/yyfQ9gl_iXQ/0.jpg' width='425' height=344 /></a>

VMWARE를 이용하여 설치하기

<a href='http://www.youtube.com/watch?feature=player_embedded&v=qB-2uj-cJ2I' target='_blank'><img src='http://img.youtube.com/vi/qB-2uj-cJ2I/0.jpg' width='425' height=344 /></a>

# 설정

## SVN 연결

![http://wiki.bitnami.com/@api/deki/files/254/=Redmine-svn.png](http://wiki.bitnami.com/@api/deki/files/254/=Redmine-svn.png)

프로젝트 세팅화면에서 Repository에 SVN URL과 접속정보를 기록해주면 끝.

## BUT, 그러나 인생은 그렇게 호락호락하지 않음 HTTPS SVN 연결

SSL을 사용하는 SVN 서버로는 "the entry or revision was not found in the repository" 오류메시지가 뜨며, 위의 방법으로는 연결되지 않는다. 연결하려면 인증정보 설정이 필요하다.

이때는, 설치디렉토리\redmine\apps\redmine\htdocs\lib\redmine\scm\adapters에 위치한subversion\_adapter.rb 화일의 credentials\_string 부분을 다음과 같이 수정한다. ( --config-dir은 인증정보가 들어갈 위치)

```
def credentials_string
  str = ''
  str << " --username #{shell_quote(@login)}" unless @login.blank?
  str << " --password #{shell_quote(@password)}" unless @login.blank? || @password.blank?
  str << " --trust-server-cert --no-auth-cache --non-interactive  --config-dir C:\\BitNamiRedmineStack\\svnfingerprint"
  str
end
```


subversion https 접근시 인증정보(fingerprint)를 로컬폴더에 저장하는 방법은

```
svn --config-dir {config정보위치} info {소스위치}
```

예시
```
svn --config-dir C:\BitNamiRedmineStack\svnfingerprint info https://123.123.123.123/svn/souerce/trunk
```

여기까지 하고 다시 레드마인에서 저장소를 클릭하면 연결되어야한다.

# SMTP Mail Sever 연결

설치위치\redmine\apps\redmine\htdocs\config에 위치한 configuration.yml 파일을 다음과 같이 수정한다.

```
  email_delivery:
    delivery_method: :async_smtp
    async_smtp_settings:
      address: xxx.xxx.xxx.xxx
      port: smtp port 기본 25
      domain: 'skbiok.com'
      authentication: :login
      user_name: user@domain.com
      password: 비밀번호
```


---


# Reference

생활코딩

  * http://opentutorials.org/course/438/2453

HTTPS SVN 서버연결방법

  * http://www.redmine.org/issues/787