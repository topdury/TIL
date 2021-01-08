# Day6

## .count()

```
***count는 str에만 사용만 사용 가능***


sum=0

for i in range(10001):

    sum+=str(i).count('8')
print(sum)


print(str(range(1,10001))) #될꺼 같지만 안됨 문법에 오류
print(str(list(range(1,10001)))) # 이건 됨 [1,2,3,...,10000](전부 str임)

a=[111,222,321]

print(a[0]+10)#121
print(str(a[0]).count("1"))#4
#print(str(a[2]).count("1")

```

## 파일 입출력

```
입출력 종류: 표준,파일,네트워크
파일 입출력
-open() :  파일 열기 -> 파일 입(read)/출력(write) -> 파일 닫기(close)
휴대폰-메모리(램) 2GB-게임(1Gb),음악(500MB),인터넷(500MB) => 외부에서 전화가 걸려옴(전화앱 실행)

#파일에 문자열 출력(크기)
f=open("hello.txt","w")#파일을 쓰기 용도로 열기
#open(파일명,모드)
#프로그램 상에서는 쓰기 모드로 열려있는 hello.txt파일이 f라는 이름으로 사용됨

f.write('hellp world')
f.close()

#파일로부터 문자열 입력(읽기)
f=open("hello.txt", "r")
s=f.read() #읽은 내용을 s에 저장하라
print(s)
f.close()
```

### with ~ as

```
with ~ as #파일을 사용한 뒤에 자동을 파일을 닫아줌
with open(파일이름,모드) as 파일변수:
    코드

with open("hello.txt", "r") as f:
    s=f.read()
    print(s)
close 작업을 자동으로 수행
```

#### with open(파일명, "w")

```
#w모드로 열게 되면 기존에  작성되어 있던 내용은 사라짐
#with open("hello.txt", "w") as f:
   
   for i in range(10):
       
       f.write("hello world {0}\n".format(i+1))


#리스트의 내용을 파일에 출력

#리스트는 그냥 write로는 출력이 안됨 #writelines사용

lines=['hello\n','nice to meet you\n','bye\n']

with open("hello.txt", "w") as f:
   
   f.writelines(lines)
```

#### with open(파일명,"r")

```

# with open("hello.txt", "r") as f:
     s=f.read() #read함수는 1글자씩 읽어들임
     print(s)



# with open("hello.txt", "r") as f:
     s=f.readline() #readline함수는 1줄씩 읽어들임

     print(s) # hello 한줄만 읽어버림그래서for 또는 while 문과 함께 사용

 with open("hello.txt", "r") as f:
    line=None
     while line !="":
         line= f.readline()  # readline함수는 1줄씩 읽어들임
         print(line) #2줄이 바뀜
         # print(line.strip("\n"))  #\n을 삭제

# with open("hello.txt", "r") as f:
     line=f.readlines()
     # for i in range(len(line)):
     for i in line:
         print(i.strip("\n"))
```

## 피클링(pickle)

````
피클(pickle):파이썬 객체를 파일로 저장하고자 하는 경우에 사용되는 모듈

# 피클링 : 객체->파일
# 언피클링 : 파일->객체


# 문자열,문자열 객체
# hello
# nice to meet you
# bye


#객체를 파일로 저장
import pickle
내용물="단팥"
색상="파랑"
너비="20센티"
높이="10센티"
가족명단={"잉어":30,"꽃게":10,"상어":40}
#객체를 저장 할때는 wb 모드로 파일 열기
with open("myfish.p","wb") as f:
    pickle.dump(내용물,f)#단팥
    pickle.dump(색상,f)#파랑
    pickle.dump(너비,f)
    pickle.dump(높이,f)
    pickle.dump(가족명단,f)

import pickle
with open("myfish.p","rb") as f:
    내용물=pickle.load(f)
    색상=pickle.load(f)
    너비=pickle.load(f)
    높이=pickle.load(f)
    가족명단=pickle.load(f)

    print(내용물)
    print(색상)
    print(너비)
    print(높이)
    print(가족명단)
# 엑셀 작업 -> 저장(xls,binary)->메모장은 깨짐


f=open("hello.txt", 'a')
for i in range(3):
    f.write("%d번째 줄 추가\n" %(i+1))
f.close()

클래스? 붕어빵 기계
객체?붕어빵
메서드(동작)?굽는다,...

atrribute(속성)?내용물 ,크기,모양,...너비,높이
````

## 클래스

```
클래스는 객체의 구조와 행동을 정의합니다.
객체의 클래스는 초기화를 통해 제어합니다.
클래스는 복잡한 문제를 다루기 쉽도록 만듭니다.

res=0

def add(n):
    #n에 전달된 값은 res에 저장
    global res
    res+=n

add(3)
print(res)
add(4)
print(res)

===============================================================================================
res1=0 #전역변수
res2=0
#편의점->계산대->계산대2대->
#1번계산대
def add1(n): #지역 변수
    #n에 전달된 값은 res에 저장
    global res1
    res1+=n
    return res1

print(add1(3000)) #맥주
print(add1(5000)) #오징어
3000
8000
#2번계산대

def add2(n): #지역 변수
    #n에 전달된 값은 res에 저장
    global res2
    res2+=n
    return res2

print(add2(1500)) #막걸리
print(add2(2000)) #두부
1500
2000

위와 같이 각 객체마다 변수를 변화시켜줘야함 
=======================================================================================================
각각의 계산대를 객체로 간주하고, 계산대의 특성 또는 동작등을 일빌반화시켜 놓은 틀

# 정/부정관사
# a car(클래스)
# the car(객체)
#사람(클래스): 실체가 없음
#사람홍길동(객체), 사람임꺽정(객체): 실체가 있음

class Calculator: #클래스명은 대문자로 시작하는 것이 약속
    def __init__(self): #현재 객체를 self라고 함
        self.res=0
        print("init함수가 호출 됬네?")
    def add(self, n):
        self.res+=n*0.9
        #10%할인코드를 여기에 작성->모든 계산대에 적용

        return self.res

cal1=Calculator() #클래스로붙 객체를 생성(init함수 자동 호출). 계산대(클래스)로부터 계산대1(객체==cal1)을 생성
cal2=Calculator() #클래스로붙 객체를 생성(init함수 자동 호출. 계산대(클래스)로부터 계산대2(객체==cal2)을 생성

print(cal1.add(3000))
print(cal1.add(5000))

print(cal2.add(1500))
print(cal2.add(2000))



```

## 모듈

```
변수#모듈? 변수,함수,클래스 등을 모아 놓은파이썬 파일. 다른 프로그램에서 모듈을 불러올 수 있음

다른 파일에 함수를 만들었음
# print(madd(1,2)) # import로 이 함수의 모듈을 활성화 시키지 않았기 때문에

# import mod1
# print(mod1.madd(1,2))

# import mod1 as m #모듈(패키지) 명이 길때 축약해서 표현
# print(m.madd(1,2))

# import pandas as pd
# import numpy as np
# # 폴더안에는 파일/서브폴더
# import malotlib.pyplot as plt

#import 모듈이름(확장자는 안씀)

# import mod1

# from mod1 import msub
# #mod1 모듈에 정의되어 있는 msub메서드만 가져와라
# print(msub(2,1))#1

#모듈에서 두개 이상 함수 가져올 때
# from mod1 import madd
# from mod1 import msub
## from mod1 import madd, msub
# from mod1 import * #모든 함수를 가져와라
#
# print(madd(3,2)) #5
# print(msub(10,3)) #7



#모듈을 가져왔을 때 가져온 모듈에 결과가 출력될 수 있다 그럴 경우
#가져온 모듈에서if __name__=="__main__":를 넣어주고 print를 들여쓰기를 해주면됨


# if __name__=="__main__":
#     print(madd(3,2)) #5
#     print(msub(10,3))

#mod1.py를 시행시키면 __name__이라는 특별한 변수의 값으로 __main__이 저장됨.
#따라서 if __name__=="__main__": 조건식이 참이 됨
```

## 과제



































