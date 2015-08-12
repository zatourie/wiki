# MS SQL Server Profiler



# Profiler란

  * DB서버의 이벤트를 모니터링 할 수 있는 툴.
  * T-SQL이나 SP 실행을 어떻게 되는지 확인할 수 있어 DB 디버깅에 용이

# 설치

  * SQL Server의 advanced client tools 항목에 포함되어 있음.

# 권한

  * 프로파일러를 실행하려면 해당 로그인 유저에게 ALTER TRACE 권한이 있어야함

# 사용법

## Advanced Index Tuning (슬라이드)

http://www.slideshare.net/SQLServerPedia/advanced-index-tuning-for-sql-server

## Performance Tuning and Query Analysis(동영상)

<a href='http://www.youtube.com/watch?feature=player_embedded&v=P97_oFfD218' target='_blank'><img src='http://img.youtube.com/vi/P97_oFfD218/0.jpg' width='425' height=344 /></a>



# 대체툴 ExpressProfiler

  * 설치없이 사용할 수 있는 대체툴
  * Filter를 걸 수 없어 DB서버로 날아오는 모든 이벤트가 기록되는 단점이 있음
  * URL : http://expressprofiler.codeplex.com/






---

# Reference

MS자료

http://technet.microsoft.com/en-us/library/ms181091.aspx

Advanced Index Tuning for SQL Server by quest software

http://www.slideshare.net/SQLServerPedia/advanced-index-tuning-for-sql-server

Permissions Required to Run SQL Server Profiler

http://technet.microsoft.com/en-us/library/ms187611.aspx