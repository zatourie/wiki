# 기능1) 정해진 역에서 깨워준다

데이터소스 : m.bus.go.kr
데이터 : 열차 현재 위치
사용가능 범위 : 1~9호선 (분당선, 공항선 제공하지 않음)

## API?

Endpoint : http://m.bus.go.kr/mBus/subway/getStatnByRoute.do
Parameter : subwadId

예) 1호선 현황
http://m.bus.go.kr/mBus/subway/getStatnByRoute.do?subwayId=1001

참고 : existYn1, existYn2 해당 역에 열차가 있는지 여부

```
{
    "resultList":[
        {"stopTime":"30","statnCd":"9","subwayId":"1001","existYn2":"Y","sctnTime":"30","statnSn":"3","statnId":"1001000124","sctnDstnc":"0","statnNm":"청량리","existYn":"N","existYn1":"N","statnTrnsit":"1001,"},
        {"stopTime":"30","statnCd":"8","subwayId":"1001","existYn2":"Y","sctnTime":"30","statnSn":"4","statnId":"1001000125","sctnDstnc":"0","statnNm":"제기동","existYn":"N","existYn1":"Y","statnTrnsit":"1001,"},
        {"stopTime":"30","statnCd":"7","subwayId":"1001","existYn2":"N","sctnTime":"20","statnSn":"5","statnId":"1001000126","sctnDstnc":"0","statnNm":"신설동","existYn":"N","existYn1":"N","statnTrnsit":"1001,1002,"},
        {"stopTime":"30","statnCd":"0","subwayId":"1001","existYn2":"Y","sctnTime":"25","statnSn":"6","statnId":"1001000127","sctnDstnc":"0","statnNm":"동묘앞","existYn":"N","existYn1":"Y","statnTrnsit":"1001,1006,"},
        {"stopTime":"25","statnCd":"6","subwayId":"1001","existYn2":"Y","sctnTime":"25","statnSn":"7","statnId":"1001000128","sctnDstnc":"0","statnNm":"동대문","existYn":"N","existYn1":"Y","statnTrnsit":"1001,1004,"},
        {"stopTime":"20","statnCd":"5","subwayId":"1001","existYn2":"N","sctnTime":"25","statnSn":"8","statnId":"1001000129","sctnDstnc":"0","statnNm":"종로5가","existYn":"N","existYn1":"N","statnTrnsit":"1001,"},
        {"stopTime":"30","statnCd":"4","subwayId":"1001","existYn2":"Y","sctnTime":"15","statnSn":"9","statnId":"1001000130","sctnDstnc":"0","statnNm":"종로3가","existYn":"N","existYn1":"Y","statnTrnsit":"1001,1003,1005,"},
        {"stopTime":"30","statnCd":"3","subwayId":"1001","existYn2":"N","sctnTime":"30","statnSn":"10","statnId":"1001000131","sctnDstnc":"0","statnNm":"종각","existYn":"N","existYn1":"Y","statnTrnsit":"1001,"},
        {"stopTime":"30","statnCd":"2","subwayId":"1001","existYn2":"Y","sctnTime":"30","statnSn":"11","statnId":"1001000132","sctnDstnc":"0","statnNm":"시청","existYn":"N","existYn1":"Y","statnTrnsit":"1001,1002,"},
        {"stopTime":"30","statnCd":"1","subwayId":"1001","existYn2":"N","sctnTime":"0","statnSn":"12","statnId":"1001000133","sctnDstnc":"0","statnNm":"서울역","existYn":"N","existYn1":"Y","statnTrnsit":"1001,1004,"}
    ],
    "error":{"errorMessage":"성공","errorCode":"0000"}
}
```


ENDPOINT : http://m.bus.go.kr/mBus/subway/getStatnTrainInfo.do
Parameter : subwayId : 지하철호선, statnId : 역코드

예) 5호선 종로3가역 조회 URL : http://m.bus.go.kr/mBus/subway/getStatnTrainInfo.do?subwayId=1005&statnId=1005000534

JSON Type retuen data
```
{
    "resultList":[
        {
            "trainLineNm":"방화",
            "sctnId":"0",
            "statnId":"1005000534",
            "sctnDstnc":"0",
            "statnTid":"1",
            "updnLine":"상행",
            "trainNo":"5616",
            "opratKndNm":"도착",
            "trainSttus":"1",
            "subwayId":"1005",
            "statnFid":"0",
            "brnchln":"0",
            "statnSn":"25",
            "opratKnd":"0",
            "cdpntDstnc":"0",
            "arvlDt":"2013-05-10 15:33:21.0",
            "statnNm":"종로3가",
            "opratDstnc":"0",
            "trainLine":"1"
        }
    ],
    "error":{
        "errorMessage":"성공",
        "errorCode":"0000"
    }
}
```

해석 : 5616 열차가 종로3가에 5/10 15:33:21에 도착하였다.

## User Story

  1. 앱을 실행한다.
  1. 지하철 호선을 선택한다. (현재 열차 진행현황 조회)
  1. 사용자가 타고 있는 열차를 선택한다.
  1. 사용자가 내렬 역을 선택한다.
  1. 잔다.
  1. 내릴 역이 다가오면 (전역, 전전역?) 알람/진동이 울린다.