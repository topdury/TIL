# Day 2

## offset: 몇칸 건너뛸래?

```
s="파이썬파이썬파이썬"
print(s[::3])#offset:몇 칸을 건너 뛸것인지
파파파

#양수(죄->우), 음수(우->좌)
ex)print(S[::-1]) 거꾸로
```

## .replace( ) 문자열에 치환,없애기

```
replace 함수 : 문자(열) 치환

tel="010-1234-5678"

print(tel.replace("-","")) 

01012345678
```

## bool: 참,거짓 자료형

```	
print(1>2) #비교 연산자에 결과는 true,false로 나옴'

print(2==2)# '='하나는 대입에 의미 이기 때문에 오류남

print(3!=2) # != :not equal

print('python'=='Python') #대문자와 소문자를 다르게 인식함


a=1
b=1
print(a==b)#== 두 값이 같은지를 비교
print(a is b)#두 객체(주소가 동일)를 비교

참고
print(1==1.0) #정수와 실수라는 점에서 차이가 있긴 하지만, 값은 같다
print(1 is 1.0) # 1은 실수 객체  1.0은 실수 객체 그래서 두 객체는 같지 않다.

논리 연산(중요) : and(모두 참 ->참), or(하나 이상 참 ->참, not(참->거짓, 거짓->참)0
print(True and False)#false
print(True or False)#true
print(not False)#true


print(1==1 and 2!=1) #false

print(3>1 or 1<2) #true

print(not 1>2)#true

0:False, 1:True, 0이 아닌 모든 수가 True 로 사용 (중요)
bool(숫자,문자열) 참,거짓

print(bool(1))#true

print(bool(0))#false

print(bool(0.5))#true

print(bool('test'))#true

print(bool(''))#false

print(bool(0 or 'test'))#true
```

## .count .find .index

```
a="hello"
print(a.count('l'))
=2

#위치 확인
print(a.find('l')) #위치:2, 여러개 있는 경우에는 맨 처음 나온 위치가 출력
print(a.find('x')) #-1:문자가 없는 경우

print(a.index('l'))
print(a.index('x')) #에러발생 : 문자가 없는 경우
```

## " ".join : 문자열 삽입

```
#문자열 삽입

print(",".join("abcd"))
print(",".join(['a','b','c','d']))
#리스트에 저장되어 있는 각각의 문자들이 컴마(,)와 결합하여 하나의 문자열("a,b,c,d")이 됨

print("".join(['a','b','c','d']))
#"abcd"
```

## 대문자 소문자 변환

```
.upper, .lower

a='hi'

print(a.upper())
a=a.upper()
print(a)

a=a.lower()
print(a)
```

## .strip(): 공백 지우기

```
n1="  대한민국"
n2="대한민국  "
n3="  대한민국  "
print(n1.lstrip())
print(n2.rstrip())
print(n3.strip())

정규표현식: 문자열 전처리
[l/r]scrip("삭제대상문자들")
str=",  python,."
print(str.lstrip(","))
print(str.lstrip(" "))#맨 앞에 (,)때문에 막힘 
print(str.lstrip(" ,"))# 큰따옴표 안에 제거대상 문자를 나열(순서 상관없이)
print(str.lstrip(", "))
print(str.lstrip(" ,."))
print(str.rstrip(" ,."))

print(str.strip(" ,."))#좌우 전부 지움
```



## import string.punctuation: 구두점 사용

```
punctuation(구두점) : !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~

함수: 1.내장함수 2.외장함수- import를 해줘야 작동
str=",  python,."

import string 

print(str.strip(string.punctuation))
  python

print(str.strip(string.punctuation+" "))
python
```

## .just :정렬

```
print('pytion'.ljust(10)) #10 확보 후 좌측 정렬

print('pytion'.ljust(10)) #10 확보 후 우측 정렬

print('pytion'.center(10)) #10 확보 후 가운데 정렬
```

## 메서드(함수) 체이닝->코드간결

```
print('python'.rjust(10).upper())
    PYTHON
```

### .zfill(): 패딩(특정값으로 빈자리 채움)

```
print("hellow".zfill(10))
0000hellow
```

## 리스트[]

```
리스트 안에 값 =요소 

x=[10,20,30] # x리스트의 0번 index 요소값:10

y=['life', 'is', 'too', 'short']
print(y[0])

# 리스트의 다양한 자료형을 저장 할수있음
z=[1,2,3,'life', 'is', 'too', 'short', True, 3.14]
print(z[0])

# 리스트에는 리스트를 요소값으로 할 수 있음
a=[1,2,['life', 'is',['too', 'short']]] #a 변수에는 요소가 3개
print(a)
print(a[2])#['life', 'is']
print(a[2][0])# life
print(a[2][1])# is

print(a[2][2][0]) # too

#리스트의 연산

a=[1,2]
b=[3,4]

print(a+b)#[1,2,3,4]
print("ab""cd")

print(a*3)
print("ab"*3)
print(len(a)) #2

# print(a[0]+"hi") 에러 발생!!!(정수와 문자열은 더할 수 없으므로)

print(type(a[0]))
#str 함수: 정수나 실수를 문자열로 변환해주는 함수
str(a[0]) #숫자 1-> 문자열 "1"

print(str(a[0])+"hi")

```



### 리스트의 요소값 변경

```
리스트 요소 값 변경
a=[1,2,3]

a[2]=4
print(a)


# 리스트의 특정 위치에 데이터 추가 : insert
a=[7,8,9]
# 7과8사이에 4추가
a.insert(1,4)#a리스트에 1번째 자리에 4를 추가하겠다
print(a)
=[7,4,8,9]

# 리스트의 요소를 제거 : del, remove, pop

#del : 특정 위치에 저장된 값을 제거 (예약어:함수가 아님)
a=[10,20,30]

del a[1] #지정 위치 제거
print(a)
==========================================
a=list(range(1,10))
print(a)

del a[:5]#0~4번 index 까지 삭제
print(a)
=[6,7,8,9]

# remove : 특정 값을 제거
a=[10,20,30,10,20,30]

a.remove(30) #첫 번쨰 30만 제거 [10,20,10,20,30]
a.remove(30) #두 번쨰 30 제거[10,20,10,20]
print(a)

# pop :가장 마지막 위치에 있는 데이터를 제거

a=[10,20,30]
a.pop()

print(a)
=[10,20]
```

### 리스트에 추가

```
#.append() ,.extend # 리스트에 추가
a =[1,2,3]
print(a)

print(a+4)(x)

print(a+[4])
=[1,2,3,4]

a.append(4)
print(a)
a.append([5,6,7])# 리스트 안에 리스트가 요소로 추가
print(a)
= [1,2,3,[5,6,7]]

a.extend([5,6,7]) #확장, 리스트 안에 요소가 추가됨  a=a+[5,6,7]
= [1,2,3,4,5,6,7]
```

## .sort:올림차순 정렬

```
# 정렬:정해진 순서(내림/오름차순(0->9, ㄱ->ㅎ)로 데이터를 나열

a=[3,7,5,1]
a.sort()#a에 저장된 자료를 정렬(오름)하고 결과를 a에 저장
print(a)

#아래와 같이 출력하면 안됨
a=[3,7,5,1]
print(a.sort())#None
print(a)

# 내림 차순
a=[3,7,5,1]
a.sort()
a.reverse()
print(a)

a=['b','k','d']
a.sort()
a.reverse()
print(a)
```



## range()

```
range(5) #0~5-1까지 숫자를 생성
print(range(5)) #(0, 5)
print(list(range(5)))#[0, 1, 2, 3, 4]

print(list(range(3,10)))
[3, 4, 5, 6, 7, 8, 9]

print(list(range(3,10,2)))
[3, 5, 7, 9]

print(list(range(10,0,-1)))
[10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
```







## 참고(정렬)

```
print('hi')
print("     hi")
print("hi     ")

print("%10s" % "hi") #앞에 10자리를 확보해서 hi(hi 포함 10자리임)를 채워넣어라
print("hello%10s" % "hi")
print("%-10s" % "hi") #왼쪽 정렬

print("%.4f" % 3.141592) #소수 이하 5쨰 자리에서 반올림해서 4째 자리까지 표현
print("%10.4f" % 3.141592) #10자리를 확보한 다음 출력(우측 맞춤)
print("{0:-<10}".format("hi")) #10자리 확보 후 왼쪽 정렬
print("{0:->10}".format("hi")) #10자리 확보 후 오른쪽 정렬
print("{0:-^10}".format("hi")) #10자리 확보 후 가운데 정렬

print("{0:-^10}".format("hi")) #10자리 -채우고 후 가운데 정렬

print("{0:4f}".format(3.141592))
print("{0:10.4f}".format(3.141592))
```

