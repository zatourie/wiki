Original Url : http://massmail.sk.com/menu/print.aspx?rcode=no1

# Server Side API

Google App Engine, Python 사용예정

이쁜 URL 하나 지어주셈.

일단은 http://jeehamenu.appspot.com (일단 본사는 완성)

"데이터가 없습니다" 상황 처리 필요


## Response json 예시

```
[ { date : "2014년 6월 23일 월요일", breakfast : "아침", lunch : "점심", dinner: "저녁" }, { date : "2014년 6월 24일 화요일", breakfast : "", lunch : "", dinner: "" }, { date : "2014년 6월 25일 수요일", breakfast : "", lunch : "", dinner: "" }, { date : "2014년 6월 26일 목요일", breakfast : "", lunch : "", dinner: "" }, { date : "2014년 6월 26일 금요일", breakfast : "", lunch : "", dinner: "" } ]
```

## Code
```
#!/usr/bin/python
# coding=utf-8
# Python 2.7 - http://python.org/download/
# BeautifulSoup - http://www.crummy.com/software/BeautifulSoup/#Download

from bs4 import BeautifulSoup, UnicodeDammit
import urllib2,re, datetime, json

#Generate Regular Expression for Today
today = datetime.date.today()
regex = re.compile(str(today.year) + ".*?" + str(today.month) + ".*?" + str(today.day));

#Get HTML
baseURL = 'http://massmail.sk.com/menu/print.aspx?rcode=no1'
html = urllib2.urlopen(baseURL).read()

#Parse HTML using BeautifulSoup
html = BeautifulSoup(html)

#Find Today's row
cell = html.find(text=regex)

today_row = cell.parent.parent
cells = today_row.find_all("td")

b_menu_str = ""
l_menu_str = ""
d_menu_str = ""

#Get Breakfast
breakfast =  cells[0]
b_menus = breakfast.find_all("li")
for item in b_menus:
    b_menu_str += item.get_text() + "</br>"

#Get Lunch
lunch =  cells[1]
l_menus = lunch.find_all("li")
for item in l_menus:
    l_menu_str += item.get_text() + "</br>"

#Get Dinner
dinner = cells[2]
d_menus = dinner.find_all("li")
for item in d_menus:
    d_menu_str += item.get_text() + "</br>"

#Generate JSON
json = """{
    date : %s,
	breakfast : %s,
	lunch: %s,
	dinner: %s
}""" % (today, b_menu_str, l_menu_str, d_menu_str,)

print json

```

## python html parser Beautifulsoup

http://www.crummy.com/software/BeautifulSoup/

구글앱엔진에서 3rd party 라이브러리 사용법

http://stackoverflow.com/questions/14850853/how-to-include-third-party-python-libraries-in-google-app-engine


# Client Side

AngularJS와 Twitter Bootstrap을 이용한 웹페이지 (모바일로 접근 가능)

## JSFiddle 코딩

http://jsfiddle.net/heartonbit/pg9Rq/