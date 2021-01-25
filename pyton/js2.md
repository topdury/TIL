()

## 반복문

### while

```
    var i=0
        while(i<10){
        document.write("무한 코딩");
        i++; //i=i+1과 같음. i+=1가능 
        }
무한 코딩무한 코딩무한 코딩무한 코딩무한 코딩무한 코딩무한 코딩무한 코딩무한 코딩무한 코딩
```

### for

```
   
   for(var i=0;i<10;i++){
//순서 i=0부터 읽고 순서대로 읽은 후 명령을 실행한다. 하지만 다시 i=0부터 읽지 않음
       document.write("무한 코딩<br/>");
    }
무한 코딩
무한 코딩
무한 코딩
무한 코딩
무한 코딩
무한 코딩
무한 코딩
무한 코딩

###break
    var i=0;
    for(i=0;i<10;i++){
        if(i==5){
            break;
        }
       document.write(i+"무한 코딩<br/>");
    }
##break와 continue 사용가능
  for(i=0;i<10;i++){
        if(i==5){
            
            continue;
        }
       document.write(i+"무한 코딩<br/>");

    }
0무한 코딩
1무한 코딩
2무한 코딩
3무한 코딩
4무한 코딩
6무한 코딩##5를 continue하고 6으로 넘어감
7무한 코딩
8무한 코딩
9무한 코딩
    //퀴즈:1~100까지 수중에서 3의 배수만 출력
    /*for(var i=1;i<101;i++){
        if(i%3=0)
            document.write(i+"<br/>");
     }
*/


```

#### for 이중 

```
    for(var i=0;i<10;i++){
        for(var j=0;j<10;j++){
        document.write(i+j+"<br/>")}}

0,1,2,3,4,5,6,7,8,9,1,2,3,4,5,6,7,8,9,10,2,3,4,5,6,7,8,9,10,11,3,4,5,6,7,8,9,10,11,12,4,5,6,7,8,9,10,11,12,13,5,6,7,8,9,10,11,12,13,14,6,7,8,9,10,11,12,13,14,15,7,8,9,10,11,12,13,14,15,16,8,9,10,11,12,13,14,15,16,17,9,10,11,12,13,14,15,16,17,18,

	for(var i=0;i<10;i++){
        for(var j=0;j<10;j++){
        document.write(String(i)+j+",")}}
      //문자와 숫자가 만나면 숫자를 자동으로 문자로 바꾸고 계산 

//퀴즈 출력물을 파란색으로
  ##<p>를 해주면 결과를 태그로 묶임, 문자에 속성을주는 거기 떄문에 반드시 string을 거친후에 적용이 가능
   for(var i=0;i<10;i++){
        for(var j=0;j<10;j++){
        document.write(String(i)+j+"<font color='blue'><p>")}}

```

### for문 출력물 색입히기

```
//퀴즈 출력물을 파란색으로
  ##<p>를 해주면 결과를 태그로 묶임, 문자에 속성을주는 거기 떄문에 반드시 string을 거친후에 적용이 가능
    for(var i=0;i<10;i++){
        for(var j=0;j<10;j++){
        document.write("<font color='blue'>"+String(i)+j+"</font>"+"<p>")}}
```

## 함수(def)

```
    function numbering(){
    i=0;
    while(i<10){
    document.write(i);
    i+=1;
    }}
    numbering();

    //퀴즈 위 함수를 다섯번 출력

function numbering(){
for(var j=0;j<5;j++){
i=0;
    while(i<10){
        document.write(i);
        i++; //i+=1, i++, i=i+1 다 가능
        }document.write("<br>")
        }
        }
        numbering();

```

### def, alert

```
function f1(){
return "test";
return "guest"; //출력 안함 test를 return 하면서 함수는 종료
}
function f2(){
return "test2";
}

alert(f1()); //alert("test")
alert(f2());

```

### 함수 다중중첩

```
    function myf(a1,a2){
    return a1+a2;
    }
    alert(myf(10,20));
    
    함수가 중첩은 가능하지만 가독성이 떨어지므로 지양하자
    
    
```

### 함수의 다른표현

```
    var myf=function (a1,a2){
    document.write(a1+a2);
    }
    myf(10,20);
    마치 람다같음
```

## 배열

```
    /*
    배열:크기와 타입이 동일한 기억장소를 여러개 나열한 것,값을 여러개 저장하는 장소
    변수:값을 1개를 저장하는 장소
    */
    var n=['kim','lee',100,'park'];
    alert(n);
    
        function f(){
    return['aaa','bbb'];
    }
    var m=f()
    document.write(m[0]);
    //atom, editplus,...
    //배열을 선언하는 다양한 방법
    //파이썬 리스트와 비슷
    var myarr1=[];
    var odd=[1,3,5,7];
    var even=new Array(2,4,6,8); //even=[2,4,6,8]
    var mixarr=['a',1,3,new Data(), "today"];
    document.write(odd[2]);
    //c,java언어:배열(동일한 자료형의 데이터만 저장)
    
```

## .push(append),.pop

```
var arr=[1,2,3,4];
//alert(arr.length);
arr.push(5);
alert(arr); //1,2,3,4,5

p=arr.pop();
document.write(p) //5
```

## (un)shift 맨앞 데이터추가(제거)

```
var arr=[1,2,3,4];
arr.unshift(999); //맨 앞에 데이터 추가
alert(arr);
document.write(arr.shift()); //맨앞에 데이터 제거
document.write(arr)
//alert(arr.lenght);
```

## . indexOf

```
var arr=[1,2,3,4];
document.write(arr.indexOf(3));
//3이라는 자료의 인덱스(0번부터 시작)를 출력


//alert("hello world".indexOf('o')); //4
//"hello world"문자열에서 "o"의 인덱스?
//alert("hello world".indexOf('O')); //-1

//alert("hello world".indexOf('hi')); //-1
//alert("hello world".indexOf('hello')); //0

alert("hello world".indexOf('world')); //0
```

## .splice()

```
var fruits=['apple','banna','orange'];

var v=fruits.splice(1,2); //(시작인덱스,제거할 항목개수)
document.write(v+"<br/>");
document.write(fruits+"<br/>"); //apple
```

## .sort,.reverse

```
var fruits=['apple','banna','orange'];
fruits.sort(); //오름차순 정렬
fruits.reverse(); //내림차순 sort랑 같이 써야함
document.write(fruits+"<br/>");
```

## 객체생성 dict생성이랑 유사

```
    /*
    객체는 파이썬의 딕셔너리{키:값,키:값..} 와 비슷
    */
    //홍길동이라는 객체를 생성하는 과정 1
    //사람클래스-> 홍길동 객체 생성
	#1
    var hgd={};
    hgd['name']='honggildong';
    hgd['age']='28';
    hgd['gender']='m';
    document.write(hgd['name']);

    //홍길동이라는 객체를 생성하는 과정 2
    //사람클래스-> 홍길동 객체 생성
	//#2
    // hgd객체 생성, 속성: name,age,gender,birth
    //속성값 : honggildong, 28,m,..
    var hgd={
    'name':'honggildong',
    'age':'28',
    'gender':'m',
    }
    hgd.birth=1994; //데이터 접근시 .(점)을 사용
    document.write(hgd['birth']);
    
    
     //#3.new이용
    //new 클래스명 무조건 new뒤에는 클래스명이 나옴
    var hgd=new Object(); //단군할아버지(동물클래스)
    hgd['name']='honggildong';
    hgd['age']='28';
    hgd['gender']='m';
    //alert(hgd['name']);

    for(k in hgd){
        document.write(hgd[k]+"<br/>");}
```

## class

```
 동물 클래스 설계
                 동물클래스(먹는다,잠잔다,다닌다)-상속(부모)->아래(자식)
                 최상위 클래스를 정의할때는 일반적인것으로 해야한다 구체화되면
                 복잡해진다.
   파충류     양서류    포유류      갑갑류....
  뱀(기어다닌다),악어,...사람(생각한다,코딩한다)...
  독뱀  무독뱁
  독사 살모사 꽃뱀

  못생긴독사객체=new 독사();
  못생긴독사객체.먹는다();
  못생긴독사객체.기어다닌다();
  못생긴독사객체.코딩한다(); 에러




 상속:부모 클래스가 가지고 있는 동작, 속성 등을 자식클래스에게 물려주는것
 오버라이딩(overrideing,재정의):부모가 물려준 동작을 자식이 변경하는것
 자식은 부모로부터 물려받은 동작외에 다른 동작을 추가할수 있음

====>객체 지향 설계=>객체지향프로그래밍

 //사람클래스->홍길동 객체
 
 
    //new 클래스명 무조건 new뒤에는 클래스명이 나옴
    var hgd=new Object(); //단군할아버지(동물클래스)
    hgd['name']='honggildong';
    hgd['age']='28';
    hgd['gender']='m';
    //alert(hgd['name']);

    for(k in hgd){
        document.write(hgd[k]+"<br/>");} 
  //사람클래스(속성-성별,나이,이름,..;동작(함수,메서드)->객체 //클래스는 동작도 부여가 된다
 
    //객체의 속성과 메서드(동작)를 표현
     var hgd={
    //속성정의
    'list':{
    'name':'honggildong',
    'age':28,
    'gender':'m'},
    //메서드 정의 ,this(지금의 현재의 객체(hgd)를 지칭=파이썬에 클래스에 있는 self      랑 같음)
    'show':function(){
        for(var n in this.list){
       document.write(n+":"+this.list[n]+"<br/>");
       }
      }
      };


hgd.show() 
 
```

## max, min

```
Math.max()
Math.min()


var num_list=[52, 273, 103, 32, 57, 103, 31, 2]

document.write(Math.max.apply(null,num_list)+"</br>");

document.write(Math.min.apply(null,num_list));
```

## repeat() 문자열 곱셈을 하고싶다

```
for(i=1;i<10;i+=2){
document.write("*".repeat(i)+"</br>")}
for(d=7;d>0;d-=2){
document.write("*".repeat(d)+"</br>")}

주어진수만큼 문자열을 반복해서 붙임
```







