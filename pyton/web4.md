# web4

##  web스크래핑 

### 1)urllib :웹사이트에서 가져오기

```
import urllib.parse as parse
import urllib.request as request
addr="http://www.weather.go.kr/weather/forecast/mid-term-rss3.jsp"
values={'stdId':'109'}

params=parse.urlencode(values)# stdId=190
url=addr+"?"+params
print(url)
#http://www.weather.go.kr/weather/forecast/mid-term-rss3.jsp?stdId=109

data=request.urlopen(url).read()
data=data.decode('utf-8')#한글꺠짐 방지
print(data)
#해당페이지 스크랩핑
```

### 2)Beautifulsoup:추출기

#### from bs4 import BeautifulSoup

```
from bs4 import BeautifulSoup

html="""
<html><body>
<h1>스크래핑</h1>
<p>웹페이지분석</p>
<p>원하는 부분 추출</p>
</body></html>
"""

# BeautifulSoup(html, "html.parser") #추출이 가능한 형태로 변환

soup=BeautifulSoup(html, "html.parser") #soup가 추출 가능한 문서\
무조건 해줘야하는 단계~~~
======================================================
print(soup.html.body.h1)#<h1>스크래핑</h1>#전체 html에서 html하위에 body하위에 h1을 스크래핑 하겠다는 의미

 print(soup.html.body.p) # 첫 p태그만 출력됨

```

### string:태그 빼고 내용만 줘

```
html2="""
<html><body>
<h1 id='title'>스크래핑</h1>
<p id='body'>웹페이지분석</p>
<p>원하는 부분 추출</p>
</body></html>
"""
soup=BeautifulSoup(html2,"html.parser")

print(soup.html.body.h1.string)
##웹페이지분석

```

### find()==select_one()

```
하나만 찾아줌

html2="""
<html><body>
<h1 id='title'>스크래핑</h1>
<p id='body'>웹페이지분석</p>
<p>원하는 부분 추출</p>
</body></html>
"""
soup=BeautifulSoup(html2,"html.parser")

print(soup.find(id="title").string)
#스크래핑

```

### find_all():같은거 다찾아줘==select()

리스트 형태이기 때문에 [num]이용해  인덱싱 가능

ex)print(soup.select("li")[2])
	 print(soup.find_all("li")[2])

```
html3="""
<html><body>
<ul>
<li><a href="http://www.naver.com">naver</a></li>
<li><a href="http://www.daum.net">daum</a></li>
</ul>
</body></html>
"""
# <태그명 속성명=속성값 속성명=속성값...>

soup=BeautifulSoup(html3,"html.parser")
print(soup) #문자열을 ->html파서로 분석할 수 있는 객체
print(html3) # 단순히 문자열을 저장하고 있는 변수 출력


print(soup.find_all("a")) #리스트로 출력
#[<a href="http://www.naver.com">naver</a>, <a href="http://www.daum.net">daum</a>]

print(html3.find_all("a")) #에러 parser변환이 안되어 있기때문에
```

### .attrs:결과를dict형태로 출력

```
html4="""
<p><a href="aaa.html"name="kkk">aaa page</a></p>
"""

soup=BeautifulSoup(html4,"html.parser")

print(soup.p.a.string)#a 태그가 여러곳에 산재 되어 있을 경우 앞태그도 써줌  p태그 안에 a태그를 출력해줘
print(soup.a.string)
#aaa page

mydict=soup.a.attrs # 딕셔너리 형식으로 나옴
print(mydict)
#{'href': 'aaa.html', 'name': 'kkk'}

print('href' in mydict)
#Ture
```

## 파일객체에서 Beautifulsoup으로 만들기

```
from bs4 import BeautifulSoup

fp=open("lang.html", mode="r",encoding="utf-8")
#파일 객체를 Beautifulsoup으로 만드는법
soup=BeautifulSoup(fp, "html.parser")
print(soup)
print("="*50)

print(soup.select_one("ul >li"))
print("-"*50)
print(soup.select("ul > li"))
print(soup.select_one("ul > li#sp")) #<li id="sp">spark</li>
print(soup.select_one("li#sp"))#<li id="sp">spark</li>
print(soup.select_one("#sp"))#<li id="sp">spark</li>
print("="*50)
#여러개의 ul이 있을때 해당되는 것에 name을 통해 식별 후 검색
print(soup.select_one("ul#language > li#py"))
print(soup.select_one("#language #py"))
print(soup.select_one("#language > #py"))
print(soup.select_one("li[id='py']"))
print("-"*50)
print(soup.select_one("li:nth-of-type(2)"))

print(soup.select("li")[2])
print(soup.find_all("li")[2])
```

## Selenium

```
# Selenium: 웹 브라우저를 제어하는 프로그램 #pip install selenium

from selenium import webdriver
from bs4 import BeautifulSoup

#크롬드라이버를 다운 받아 설치

#chromdriver는 크롬 웹브라우저를 제어하는 프로그램

driver=webdriver.Chrome("c:/scrap/chromedriver.exe")
url="https://www.naver.com"
driver.get(url)
html=driver.page_source #url에 해당하는 페이지를 전체스크랩핑
print(html)

#멜론 실시간 인기 차트 곡 수집
url='https://www.melon.com/chart/index.htm'

driver.get(url)
html=driver.page_source
# print(html)
soup=BeautifulSoup(html,"html.parser")
# print(soup)
songs=soup.select("tr")[1:]

# print(len(songs))
song=songs[2]


title=song.select('a')
print(title)
print("="*50)
for song in songs:
    print("곡명:",song.select("div.ellipsis.rank01 > span > a")[0].string)
    print("가수명:",song.select("div.ellipsis.rank02 > span > a")[0].string)
    print("=" * 50)


```