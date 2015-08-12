일시 : 2013.7.10 (수) 11:00~12:00
장소 : 민들레
발제 : 이정훈 대리


# 암호화

## 대칭키 암호화
  * 암호화의 역사
    * 시저 알고리즘
    * 치환법
    * 애니그마
  * 암호화 알고리즘
    * DES : Data Encryption Standard
    * 3DES : Triple DES
    * AES  : Advanced Encryption Standard
    * SEED
  * 대칭키의 취약점은 바로 키(안전하게 키를 전달할 방법은?)

## 대칭키 암호화 Security
  * DES : 1999년 22시간 15분 안에 해독됨 http://ko.wikipedia.org/wiki/DES_(%EC%95%94%ED%98%B8)
  * AES : 미정부 기밀암호화에 사용


## 비대칭키 암호화(공개키 암호화)
  * 대칭키의 약점을 보완한 방법
  * RSA 암호화 ( Ron Rivest, Adi Shamir, Leonard Adlema )
  * 공개키(public key), 개인키(private key)
  * 다 좋은데 속도가 좀 느리다. (대칭키에 1000배 이상)

## Hash 알고리즘
  * 단방향 암호화 (복호화가 안됨)
  * 빠르고, 결과값이 작다.
  * MD5, SHA1 ...
  * 해쉬 충돌?
  * 비밀번호는 암호화되어 저장되므로 관리자도 모릅니다.
  * Hash값 복호화 : 레인보우 테이블

## 전자서명
  * 개인키로 암호화(메시지의 Hash값)
  * Enc(MSG) + Apriv(Hash(MSG))
  * 공인인증서는 개인키