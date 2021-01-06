# Day 5

## ramdom.sample()

```
import random
print(random.sample(range(1,10000000000),2)) #중복 되지 않게 샘플을 뽑아줌
```

## def

```
입력(과일)->함수(믹서기)->출력(과일주스)
def 함수명(매개변수0개 이상):
    문장1
    문장2
함수 정의 구문
def am(a,b):
    return a+b, a*b #함수의 결과는 항상 1개 튜플형식으로 (덧셈,곱셈)만 존재
print(am(3,4))#(7,12)

함수 호출 구문

def add(a, b):
    sum=a+b
    print("add함수")
    return sum #res에 다시 결과를 보내줘라는 말임
print("호출전")
res=add(1,2) #prameter(인수)는 항상 맞춰줘야함
print("호출후")
print(res)
호출전
add함수
호출후
3
수행 순서
함수는 스스로 수행하지 않는다.호출해야만 수행
1) add(1,2)호출
2) add함수 수행 -> sum 리턴
3) sum이 res에 저장
```

### (입력값/출력값)이 없는 함수

```
#입력값이 없는 함수
def say():
    return "안녕"
s=say()
print(s)
안녕

#출력값이 없는 함수(return문이 없는 함수)
def add(a,b):
    print("두 수의 합은 :", a+b)
두 수의 합은 : 7

res=add(3,4)
print(res) #none return이 없으므로
None

#입력값/출력값 없는 함수
def say():
    print("안녕")
say()
안녕
```

### 매개 변수의 초기값을 설정한 함수 호출

```
#매개변수의 초기값을 설정하여 함수 호출
def add(a,b):
    print(b) #2
    print(a) #3
    return a+b
res=add(b=2,a=3)
print(res)
2
3
5

def add(a,b=3): # b를 초기에 3으로 책정했기 때문에 상관없음
    print(b) #3
    print(a) #2
    return a+b
res=add(2)
print(res)
3
2
5

def add(a,b=3): # 외부인수가 우선시 되어 3이 5로 바뀜
    print(b) #2
    print(a) #3
    return a+b
res=add(2,5)
print(res)
5
2
7

```

### 함수로 전달되는 인수의 개수가 정해지지 않은 경우

```
def add(*arg): #매개변수 명 앞애 *을 붙이면 튜플로 인식, /arg그냥 변수명임 특정 명령어 아님
    print(arg)
    res=0
    for i in arg:
        res+=i
    return res
r=add(1,2,3)
print(r)
(1, 2, 3)
6

#미니문제
def mul():

mul(1,2,3) #인수가 가변적

=>6출력

def mul(*arg):
    res=1
    for i in arg:
        res*=i
    return res
res=mul(1,2,3)
print(res)
6

#
def addmul(a,*arg):

    if a=="add":
        res=0
        for i in arg:
            res+=i
        return res
    elif a=="mul":
        res=1
        for i in arg:
            res*=i
        return res
#addmul(연산종류(add/mul), 피연산자들)
res=addmul("add",1,2,3,4)
print(res) #1+2+3+4의 결과가 출력 10
10

res=addmul("mul",1,2,3,4,5) #120
print(res) #1*2*3*4*5의 결과가 출력
120
```

## 변수의 scope (return, global)

```
변수의 scope 문제 : 이 경우 def 안에서 변수는 밖에 아무런 영향을 줄 수 없음

#scope
a=1
def mytest3(a):
    a=a+1 #함수 안에서 밖에 있는 변수를 쓰고 싶다면?2가지 방법 존재(return,global)

mytest3(a)
print(a)#이가 출력 됐으면...
함수 내부 a값을 지정해주지 않았기 떄문에 값이 안나옴

#1. return 사용
a=1
def mytest3(a):
    a=a+1
    return a
a=mytest3(a)
print(a)#이가 출력 됐으면...
2

#2 global 사용: 함수 안에서 함수 밖의 변수를 직접 사용가능
a=1
def mytest3_2():
    global a
    a=a+1

mytest3_2()
print(a)#이가 출력 됐으면...
2

```

## lamda

```
def 와 동일한 기능 수행하는 예약어
#함수 정의시 일반적으로는 def를 사용. 함수가 복잡하거나 def를 사용하지 못하는 곳에서는 람다 사용

1. def를 이용한 일반적인 함수 정의
def myadd(a,b):
    return a+b
res=myadd(2,3)
print(res)
5
#2. 람다를 이용한 함수 정의

myadd2=lambda a,b:a+b #흔하지 않음 원래 함수명을 안적어도됨
#함수명=lambda 매개변수1, 매개변수2,...:매개변수를 이용한 계산식
res=myadd(2,3)
print(res)
5


#람다 함수 형식
pt=lambda x:x+10
print(pt(1))

#람다 자체를 바로 호출
# (lambda  매개변수들:수식)(인수들))
print((lambda x:x+10)(1))


print((lambda x,y:x+y)(1,2))


#람다 함수 내에서는 변수를 생성할 수 없음
# print((lambda x:y=2;x+y)(1)) 문법에러
y=2 #변수를 미리 선언해야함
print((lambda x:x+y)(1))


#함수의 인수 부분에 간단한 함수를 적용하고자 하는 경우
def pt2(x):
    print(x)

    # return x+10
# pt2([1,2,3])->이건 안됨

def pt(x):
    return x+10
print(list(map(pt,[1,2,3])))
#[11, 12, 13]


def pt2(x):
    return x+10
print(list(map(lambda x:x+10,[1,2,3])))
#[11, 12, 13]

#람다 식으로 매개변수가 없는 함수 표현(거의 안씀 참고)
print((lambda : 1)())
x=10
print((lambda : x)())
```

## 연습문제

```
def mymax(*arg): #매개변수도 구현
    #구현
    max_num=max(arg)
    return max_num

print(mymax(5,1,3,2)) #5
print(mymax(2,7,9)) #9

def mymax(*arg): #매개변수도 구현
    #구현
   print(max(arg))
mymax(5,1,3,2) #5
mymax(2,7,9) #9

for 문
def mymax(*arg):
    m=0
    for i in range(len(arg)):
        if m<arg[i]:
            m=arg[i]
    return m

print("최댓값 :",mymax(5,1,3,2)) #5
print("최댓값 :",mymax(2,7,9)) #9


#2
fl=['test.c','test2.h','sample.py','smaple2.c']
#확장자가 c이거나 h인 파일 이름을 모두 화면에 출력

for i in fl:
    res=i.split(".")
    if res[1]=="c" or res[1]=='h':
        print(i)

for i in fl:
    if i[-1]=="c"or i[-1]=="h":
        print(i)




```

## 과제 

```
#1. 리스트에서 20 보다 작은 3의 배수를 출력하라
ls=[13, 21, 12, 14, 30, 18]

for i in ls:
    if i<=20 and i%3==0:
        print(i)

#2. 리스트에서 세 글자 이상의 문자를 화면에 출력하라

ls = ["I", "study", "python", "language", "!"]

for i in ls:
    if len(i)>=3:
        print(i)

#3. 파일 이름이 저장된 리스트에서 확장자를 제거하고 파일 이름만 화면에 출력하라.

ls = ['hello.py', 'ex01.py', 'intro.hwp']
# hello
# ex01
# intro
for i in ls:
    i=i.split(".")
    del i[1]
    print(i)

#4. my_list를 아래와 같이 출력하라.
# 가 나
# 나 다
# 다 라

my_list = ["가", "나", "다", "라"]
for i in range(3):
    print(my_list[i],my_list[i+1])


#5. 반복문과 range 함수를 사용해서 my_list를 아래와 같이 출력하라.
# 라 다
# 다 나
# 나 가
my_list = ["가", "나", "다", "라"]

for i in range(3,0,-1):
     print(my_list[i], my_list[i-1])

#6.리스트에 5일간의 저가, 고가 정보가 저장돼 있다. 고가와 저가의 차를 변동폭이라고 정의할 때,
# low, high 두 개의 리스트를 사용해서 5일간의 변동폭을 volatility 리스트에 저장하라.

low_prices  = [100, 200, 400, 800, 1000]
high_prices = [150, 300, 430, 880, 1000]
volatility=[]
for i in range(4):
    volatility.append(high_prices[i]-low_prices[i])
print(volatility)

#7.리스트에 저장된 데이터를 아래와 같이 출력하라.
apart = [ [101, 102], [201, 202], [301, 302] ]

# 101 호
# 102 호
# -----
# 201 호
# 202 호
# -----
# 301 호
# 302 호
# -----

for i in range(3):
    i=apart[i]
    for d in range(2):
        if d==0:
            print(i[d],"호")
        else:
            print(i[d],"호")
            print("-"*5)





# 8. 구글 입사 test
# 1부터 10,000까지 8이라는 숫자가 총 몇번 나오는가?
# 
# 8이 포함되어 있는 숫자의 갯수를 카운팅 하는 것이 아니라 8이라는 숫자를 모두 카운팅 해야 한다.
# (※ 예를들어 8808은 3, 8888은 4로 카운팅 해야 함)

s="0"
for i in range(1,10001):
    i=str(i)
    s=s+i
print(s.count("8"))
```

















