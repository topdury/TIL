# js5

````
<html>
    <head>
        <title>WEB1 - JavaScript</title>
        <meta charset="utf-8">
        <script>
        //문서 내의 모든 a태그의 색상을 전달받은 color값으로 설정
            function setColor(color) {
                var alist = document.querySelectorAll('a');
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = color;
                    i = i + 1;
                }
            }
            //배경 색상을 전달 받은 
            function nightDayHandler(self) {
                var target = document.querySelector('body');
                if(self.value === 'night') {
                    target.style.backgroundColor = 'black';
                    target.style.color = 'white';
                    self.value = 'day';

                    setColor('powderblue');
                } else {
                    target.style.backgroundColor = 'white';
                    target.style.color = 'black';
                    self.value = 'night';

                    setColor('blue');
                }
            }
        </script>
    </head>

    <body>
        <h1><a href="index.html">WEB</a></h1>

        <input type="button" value="night" onclick="
            nightDayHandler(this);
        ">

        <ol>
            <li><a href="1.html">HTML</a></li>
            <li><a href="2.html">CSS</a></li>
            <li><a href="3.html">JavaScript</a></li>
        </ol>
        <h2>JavaScript란 무엇인가?</h2>
        <p>JavaScript (/ˈdʒɑːvəˌskrɪpt/),[6] often abbreviated as JS, is a high-level, interpreted programming language. It is a language which is also characterized as dynamic, weakly typed, prototype-based and multi-paradigm. Alongside HTML and CSS, JavaScript is one of the three core technologies of the World Wide Web.[7] JavaScript enables interactive web pages and thus is an essential part of web applications. The vast majority of websites use it,[8] and all major web browsers have a dedicated JavaScript engine to execute it.</p>

        <input type="button" value="night" onclick="
            nightDayHandler(this);
        ">
    </body>
</html>
````

## //글자 색상을 전달받은 color값으로 설정

```
<html>
    <head>
        <title>WEB1 - JavaScript</title>
        <meta charset="utf-8">
        <script>
        //문서 내의 모든 a태그의 색상을 전달받은 color값으로 설정
            function setColor(color) {
                var alist = document.querySelectorAll('a');
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = color;
                    i = i + 1;
                }
            }
            //배경 색상을 전달 받은 
            
           
            function nightDayHandler(self) {
                var target = document.querySelector('body');
                if(self.value === 'night') {
                    target.style.backgroundColor = 'black';
                    target.style.color = 'white';
                    self.value = 'day';

                    setColor('powderblue');
                } else {
                    target.style.backgroundColor = 'white';
                    target.style.color = 'black';
                    self.value = 'night';

                    setColor('blue');
                }
            }
        </script>
    </head>

    <body>
        <h1><a href="index.html">WEB</a></h1>

        <input type="button" value="night" onclick="
            nightDayHandler(this);
        ">

        <ol>
            <li><a href="1.html">HTML</a></li>
            <li><a href="2.html">CSS</a></li>
            <li><a href="3.html">JavaScript</a></li>
        </ol>
        <h2>JavaScript란 무엇인가?</h2>
        <p>JavaScript (/ˈdʒɑːvəˌskrɪpt/),[6] often abbreviated as JS, is a high-level, interpreted programming language. It is a language which is also characterized as dynamic, weakly typed, prototype-based and multi-paradigm. Alongside HTML and CSS, JavaScript is one of the three core technologies of the World Wide Web.[7] JavaScript enables interactive web pages and thus is an essential part of web applications. The vast majority of websites use it,[8] and all major web browsers have a dedicated JavaScript engine to execute it.</p>

        <input type="button" value="night" onclick="
            nightDayHandler(this);
        ">
    </body>
</html>
```

## 객체의 이해

### 객체 속성 접근

```
<script>
var coworkers={
"programmer":"kim",
"designer":"lee"

}

document.write("개발자명:"+coworkers.programmer+"<br>");
document.write("개발자명:"+coworkers.designer);

//일일이 키값으로 호출하는건 불편하니까
for(var k in coworkers){//k에는 key값들이 들어갈거임
document.write(k+":"+coworkers[k]+"<br>");
}

</script>

```

### 객체 새로운 속성 추가

```
<script>
var coworkers={
"programmer":"kim",
"designer":"lee"

}

document.write("개발자명:"+coworkers.programmer+"<br>");
document.write("개발자명:"+coworkers.designer+"<br>");

coworkers["dataScientist"]="park" 방법1 (띄어쓰기해서쓰지마세요)
coworkers.dataScientist="park" 방법2(띄어쓰기해서쓰지마세요 대문자 쓰세요)


document.write("데이터과학자:"+coworkers.datascientist);

</script>
```

### 객체의 함수 적용 

```
<!--<html>
    <head>
        <title>WEB1 - JavaScript</title>
        <meta charset="utf-8">
        <script>
            function LinksSetColor(color) {
                var alist = document.querySelectorAll('a');
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = color;
                    i = i + 1;
                }
            }
            function BodySetColor(color) {
                document.querySelector('body').style.color = color;
            }
            function BodySetBackgroundColor(color) {
                document.querySelector('body').style.backgroundColor = color;
            }
            var Body = {//객체를 정의한후 메서드 적용
            setBackgroundColor:function(color){
            document.querySelector('body').style.backgroundColor = color;
            },
            setColor:function(color){
            document.querySelector('body').style.color = color;
                }

            }
            var Links = {
                setColor: function(color) {
                    var alist = document.querySelectorAll('a');
                    var i = 0;
                    while(i < alist.length) {
                        alist[i].style.color = color;
                        i = i + 1;
                    }
                }
            }



function nightDayHandler(self) {
                var target = document.querySelector('body');
                if(self.value === 'night') {
                    Body.setBackgroundColor('black');
                    Body.setColor('white');
                    self.value = 'day';

                    Links.setColor('powderblue');
                } else {
                    Body.setBackgroundColor('white');
                    Body.setColor('black');
                    self.value = 'night';

                    Links.setColor('blue');
                }
            }
        </script>
    </head>
<body>
        <h1><a href="index.html">WEB</a></h1>

        <input type="button" value="night" onclick="
            nightDayHandler(this);
        ">

        <ol>
            <li><a href="1.html">HTML</a></li>
            <li><a href="2.html">CSS</a></li>
            <li><a href="3.html">JavaScript</a></li>
        </ol>
        <h2>JavaScript란 무엇인가?</h2>
        <p>JavaScript (/ˈdʒɑːvəˌskrɪpt/),[6] often abbreviated as JS, is a high-level, interpreted programming language. It is a language which is also characterized as dynamic, weakly typed, prototype-based and multi-paradigm. Alongside HTML and CSS, JavaScript is one of the three core technologies of the World Wide Web.[7] JavaScript enables interactive web pages and thus is an essential part of web applications. The vast majority of websites use it,[8] and all major web browsers have a dedicated JavaScript engine to execute it.</p>

        <input type="button" value="night" onclick="
            nightDayHandler(this);
        ">
    </body>
</html>-->
```

## js 정규식 표현

```
</script>-->
<!--정규식을 표현하는 2가지 방법-->
<!--
<script>
    var re=/ab+c/; //1)정규 표현식을 슬래쉬로 감싸는 방법으로 표현
    var re=RegExp("ab+c");//2) RegExp 객체 생성 방법으로 표현.
</script>
//정규표현식의 예
/Chapter(\d+)\.\d*/
-->
```

## 실제 적용

```
<script>
    var myRe=/cdb{3}d*/;
    var myArray=myRe.exec("cdbbddbsbz");
    document.write(myArray); //null

</script>
-->
<script>
    document.write(/abc/.exec("this is abc")+"<br>");
    document.write(/abc/.exec("this is ab c")+"<br>"); //null

    document.write(/a\d/.exec("ab")+"<br>");//null
    document.write(/a\d/.exec("a1b")+"<br>");//a1


</script>
<script>
    //특수문자 앞에 역슬래쉬를 넣으면 단순 문자로 해석
    document.write(/a\*/.exec("aaaaaa")+"<br>");//null
    document.write(/a\*/.exec("a*aaaaa")+"<br>");//a*

    document.write(/^A/.exec("an E")+"<br>");//null
    document.write(/^A/.exec("An E")+"<br>");//A
    document.write(/[^A]/.exec("An E")+"<br>");//n
    document.write(/[^0-9]+/.exec("An E")+"<br>");//An E

    document.write(/t$/.exec("eat")+"<br>");//t
    document.write(/t$/.exec("eater")+"<br>");//null


    document.write(/(zoo)(bar)/.exec("zoo test bar")+"<br>");//null

    document.write(/(zoo) (bar)/.exec("zoo test bar")+"<br>");//null
    document.write(/(zoo) (bar)/.exec("zoo bar test")+"<br>");//zoo bar,zoo,bar


</script>

파이썬 정규표현식이랑 유사한 속성이많음
```