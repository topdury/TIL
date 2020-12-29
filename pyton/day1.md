# Day 1

| 단어                                            | 의미                                                         |
| ----------------------------------------------- | ------------------------------------------------------------ |
| for                                             | 반복하라                                                     |
| in                                              | 안에                                                         |
| str                                             | 문자                                                         |
| int                                             | 정수                                                         |
| float                                           | 실수                                                         |
| 리스트:[], 튜플:()                              | 딕셔너리,셋:{}                                               |
| pip install <name> (terminal명령)               | 설치                                                         |
| ;                                               | 한줄에 명령어 두개 사용할때 사용                             |
| //                                              | 몫 만                                                        |
| %                                               | 나머지                                                       |
| *                                               | 곱셈,반복                                                    |
| **                                              | 거듭제곱                                                     |
| int(5/2)=2, int('10')=10<br />print('10')= 일영 | 연산시 정수처리  숫자 처리 시문자에서 숫자로 변환            |
| float()                                         | 정수->실수                                                   |
| type ()                                         | 자료의 타입?                                                 |
| divmod(인수1,2)                                 | 몫과 나머지                                                  |
| =                                               | 메모리를 만듬(ex a=1[a라는 메모리를 만들고 1을 저장]<br />대입(res=dimod(8,3))<br />=br /> res=(2,2) |
| \n(엔터 위 돈표시)                              | 줄바꾸기 <br />ex) print("안녕 /n  반가워")<br />=안녕<br />   반가워 |
| \t                                              | 띄어쓰기                                                     |
| sep="B"                                         | 문자 사이마다 B  추가                                        |
| end=""                                          | ex)print("안녕",end=""); print("하새요")<br />=안녕하세요    |
| del                                             | 메모리 제거                                                  |
| None                                            | ex)b=None <br />값이 들어있지 b라는 변수                     |
| x=10<br />x+(-,/,%)=20                          | x=x+(-,/,%)20                                                |
| input()                                         | 문자를 삽입                                                  |
| len()                                           | 문자의 길이 측정                                             |

## int(정수)

정수

```
int()

print(int(3.3))
=3

print(int(5/2))
=2

print('10') 
=숫자 십이 아닌 그냥 일영

print(int('10')+2) #문자열 일영 => 숫자 10변환 ->+2 
  =12
```

## float(실수)

실수

```
float()

print(float(5))#정수->실수
=5.0

print(float(1+2))
=3.0

print(float('3.14'))
=3.14

print(float('3.14')*2) #'3.14' -> 3.14 -> *2 ->6.28
=6.28
```



## type():type 알려줘

```
print(type(10))
=int

print(type('10'))
=str
```

## divmod ():몫과 나머지

```
print(divmod(9,  4)) #9를로 나눈 몫과 나머지
             인수1 인수2
=(2, 1)
res=divmod(9,  4) #res=(2, 1) 튜플 1개, 요소2개(몫, 나머지)
print("결과:",res)

print("1번째 요소 : ", res[0]) #res 튜플에 저장된 1번째 요소값을 출력
=1번째 요소 : 2

print("2번째 요소 : ", res[1]) #res 튜플에 저장된 2번째 요소값을 출력
#튜플(리스트)에서 데이터의 위치는 0번부터 시작
=2번째 요소 : 1

res1, res2=divmod(9, 4) #변수 두개 가능

print("1번째 요소 : ", res1) #res 튜플에 저장된 1번째 요소값을 출력
=1번째 요소 : 2

print("2번째 요소 : ", res2) #res 튜플에 저장된 2번째 요소값을 출력
=2번째 요소 : 1
```

## n진법

```
print(11) #10진수

print(0b11), 2진수
=3

print(0o10), 8진수
=8
```



## \n("""""") \t :띄어쓰기 줄바꾸기

```
print("안녕!\n 반가워 \n잘있어요")
안녕!
반가워
잘있어요
x='인생은\n 짧다,\n 그래서 \n파이썬이 필요하다.'
or
x='''인생은
짧다,
그래서
파이썬이 필요하다.'''



print("할\t아\t버\t지")
할 아 버 지
```

## sep=:끼워 넣기

```
print("naver", "kakao", "samsung", sep='$')
=naver$duam$samsun

응용
print(1, 2, 3, sep='\n')
1
2
3
```

## end=:바로 따라오게

```
print(1,end='')    # end에 빈 문자열을 지정하면 다음 번 출력이 바로 뒤에 오게 됨
print(2, end='')
print(3)
=123
```

## del :변수 제거

```
a=1
del a
print(a)

없음
```

## intput: 넣을 값을 정해줘

```
x=input("출력하고 싶은 값을 입력해주세요? ") 
#입력을 맞은뒤 엔터 키를 누르면 다음 문장으로  순서: intput()이 먼저 가동하고 밑에 값을 치면 x에 저장된다

print("당신이 입력한 값은:",x)

x=input("첫 번째 수 입력 : ")
y=input("두 번째 수 입력 : ")
#input 함수로 입력 받은 모든 데이터는 '문자'로 간주

print("덧셈 결과는 ",x+y)


x=int(input("첫 번째 수 입력 : "))
y=int(input("두 번째 수 입력 : "))

print("덧셈 결과는 ", x+y)

x=float(input("첫 번째 수 입력 : "))
y=float(input("두 번째 수 입력 : "))

print("덧셈 결과는 ", x+y)
```

## .split() :분리해줘

```
x,y=int(input("숫자 두개 입력: ").split())# 에러 발생 "1,2" -> int(1,2)

print(x+y)

x,y=input("숫자 두개 입력: ").split()
print(int(x)+int(y))#에러 발생 안함
or

x1,x2=map(int,input("숫자 두개 입력: ").split())
print(x1+x2)

```

## 인덱싱:참조해 x[]

```
x="life is too shrot"
print(x[8:-3]) #too sh


print(x[5]+x[6])
=print(x[5:7])#범위를 지정하여 슬라이싱 [시작위치: 끝위치 +1]

print(x[12:17])
print(x[12:])#끝위치를 지정하지 않으면, 문자열의 마지막까지 참조

print(x[:4])#맨 앞에서 3번인덱스까지 출력
print(x[:] #전체

응용
x="pithon"
print(x)
print(x[1])
x[1]="y" #에러 : 문자 /문자열의 요소값(p,i,t,h,o,n)은 변경이 안됨
x=x[0:1]+"y"+x[2:]
print(x)

python
```

## len()

```
x="life is too shrot"
print(len(x))#문자 길이 측정

17
```

## 포매팅 %(F,s,d)

```
x=5
print("I eat %d egg" % x) #문자열 포매팅 , %d(decimal)

x = "two"
b = 3
per = 30

print("I eat %s eggs. so I was sick for %d days. %d%%" % (x, b, per))
=I eat two eggs. so I was sick for 3 days. 30%

%F: 실수 %s :문자 %d: 정수
```



## map(mapping:사상)

```
함수출력=map(함수,함수 입력):
x1,x2=map(int, ["3", '4'])

print(x1+x2)

입력값을 컴마로 구분

x1,x2=map(int,input("숫자 두개 입력: ").split(",")) #"1,2"-> ['1','2'] -> [1,2]-> x1=1, x2=2
print(x1+x2)
```



## 자리 바꿔서 출력

```
x,y=1,2
a=y
y=x
x=a
print(x,y) 

2 1

x,y=1,2
x,y=y,x
print(x,y)

2 1
```

## 변수만 만들고 값은 저장하고 싶지 않을 경우

```
b=None # 사과바구니 자체가 없음
=None

print(b)
b='' #b라는 이름의 사과바구니에 사과가 1개도 없음
''는 None이 아님
=
```