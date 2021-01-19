# css1

```
css: 웹페이지에 출력할 내용과 스타일(표현 방식)을 분리하기 위해 생겨남
태그들에게 어떤 스타일 효과를 적용하는 언어

선택자: 어떤 태그들에게 스타일을 적용할 것인지 정의하기 위한 문법
선택자 문법 예시
선택자{
속성1:값;
속성2:값;
}


css 선택자 종류(3가지)
태그 선택자,id 선택자, class 선택자
```

## css

```
<!--2)<style> 태그를 이용하여 html 문서에 css 작성-->
<div style="color:red">문서입니다</div>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style type="text/css">
        .my-text{color:blue} #.my-text라는 이름으로 묶인 색상을 파란색으로 설								정
    </style>
</head>
<body>
    <div class="my-text">this is blue</div> #파란색으로 나옴

</body>
</html>



```

## css 선택자 

### 태그 선택자

````
<!--css 선택자 종류(3가지)-->
<!--태그 선택자,id 선택자, class 선택자-->
<!--태그이름{속성1:속성1값;....}-->
<html>
<head>
    <style>
        h5{color:#F00}
        h6{color:#00F; font-size:20px}
    </style>
</head>
<h4>h4태그</h4>
<h5>h5태그</h5> #빨간색
<h6>h6태그</h6> #파란색 폰트크기 20

</html>

````

### id ,class선택자

```
<!--2.id 선택자-->
<!--#아이디{속성1:속성1값;....}-->
<!--.클래스{속성1:속성1값;....}-->
<html>
<head>
    <style>
        #mybox{background-color:#09c; width:200px; height:50px;}
        .yourbox{border:2px solid green}
    </style>
</head>
<body>
    <div id="mybox">스타일</div>
    <div class="yourbox">스타일</div>

</body>
</html>

```

### 부모 자식 선택자

```
<!--부모 자식 선택자
선택자1(부모) 선택자2(자식) {속성1:속성갑; 속성2:속성값;}
부모 태그 하위에 있는 자식 태그에 있는 스타일을 적용-->

<html>
<head>
    <style>
        div.yello_box{background-color:yellow;}
        div.sb_box span{background-color:skyblue;}
        div#c_box span{text-align:center;padding:10px;color:green}
        ##padding: 여백(들여쓰기 느낌)
    </style>

</head>
<body>
<div> div 태그 부분입니다</div>
<div class="yello_box"> div 태그 부분입니다</div>
<div class="sb_box">
    <span>
        div 태그 Yello_box span 부분입니다
    </span>
</div>

</body>

</html>

```

### padding

#### 부모 선택자 응용

```
        .aa>.cc{background-color:yellow}
        .xx.yy{background-color:skyblue}

    </style>

</head>
<body>
<div class="aa">
    <div class="cc">
        aa와 cc클래스에서 꺽쇠는 부모 자식간에 직접적인 관계
    </div>
</div>
적용이 잘됨


<div class="aa">
    <div class="bb"></div>
     <div class="cc">
        aa와 cc클래스 사이에 bb클래스가 있음(부모 자식사이에 다른 클래스가 존재
     </div>
    </div>

</div>
적용이 안됨 >가 있으면 사이에 아무것도 없어야함



<div class="xx">
    <div class="kk"></div>
     <div class="yy">
         xx와 yy클래스에서 꺽쇠는 부모 자식간에 직접적인 관계
     </div>
    </div>
</div>
적용이 잘됨 이건 스크래핑시에도 적용 가능

```

#### 다중선택 선택자(and or)

```
<!--
and조건
태그이름#아이디{}
태그이름.클래스명{}
.쿨래스#아이디{}
...
-->
<!--선택자 사이에 공백이 없으면 여러선택자들을 동시에 만족하는 태그에 대해 스타일 적용-->


<!--
or조건
#아이디,.클래스명{}
태그이름,.클래스명{}
쉼표로 구분 된 여러 선택자 중에서 어느 하나 이상에 선택자 조건을 만족하는 태그에 스타일 적용
-->


<html>
<head>
    <style>
        div#m_box{color:blue;}
        div.box{color:red;}
        div, .box{color:skyblue;}

    </style>

</head>
    <div id="m_box">mbox</div>

<div class="box">box</div>
<div>div태그</div>
<span class="box">span</span>
</html>



```









































