
```
아래 문장을 httpd.conf에 추가 한다.

*mod_wl_ssl 은 SSL과 연동할 때 추가되는 옵션이다. 보통 mod_wl.so로한다.

################################################

#     Weblogic Setting

################################################

LoadModule weblogic_module libexec/mod_wl.so

AddModule mod_weblogic.c

<Location /madeup>

    SetHandler weblogic-handler

    PathTrim /madeup

</Location>

<Files *.jsp>

    SetHandler weblogic-handler

</Files>

<IfModule mod_weblogic.c>

    WebLogicCluster 192.168.1.1:7005 ,192.168.1.2:7005,192.168.1.3:7005,192.168.1.4:7005

    ConnectTimeoutSecs 20

    ConnectRetrySecs 2

</IfModule>

****** IfModule 에는 다음과 같은 내용들이 들어 갈 수 있다 **************

WebLogicHost 10.200.17.27

WebLogicPort 7005

WebLogicCluster 10.1.1.100 7005,10.1.1.101 7006,10.1.1.103 7007

PathPrepend "string"

ConnectTimeoutSecs 10

ConnectRetrySecs 2

ErrorPage http://myerrorpage1.mydomain.com

StatPath true

*************************************************************************
```


---

참고

http://www.apache-kr.org/documents/apacheTechnical.php?cmd=technicalView&rg_d=20000205&rg_seq_n=1