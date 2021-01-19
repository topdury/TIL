# Html2

## table

```
<!--테이블태그:표,tr(행(세로)태그와 td(렬(가로)태그 함께 사용-->
<!--화면 구성 할때는 테이블태그 보다 div태그(css) 를 더 많이 사용-->


<!--thead태그:표의 제목영역-->
<!--th태그:제목-->
<table>
	<thead>
		<tr>
			<th>학교</th>
			<th>창립년도</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>서울대학교</td>
			<td>1946</td>
		</tr>
		<tr>
			<td>고려대학교</td>
			<td>1905</td>
		</tr>
		<tr>
			<td>연세대학교</td>
			<td>1885</td>
		</tr>
	</tbody>
</table>

  학교(굵)	 창립년도(굵)
서울대학교	1946
고려대학교	1905
연세대학교	1885


###css
<style>
	table{border:1px soild #ff0000;
		}
</style>
<!--
색생값 범위: 0~f까지(16진수)
000000:검정, FFFFFF:흰색
#ff0000
-->
```

### table border:외각선 두꼐 

```

###css가 아님
<html>
<head>
<meta charset="EUC-KR">
<title>초간단 테이블</title>
</head>
<body>
    <table border="2"bordercolor="blue"width="300"height="300"> #border수가 커질수록 외각선이 두꺼워짐
    <table border="2"bordercolor="blue"width="100%"height="100%"> 
    #표에 높이와 너비는 퍼센트로 지정할수 있다
    
	<th>테이블</th>
	<th>만들기</th>
	<tr><!-- 첫번째 줄 시작 -->
	    <td>첫번째 칸</td>
	    <td>두번째 칸</td>
	</tr><!-- 첫번째 줄 끝 -->
	<tr><!-- 두번째 줄 시작 -->
	    <td>첫번째 칸</td>
	    <td>두번째 칸</td>
	</tr><!-- 두번째 줄 끝 -->
    </table>
</body>
</html>
```

### table align :정렬

```
<html>
<head>
<meta charset="EUC-KR">
<title>초간단 테이블</title>
</head>
<body>
<!--    <table border="2" bordercolor="blue" width="300" height="300">-->
    <table border="2" bordercolor="blue" width="100%" height="300">

	<th>테이블</th>
	<th>만들기</th>
	<tr align="center"><!-- 첫번째 줄 시작 -->
	### 가운데 정렬 첫줄만
	    <td>첫번째 칸</td>
	    <td>두번째 칸</td>
	</tr><!-- 첫번째 줄 끝 -->
	<tr><!-- 두번째 줄 시작 -->
	    <td>첫번째 칸</td>
	    <td>두번째 칸</td>
	</tr><!-- 두번째 줄 끝 -->
    </table>
</body>
</html>
```

### table 병합

```
  <td colspan="2">합쳐진칸</td>
  <td rowspan="2">합쳐진칸</td>

<html>
<head>
<meta charset="EUC-KR">
<title>초간단 테이블</title>
</head>
<body>
<!--    <table border="2" bordercolor="blue" width="300" height="300">-->
    <table border="2" bordercolor="blue" width="100%" height="300">

	<th>테이블</th>
	<th>만들기</th>
	<tr align="center"><!-- 첫번째 줄 시작 -->
	    <td colspan="2">합쳐진칸</td>
	    
	</tr><!-- 첫번째 줄 끝 -->
	<tr><!-- 두번째 줄 시작 -->
	    <td>첫번째 칸</td>
	    <td>두번째 칸</td>
	</tr><!-- 두번째 줄 끝 -->
    </table>
</body>
</html>
```

### table bgcolor

```
	칸 색채우기
	
	<tr bgcolor="sky blue"><!-- 두번째 줄 시작 -->
```

## div태그

```
div태그 : division의 약자, 레이아웃, 기능없음,
CSS와 연동하여 사용

<div style="background-color:yellow">구역1</div>
<div style="width: 100px; height:100px; background-color:#CF0">구역2</div>
<div style="background-color:blue">구역3</div>
<div style="background-color:red">구역3</div>

구역1
구역2
구역3
구역3
```

## span 태그

```
span태그 :기능없음 ,css와 연동하여 사용
div는 줄바꿈, span은 줄바꿈을 하지않음
<span style="background-color:blue">구역1</span>
<span style="background-color:red">구역2</span>
<span style="background-color:blue">구역3</span>
<span style="background-color:red">구역4</span>

구역1 구역2 구역3 구역4
```

## ol태그 ul태그

```
##순서가 있는 목록
<ol>
	<li>목록1</li>
	<li>목록2</li>
</ol>
1.목록1
2.목록2
ol과 li는 실과 바늘 같은 관계로 항상 같이 쓰임

##순서가 없는 목록

<ul>
	<li>목록1</li>
	<li>목록2</li>
</ul>
목록1
목록2


<ul>
	<li>목록1</li>
	<li>목록2</li>
        <ol>
	        <li>목록1-1</li>
	        <li>목록2-2</li>
        </ol>

</ul>
목록1
목록2
	목록1-1
	목록2-2
```

## head태그

```
<html>
<head>
    <title>제목</title>
    meta:페이지 정보(페이지 설명,키워드,제작자,크롤링 정책)를 제공
    <meta charset="UTF-8"> #출력 글자 속성
    <meta name="keywords" content="노트북,컴퓨터,주변기기"> #검색에 키워드 제공
    <meta name="description" content="컴퓨터 판매 페이지입니다"> 
    <meta name="robots" content="all">

    <!--실행시 화면에 출력 되지 않음. 숨어 있는 태그
    title,meta,link,style,scrip태그 등이 위치-->
</head>
<body>
<!--어제부터 방금까지 공부 했던 모든 태그들이 위치-->
</body>
```

## 한국 인코딩 방식

```
한국 인코딩 방식: euc-kr, utf-8
euc-kr:ascii(1byte)+한글만 확장 사용=> 2byte
utf-8: 보편화된 인코딩
```

## form태그