
```

svnadmin dump C:\Repo > D:\backup\new\svn_%date:~0,4%%date:~5,2%%date:~8,2%.dump

ROBOCOPY D:\backup\new D:\backup\Old *.* /move /minage: 7

DEL D:\backup\Old\*.*

```

New 폴더로 백업덤프를 남기고 , 7일 지난건 Old폴더로 옮긴다음 Old폴더에 있는 모든 파일을 삭제하는 스크립트입니다 .