# Powershell

## Powershell 설치되었는지 확인방법

command line에서

```
C:\>powershell [엔터]
```

결과
```
Windows PowerShell
Copyright (C) 2009 Microsoft Corporation. All rights reserved.
```

## Powershell 버전 확인방법

powershell 실행후,

```
PS C:\위치>$host [엔터]
```

결과

```
Name             : ConsoleHost
Version          : 2.0
InstanceId       : 868af158-5b47-4fa5-afd9-d7838e2903d9
UI               : System.Management.Automation.Internal.Host.InternalHostUserInterface
CurrentCulture   : ko-KR
CurrentUICulture : ko-KR
PrivateData      : Microsoft.PowerShell.ConsoleHost+ConsoleColorProxy
IsRunspacePushed : False
Runspace         : System.Management.Automation.Runspaces.LocalRunspace
```

## 서비스 리스트 보기

명령어
```
get-service
```

## 프로세스 리스트 보기

명령어
```
get-process
```

## 프로세스 중지하기

명령어
```
stop-process -id 1234
```

혹은

```
stop-process -name processname
```

## Powershell 스크립트 실행하기

실행정책 변경필요 (기본값: Restricted, 스크립트실행을 허용하지 않음)

```
PS C:\Users\Administrator\Desktop> Get-ExecutionPolicy
Restricted
PS C:\Users\Administrator\Desktop> Set-ExecutionPolicy RemoteSigned
```

## 큰 텍스트화일 비교

```
PS C:\> compare-object (get-content one.txt) (get-content two.txt)
```


---

references

http://technet.microsoft.com/en-us/scriptcenter/powershell.aspx

http://powershell.com/cs/blogs/ebookv2/archive/2012/03/08/chapter-1-the-powershell-console.aspx

Windows Powershell Cookbook: for Windows, Exchange 2007, and MOM V3, Lee Holmes

http://technet.microsoft.com/en-us/library/ee176949.aspx