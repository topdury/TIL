# js4

## 반복문을 이용한 태그 속성부여

```
<!--
<html>
    <head>
        <meta charset="utf-8">
        <title></title>
    </head>
    <body>
    <script>

            var coworkers = ['네이버카페', '네이버지식인', '네이버쇼핑', '네이버블로그'];
            var addrs=['section.cafe.','kin.','shopping.']
     </script>
    <ul>
        <script>
                var i = 0;
                while(i < coworkers.length) {
                    //document.write('<li>' + coworkers[i] + '</li>');
                    //document.write('<li><a href="http://a.com/' + coworkers[i] + '">' + coworkers[i] + '</a></li>');

                   document.write('<li><a href="http://'+addrs[i]+'naver.com/">' + coworkers[i] + '</a></li>');
                   //document.write('<li><a href="http://'+addrs[i]+'naver.com/">'+ coworkers[i] + '</a></li>');
                    i = i + 1;
                }


    </ul>


        </script>
```



## 태그와 js결합

```
<!-- <body>
        <h1>Array</h1>
        <h2>Syntax</h2>
        <script>
            var coworkers = ["egoing", "leezche"];
        </script>
        <h2>get</h2>
        <script>
            document.write(coworkers[0]);
            document.write(coworkers[1]);
            document.write(coworkers.length);

        </script>
    <h2>add</h2>
        <script>
            coworkers.push('duru');
            coworkers.push('taeho');
            document.write(coworkers.length);

            document.write('<li>1</li>');
            
            ##while문도 사용 가능 
           var n=0
            while(n<2){
            document.write('<li>2</li>');
            document.write('<li>3</li>');
                n++;
                }

        </script>
```

## 함수를 이용한 속성부여(onclick)

```
<!--함수를 활용한 속성부여 (onclik)-->
<html>
    <head>
        <title>WEB1 - JavaScript</title>
        <meta charset="utf-8">
        <script>
            var target = document.querySelector('body');
            if(this.value === 'night') {
                target.style.backgroundColor = 'black';
                target.style.color = 'white';
                this.value = 'day';

                var alist = document.querySelectorAll('a');
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = 'powderblue';
                    i = i + 1;
                }
            } else {
                target.style.backgroundColor = 'white';
                target.style.color = 'black';
                this.value = 'night';

                var alist = document.querySelectorAll('a');
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = 'blue';
                    i = i + 1;
                }
            }
        </script>
    </head>

<html>
    <head>
        <title>WEB1 - JavaScript</title>
        <meta charset="utf-8">
        <script>

        function nightDayHandler(self){ // this를 self로 받아줬음
            //alert("호출됬니?");

            var target = document.querySelector('body');//body태그를 target에 넣은것
            if(self.value === 'night') {
                target.style.backgroundColor = 'black';
                target.style.color = 'white';
                self.value = 'day';

                var alist = document.querySelectorAll('a');
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = 'powderblue';
                    i = i + 1;
                }
            } else {
                target.style.backgroundColor = 'white';
                target.style.color = 'black';
                self.value = 'night';

                var alist = document.querySelectorAll('a');//a태그는 모조리다 alist에 넣은것
                var i = 0;
                while(i < alist.length) {
                    alist[i].style.color = 'blue';
                    i = i + 1;
                }
            }
}
        </script>
    </head>
<body>
        <h1><a href="index.html">WEB</a></h1>

        <input type="button" value="night" onclick="nightDayHandler(this);">
                                                                  //여기서 this는 버튼을 의미하며 이벤트가 발생한 곳을 의미한다. 여기서는 클릭이 이벤트 이 버튼을 위 함수에 보내준다. 그리고 함수에서는 self로 받아줘야한다
        <ol>
            <li><a href="1.html">HTML</a></li>
            <li><a href="2.html">CSS</a></li>
            <li><a href="3.html">JavaScript</a></li>
        </ol>
        <h2>JavaScript란 무엇인가?</h2>
        <p>JavaScript (/ˈdʒɑːvəˌskrɪpt/),[6] often abbreviated as JS, is a high-level, interpreted programming language. It is a language which is also characterized as dynamic, weakly typed, prototype-based and multi-paradigm. Alongside HTML and CSS, JavaScript is one of the three core technologies of the World Wide Web.[7] JavaScript enables interactive web pages and thus is an essential part of web applications. The vast majority of websites use it,[8] and all major web browsers have a dedicated JavaScript engine to execute it.</p>

        <input type="button" value="night" onclick="nightDayHandler(this);">
    </body>
</html>
```































