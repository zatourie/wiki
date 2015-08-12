# BIOK(구매포탈) Mobile BETA

## 개요

BIOK(구매포탈)에서 모바일로 제공하면 좋을 기능을 구현해본다.

## 기능 리스트 (Candidates)

  1. 긴급구매 상태, 구매요청자, 구매담당자 및 납품처 조회

## User Story

  * 앱/웹 실행후 텍스트박스에 주문장번호를 입력하면 현재 상태, 요청자, 구매담당자 정보를 보여주고, 납품처를 구글맵스에 보여준다.

## UI

![http://zatouri.googlecode.com/files/mobiok000.png](http://zatouri.googlecode.com/files/mobiok000.png)

![http://zatouri.googlecode.com/files/mobiok100.png](http://zatouri.googlecode.com/files/mobiok100.png)

![http://zatouri.googlecode.com/files/mobiok200.png](http://zatouri.googlecode.com/files/mobiok200.png)

![http://zatouri.googlecode.com/files/mobiok210.png](http://zatouri.googlecode.com/files/mobiok210.png)

![http://zatouri.googlecode.com/files/mobiok300.png](http://zatouri.googlecode.com/files/mobiok300.png)


추가1) 구매원 정보, PR번호, PO번호 표시 필요
추가2) 구매원 전화번호 클릭시 전화걸림

## 상태정의 필요(작성중)

  1. ERP 구매요청완료
  1. BIOK 구매원 승인중
  1. BIOK PR접수대기
  1. BIOK PR접수완료
  1. BIOK 발주대기
  1. BIOK 발주완료
  1. BIOK 출입지원 전송완료

## Data Structure

Protocol : JSON

```
/?prno=1100012345

/*Pseudo code*/
{
    data : 
    {
        PR번호 : "1100012345",
        요청자: "홍길동",
        요청자전화번호: "02-2121-0000",
        요청자이메일: "somebody@company.com",
        PO번호 : "4110012345",
        구매원: "고길동",
        구매원전화번호: "02-2121-1111",
        구매원이메일: "somebody@company.com",
        현재상태: "BIOK발주완료",
        납품처: "울산CLX",
        납품처주소: "울산광역시 남구 고사동 110"
    },
    error : 
    {
        code: "",
        message: ""
    }
}

//실데이터
{
    data : 
    {
        pr : "1100012345",
        rqstr: "홍길동",
        rqstr_phn_no: "02-2121-0000",
        rqstr_email: "somebody@company.com",
        po : "4110012345",
        buyer: "고길동",
        buyer_phn_no: "02-2121-1111",
        buyer_email: "somebody@company.com",
        status: "BIOK발주완료",
        to: "울산CLX",
        to_addr : "울산광역시 남구 고사동 110"
    },
    error : {}
}

//오류시
{
    data : {},
    error : 
    {
        code: "-1",
        message: "요청하신 번호가 존재하지 않습니다."
    }
}

```
## 이슈

  * 데이터 조회 권한 (누구나 주문장 번호를 알고 있으면 조회 가능?)
  * 프로세스상 현재상태가 중요하므로 전체 상태 flow를 보여주는 것이 좋을 것 같음.
    * 예를 들어, a > b > _**C**_ > d > e 이렇게 C상태를 보여주는 식.