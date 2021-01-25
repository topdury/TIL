# js3

## on 접두어

```

  버튼을 클릭 했을 때, 메세지 출력
  '~했을 때'에 해당되는 자바스크립트 이벤트를 지정하는 속성명은
  접두어가 on으로 시작되는 함수를 정의하여 이벤트 처리
  thrtjdaud = on+ "이벤트명"
  ex)onclick= 클릭 했을때
<input type="button" value="click me" onclick="alert('why click me?')">//클릭을했때 이벤트실행
ID:<input type="text" onchange="alert('changed')"/> 변경되면 이벤트 실행

  ID:<input type="text" onchange="alert('changed')"/> 
  PW:<input type="text" onkeydown="alert('key down')"/> #누르면 엘럿 박스가 뜨고 확인을 눌러야 입력됨 
  
	PW:<input type="text" onkeyup="alert('key up')"/> #누르꼬 때면 입력되면서 엘럿박스가 뜸

```

## trim() 공백없애줘

```
document.write("     hi     ".trim()+"<br/>"); //trim 양쪽공백dmf 없애줌
```

## input태그와 활용

### body태그배경에 색을 바꾸는 button

```
 <input type="button" value="black" onclick="document.querySelector('body').style.backgroundColor='black';">
## button을 눌르면 바디태그에 백그라운드 색을 검정을 바꿔줘

    <input type="button" value="black" onclick=
            "document.querySelector('body').style.backgroundColor='black';
document.querySelector('body').style.color='white';">
##여러것에 속성을 부여하고 싶으면 enter을 치고 추가로 적으면된다.
배경만이 아니라 바디에 글자색도 바꿔줘



    <input type="button" value="white" onclick="document.querySelector('body').style.
    
    
    ## button을 눌르면 바디태그에 백그라운드 색을 검정으로 바꿔줘
```

### 퀴즈

```
<!--퀴즈
배경이 black상태에서 toggle을 누르면 그대로,
배경이 white 상태로 toggle을 누르면 반전-->

<!--black버튼을 클릭했을 때,myblack이라는 id를 갖고 있는 대상의 value가 black과 같다면-->

<input  id="myblack" type="button" value="black" onclick="
if(document.querySelector('#myblack').value=='black'){
document.querySelector('#myblack').value='white';
document.querySelector('body').style.backgroundColor='black';
document.querySelector('body').style.color='white';

##버튼을 눌르면 만약 id가 myblack이고 value가 black이라면 
value 값을  white로 바꾸고 백그라운색을 검정으로 바꾸고 글자색을 흰색을 바꾼다.

} else{
document.querySelector('#myblack').value='black';
document.querySelector('body').style.backgroundColor='white';
document.querySelector('body').style.color='black';

##버튼을 눌르면 만약 id가 myblack이고 value가 black이 아니라면 
value 값을  black로 바꾸고 백그라운색을 흰색으로 바꾸고 글자색을 검정을 바꾼다.

<위 아래 코드가 같은 거임 id를 안쓰고 this.을 이용해 만듬>

<input type="button" value="black" onclick="
var target=document.querySelector('body'); ##taget에다가 바디태그 전체를 넣은거랑 같음, this는 파이썬 self랑 같음 
if(this.value=='black'){                       
target.style.backgroundColor='black';
target.style.color='white';
this.value='white';
}else{  
target.style.backgroundColor='white';
target.style.color='black';
this.value='black';
}
">
```



## 태그안에서 태그 기호쓰기 <>

```
<h1>2&gt;1</h1> 2>1
<h1>2&lt;1</h1> 2<1
```



