# js 1

```
정적인 페이지:html,css
동적인 페이지:javascript(객체 기반(클라이언트 스크립트) 언어, 동작을 클라이언트에서 함,확장자 js)
php,jsp,asp등(서버스크립트 언어, 동작을 서버에서 함)
생성된(form 클래스) 객체를 이용하여 동적인 페이지를 기술하는 언어

클래스 -> 객체생성(속성 초기화) -> 객체 동작...
붕어빵기계 -> 붕어빵(크기:5센티, 내용물:팥,...)->붕어빵을 굽는다,....
자동차->자동차(색상:빨강, 배기량:3000,...)->달린다,멈춘다...
신(조물주,...)->사람(코:1개, 눈:2개,...) ->먹는다, 잔다...
날씨 -> 날씨예보객체 -> 오늘(현재)의 날씨(기온)는 맑음(흐림,눈,비,...)입니다


사람객체와 자동차객체간 동작(ex. 사람이 자동차에 탄다, 사람이 자동차를 운전한다...)

<java script 작성법>
1)html 문서 내에 작성
2)별도로 파일(js)
```

## java script

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <script type="text/javascript">
        var a=10 //var는 variable 약자로서 변수를 의미
        var b='k';
        document.write(a);
        document.write(b);
        document.write(' ');

        var c=0.5;
        var d=-3.2;
        var e=0x1af; //16진수(0x)
        var f=010;  //8진수(0)
        document.write(c);
        document.write(d);
        document.write(e);
        document.write(f);
        document.write(' ');
        var k='5';
        //document.write(k+2); //문자+숫자-> 문자+문자->문자결합
        document.write(parseInt(k)+2);
        //parseInt():문자로 된 숫자를 숫자로 변환해주는 함수, '5'->5

        document.write(parseInt('hello')); //NaN
        document.write(Math.sqrt()); //square root(제곱근)
		document.write(3/0); //Infinity
/*
자바스크립트 자료유형
Boolean:참 또는 거짓
String:문자열
Number:숫자형
null:빈 값
Nan:Not a Number, 숫자 아님
Infinity: 무한대
*/
        /*function myfunc(){ //함수 정의
            return 3;
           }
         ret=myfunc(); //함수 호출
         document.write(ret);*/


    </script>
    <!--    test.js파일 불러오기-->
    <!--<script type="text/javascript" src="test.js"></script>-->

    <!--객체.동작(내용);
    <script type="text/javascript">
        document.write("hello");

    </script>-->

####그냥 body에서 <script> 만해줘도 javascrip을 쓸수 있음

```

### 주석

```
줄은 //  여러줄이면 /* 내용*/
```

## alert함수

```
창을 띄어서 결과를 내줌


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <script>
        alert('Hello world')
        alert(1+2)

    </script>

</body>
</html>

    //alert(7%4); #3

    var a=1
    //alert(a+1); #2
    //alert((10+20)/10+2); 5
```



### length

```
    alert("안녕".length);//문자열 길이

```



## pow,sqrt 제곱과제곱근

```

<script>
document.write(Math.pow(3,2)); //power 제곱함수
document.write(Math.sqrt()); //square root(제곱근)
</script>
```

## 반올림,올림,내림

```
    document.write(Math.round(1.7)+"<br/>"); //round 반올림함수
    document.write(Math.ceil(1.2)+"<br/>"); //ceil:올림
    document.write(Math.floor(2.9)+"<br/>"); //floor:내림
```

## typeof 함수(타입을 출력)

```
    함수지만 독특하게 괄호를 안씀 
    document.write(typeof "1"+"<br/>"); string
    
```

## 줄바꾸기

```
##함수마다 다름 

    //alert("안녕\n하세요.\n자바스크립트");//줄바꾸기
    document.write("안녕<br/>하세요."+"<br/>");//줄바꾸기
    document.write("안녕\n하세요.\n자바스크립트"+"<br/>");//그냥 공백
```

## 불인 연산자

```
document.write("one"!="two"); //ture !==도 같음
document.write("one"!=="two"); //false

document.write(1!=2); //ture
document.write(1!=2); //false



//1은 ture 1이 아니면 false
document.write(true==1); //ture
document.write(true=="1");//ture
document.write(true==0); //false
document.write(true=="0");//false
document.write(true==2); //false
document.write(true=="2");//false

//alert(1==2);//false
//alert("1"==1);ture //내부적으로 (비교)연산을 하기 전에 자동으로 형변환
//alert("1"===1);//false //형변환 수행 안됨
```

## if문

```
  ####퀴즈1
  /*
아이디를 입력받은 후, 아이디가 "master" 와 같으면 "아이디가 일치합니다"
다르면 "아이디가 일치하지 않습니다"fmf alert창으로 출력하시오.
*/

  id=prompt("아이디:");
  if("master"==id){
  alert("아이디가 일치합니다")}

   else{
   alert("아이디가 일치하지 않습니다")
   }
  //document.write(id+'<br/>');
  
  /*
퀴즈 2
아이디를 입력받은 후, 아이디가 "master" 와 같으면 비밀번호를 입력받고,
비밀번호가 "1234"와 같으면 "인증에 성공하였습니다"
다르면 "인증에 실패하였습니다"
아이디가 "master"와 다르면
다르면 "아이디가 존재하지 않습니다"fmf alert창으로 출력하시오.
*/
  
      id=prompt("아이디:");
  if("master"==id){
  pw=prompt("비밀번호:");
  if("1234"==pw){
  alert("인증에 성공하였습니다")}
  else{
  alert("인증에 실패하였습니다")}
  }

   else if("master"!=id){
   alert("아이디가 존재하지 않습니다")
   }
  
  






    //else가 나오면 무조건 앞 조건이 부정이어야 작동함
if(false){
alert(1);
}
else if(true){
alert(3);
}
else if(true){
alert(4);
}
else{
alert(5);
}
/*
if(ture){
alert(1);}
else{
alert(2);}
*/






    /*
    if(조건){
    수행할 문장;
    }
    */
    /*
    alert(2>1);
    if(ture){
        alert("1");
        alert("2");
    }
    alert("3); //조건문과는 별개로 동작
    */
```

