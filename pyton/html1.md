# html 1

```
html:비구조화된 문서, 태그 이름이 정해져 있음
xml:구조화된 문서, 태그 이름을 사용자가 지정할 수 있음

teg는 대문자 소문자 구분이 없음 
```

## 웹통신과정*

```
1.사용자가 주소 입력(www.naver.com)
2.www.naver.com->13.15.230.221(DNS) 주소로 변환
3.사용자 브라우저는 13.15.230.221에 웹페이지를 요청
4.웹서버는 요청을 받고 실행함 -> HTML,CSS,JS 문서 전송
5.사용자 웹브라우저는 전달 받은 문서를 해석 -> 화면에 출력
6.브라우저에는 네이버 홈페이지가 출력
```

## 한글 문자 출력

```
<meta charset="UTF-8">
```

## strong:굵은 글씨

```
굵은 글씨
```

## u:밑줄

```
밑줄
```

## h1~6

```
<h1>this is heading 1</h1>
<h2>this is heading 1</h2>
<h3>this is heading 1</h3>
<h4>this is heading 1</h4>
<h5>this is heading 1</h5>
<h6>this is heading 1</h6>

1에서 6까지 순차적으로 글씨가 굵은 글씨로 점점 작아짐 6이 끝임

```

***strong 과 h의 차이***

h태그는 검색엔진에 중요한 제목 태그라고 인식

strong은 그냥 굵은 글씨

## html에서 주석

```
ctrl+shift+/ : 드래그한 전체를 한번에 주석
ctrl+/:한줄만 주석
<!--내용-->
```

## 단독태그

```
<br> 줄바꾸기
<img>
<meta>
<hr>
<input>
<link>
```

## 줄바꾸기

```
<br> 줄바꾸기
```

## pre:그대로 출력

```
있는 그대로 출력해줌
```

## p:문단

```
문단을 만들어 줄 때
```

## b: 굵은 글씨

```
<!--<b> 보다는 <strong> 태그 사용권장</strong>>-->

<!--css에서는 font-weight 값을 bold로 설정-->

```

## i :기울임 

```
기울임 글씨
```

## a :하이퍼링크

```
a태그:하이퍼링크를 설정하는 태그
속성:
-href:이동 할 링크
-target:링크를 여는 방법
새탭,현재 화면,iframe:부모페이지...


<a href="http://www.naver.com">네이버</a> 지금화면으로 띄움

<a href="http://www.daum.net" target="_blank">다음</a>

target="_blank" 새창을 띄워서 출력



```

## img:이미지

```
<img src="google.png" width="300" height="200">

<!--구글 이미지를 클릭했을때 구글 웹페이지가 새로운탭에 출력되도록 코드를 완성-->

<a href="http://www.google.com" target="_blank"><img src="google.png"></a>
```

## 속성 부여

```
	<font color="red" face="Dotum">Hello</font>
	<font color="yellow">World</font>
	빨간글씨에 돋음체의 hello
	노란글씨에 word
	
<div style="width:500px; height:300px;border: 1px solid red">gi</div>
<div style="height:40px; border: 1px solid green">mybox</div>

높이 300 너비500 1px두께에 빨간 실선(solid) 박스를 만들어 gi를 삽입

```

