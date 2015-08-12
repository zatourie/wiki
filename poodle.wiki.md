# POODLE

## Padding Oracle On Downloaded Legacy Encryption (POODLE)이란?

Common Vulnerabilities and Exposures 등재번호 CVE-2014-3566

구글에서 보고한 SSLv3 관련 취약점.

해당 취약점을 이용하여 SSLv3를 사용하는 통신을 중간에서 가로채는 man-in-the-middle attack이 가능함.

## 해결책

disable SSLv3 and use TLSv1 or newer

### 서버 대응방안

https://scotthelme.co.uk/sslv3-goes-to-the-dogs-poodle-kills-off-protocol/

### 클라이언트(웹브라우저)대응방안

https://zmap.io/sslv3/browsers.html


---


## 관련 자료

취약점
http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-3566

http://googleonlinesecurity.blogspot.com.au/2014/10/this-poodle-bites-exploiting-ssl-30.html

http://serverfault.com/questions/637053/how-can-i-tell-if-my-website-is-vulnerable-to-cve-2014-3566-poodle

서버테스트
http://poodlebleed.com/
https://www.ssllabs.com/ssltest/analyze.html

브라우저 테스트
https://dev.ssllabs.com/ssltest/viewMyClient.html


각종 서버에서 SSLv3를 disable 하는 방법
https://scotthelme.co.uk/sslv3-goes-to-the-dogs-poodle-kills-off-protocol/

각종 브라우저에서 SSLv3를 disable 하는 방법
https://zmap.io/sslv3/browsers.html