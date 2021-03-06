# Day4

## 데이터 최솟값 최댓값 추출

```
num=[5,1,4,3,2]

print(max(num))
print(min(num))
print(sum(num))
print(len(num))
avg=(sum(num)/len(num))
print(avg)
```



## 집합{}(셋)

```
특징: 순서 없음 중복 불허

s1=set([1,2,2,3]) #리스트 자료를 기초로 집합(중복 제외)을 생성
print(s1) #{1, 2, 3}

print(s1[2]) # 에러 발생: 리스트나 튜플은 순서가 있음 ->인덱싱을 통해 접근 가능
# 반면에 set은 순서가 없음->인덱싱 사용불가 =>만약 인덱싱 접근을 하고 싶다면? 리스트 or 튜플로 변경 후 가능
s11=list(s1)
print(s11[2])

s2=set("hihello") #리스트 자료를 기초로 집합(중복 제외)을 생성
print(s2) #{'h', 'l', 'o', 'i', 'e'}

s3=set()
print(s3)#set()

s1=set([1,2,3,4,5,6])
s2=set([4,5,6,7,8,9])
#교집합
print(s1&s2) #{4, 5, 6}
print(s1.intersection(s2))#{4, 5, 6}
#합집합
print(s1|s2) #{1, 2, 3, 4, 5, 6, 7, 8, 9}
print(s1.union(s2))#{1, 2, 3, 4, 5, 6, 7, 8, 9}
#차집합
print(s1-s2) #{1, 2, 3}
print(s1.difference(s2))#{1, 2, 3}
# 데이터 추가
s3=set()
s3.add(3)
print(s3) #{3}

# s3.add(3,4)
# s3.add([3,4]) #에러
# print(s3) #에러
# add 함수는 데이터 1개만 추가 가능

#.update 함수 : 여러개를 추가
s3.update([1,2,3,4,5,6])
print(s3) #{1, 2, 3, 4, 5, 6}

s3.update([1,2,3,15,16])
print((s3)) #{1, 2, 3, 4, 5, 6, 15, 16} 기존에 없는것만 추가됨 집합이니까

s3.remove(2)
print(s3)
```

### set의 응용 .intersection 리스트간 중복 요소찾기 굳

```
b1=['a','b','c','d']
b2=['a','f']

b3=list(set(b1).intersection(b2))
##['a']


중복도 가능
b1=['a','b','c','d']

b2=[['a','g'],['b','c']]
b3=list(set(b1).intersection(i)) for i in b2]

##[['a'],['c','b']]
```



## 메모리의 이해

````
a=[1,2,3]
# 변수=리스트? 리스트(객체)는 메모리에 생성되고, 변수 a는 리스트가 저장된 메모리상의 주소를 가지게 됨

#a 변수가 가리키는 메모리의 주소를 확인
print(id(a)) #메모리의 1826402998784 번지에 [1,2,3]이 저장되어 있다는 의미

a=[1,2,3]
b=a #a가 가지고 있는 값은 엄밀하게 애기하자면 [1,2,3]이 저장되어 있는 "주소값"
print(a)
print(b)

print(id(a)) #1413462170240
print(id(b)) #1413462170240
# a가 가지고 있는 주소값이 b에 복사(저장)


````

### is

```
#is: 두 변수가 가리키는 메모리상의 대상이 동일한 지 확인
a=[1,2,3]
b=a
print(a)
print(b)
a[1]=5
print(a)
print(b)
print(a is b) #a와 b가 가리키는 메모리상의 대상이 동일한가요? #True

a=[1,2]
b=[1,2]
print(id(a)) #1619655637184
print(id(b)) #1619655637248

print(a is b) #False
print(a==b) #True


a=[1,2]
b=a
a[1]=10
print(a)
print(b)

```

### b변수를 만들때, a변수의 값은 가져오면서도 a와 다른 주소를 가리키도록 하는법

```
#1 번째 [:] 이용
a=[1,2,3]
b=a[:]
print(id(a)) #2285697677504
print(id(b)) #2285697677440 다름
print(a)
print(b)

a[1]=10
print(a) #[1, 10, 3]
print(b) #[1, 2, 3] b에는  영향을 주지 않음
```

### copy함수를 이용한 방법

```
패키지(폴더):모듈(파일) 또는 패키지의 묶음
모듈:관련 함수들의 묶음

from 모듈명 import 함수명
모듈로 부터 함수를 가져와
from copy import copy
a=[1,2]
b=copy(a) #b=a[:] 와 같음
print(id(a))
print(id(b))
print(a is b) #False
```

## if 조건문

```
if 조건문:
    코드

x=1
if x==1:
    print('x는 1이다')
    print('x는 홀수이다')
print("출력됩니다")# if문과는 벌개의 문장
pass #코드를 수행하지 않고 넘아감
print("x는 1이다")

x=5
if x>=1:
    print("1이상")
    if x>=5:
        print("5이상")
    if x==10:
        print("10")
print('출력')

money=True
if money:
    print("버스")
    print("택시")
else:
    print("도보")
    
    
or, and, not : 여러 조건을 표현
money=6000
card=True
# if not money>=5000 or card: #or:또는 ,and: 그리고(이고,이면서)
# if card !=False:
if not money<=5000: #만약 오천원보다 적거나 같게 갖고 있지 않다면 택시타라
    print('택시')

else:
    print("버스")


#x in 리스트(튜플,문자열)
print(4 in [1,2,3])
print(4 not in [1,2,3])

print('a' in ('a','b'))

print('h' in "hello")

조건 여러개 경우
if 조건:
    문장
elif 조건:
    문장
elif 조건:
    문장
else:
    문장


money=1000
card=True
if money > 3000:
    print("택시")
elif card: #3000원 이하의 돈을 가지고 있지만, 카드를 가지고 있다면
    print("버스")
else: #돈이 3000원 이상도 없고, card도 없는 경우
    print("도보")
버스

s=60
if s>=60:
    msg="pass"
else:
    msg="fall"
print(msg)
pass

s=60
#퇴근을 5초 당겨주는 궁극의 코드
msg="pass" if s>=60 else "fail"
# 조건문이 참인 경우 if 조건문 else 조건문이 거짓인 경우
#만약에 s가 60이상이면 "pass" 를 msg에 대입하고, 아니면 "fail"를 msg에 대입

print(msg)
pass
 
```

## while,for 반복문

```
i=0
while i<10: #"i 변수 값이 10보다 작다" 라는 조건을 만족하는 동안에, 문장을 반복하세요
    i=i+1
    print(i,"번째 반복 수행")

while True: # 무한 루프(loop)
    i=i+1
    print(i,"번째 반복 수행")
    #조건을 만족했을때 반복 종료
    if i>10:
        break# 반복문을 빠져나가라

propmt="""
1.추가
2.삭제
3.종료
번호입력:"""

# print(propmt)

num=0
while num !=3:
    print(propmt)
    num=int(input())


a=0
while a<10:
    a=a+1
    if a%2==0:continue #continue는 while의 시작위치로 이동
    print(a)

a=0
while a<10:
    a=a+1
    if a%2==0:break #break는 반복문을 벗어나게 됨
    print(a)


while문을 이용해서 1~100 사이의 자연수 중 4의 배수의 합을 출력
a=0
sum=0
while a<=100:
    a=a+1
    if a%4==0:
        sum=sum+a
print(sum)

for문
for 변수 in 리스트(튜플,문자열):
    문장1
    문장2

mylist=[1,2,3]
mylist=['하나','둘','셋']
for i in mylist:
    print(i)

for i in "bigdata":
    print(i)

for i in [(1,2),(3,4),(5,6)]:
    print(i)


for i,j in [(1,2),(3,4),(5,6)]:
    print(i)
    print(j)
    print(("="*50))

for i in range(5):
    print(i)


for i in range(3,10):
    print(i)



for i in range(3,10,2):
    print(i)

a=[5,6,7,8]
for i in range(len(a)):
    print(i)


```

## 이중반복문을 이용한 구구단

```
**for & range 사용 해서 2단부터 9단까지 만들기**
2 4 6 8 12 14 16 18
print(""*50)
for dan in range(2,10): #dan=2 to 9까지 반복
    for i in range(1,10): #i=1 to 9
        a=i*dan
        print(a, end=" ") # end가 가로출력을 도와줌
    print("")# 줄을 바꿔줌
```



## random

```
import random
print(random.random()) #0~1
print(random.randrange(1,7)) #1~6

print(random.randint(1,46)) #1~46 int로 반환
print(random.randrange(1,46)) #1~45

#다른점 뒤에 콤마가 가능
print(random.randrange(1,46,2)) #1~45

2. random.uniform(a, b)

random.uniform 함수는 인자로 들어온 a~b 사이의 실수(float)를 반환합니다.

uniform 함수의 랜덤 범위는 a <= x <= b 입니다.

x = random.random(10, 20)

print(x)    # 10.00000 <= x <= 20.00000

5. random.choice(seq)

choice 함수는 매개변수로 seq 타입을 받습니다. 시퀀스 데이터 타입은 문자열, 튜플, range, 리스트 타입들을 말합니다.

시퀀스 함수는 인자로 받은 리스트, 튜플, 문자열, range 에서 무작위로 하나의 원소를 뽑습니다.

만약, 비어있는 시퀀스 타입의 객체를 인자로 넣는다면 (ex. 리스트가 비어있다면) indexError 의 예외가 발생합니다.

(indexError : 시퀀스의 인덱스가 범위를 벗어났을때 발생하는 에러)



x1 = random.choice('BlockDMask')

print(x1)    # 'BlockDMask' 문자열중 랜덤한 문자를 반환

x2 = random.choice('')

print(x2)    # indexError 발생



출처: https://blockdmask.tistory.com/383 [개발자 지망생]

6. random.sample(seq or set, N)

첫번째 매개 변수로 시퀀스 데이터 타입(튜플, 문자열, range, 리스트) 또는 set 타입을 받을 수 있습니다.

두번째 매개 변수로는 랜덤하게 뽑을 인자의 개수 입니다.

sample 함수는 첫번째 인자로 받은 시퀀스데이터 or set에서 N개의 랜덤하고, unique하고, 순서상관없이 인자를 뽑아서 리스트로 만들어서 반환해줍니다.

sample의 특징 2가지

1. unique라는것이 중요합니다. 겹치지 않는 element를 반환한다는 것인데요

- 'abc' 라는 문자열 있다고 할때 N에 2를 넣을때 겹치지 않게 a,b 혹은 b,c 혹은 c,a를 반환 합니다. (순서 상관없음)

- 'aaa' 라는 문자열이 있다고 할때 N에 2를 넣으면 겹치지 않게 a,a, 혹은 a,a 혹은 a,a 를 반환 합니다. (색으로 구분했습니다, 순서상관없음)

값이 중요한게 아니라 배열의 위치가 겹치지 않게 유니크한 것을 뽑는다는 이야기가 하고 싶었습니다.

다시한번 말씀드리자면, str = 'aaa'가 있을때 str[0],str[1] or str[1],str[2] or str[2],str[0] 을 뽑는다는 것 입니다.



2. 만약에 두번째 매개변수 N이 seq, set의 인자의 개수를 넘어갈때 valueError가 발생합니다. 

- 'abc'라는 문자열을 첫번째 인자로 넣고, 두번째 인자 N를 3을 넘어가는 수인 10을 넣었다고 한다면 valueError가 발생하게 됩니다.



arr1 = 'abc'

print(arr1, 2) # ['a','b'] or ['b','c'] or ['c','a'] 순서는 바뀔수있음

arr2 = 'ccc'

print(arr2, 10) # valueError 발생

arr3 = 'ccc'

print(arr3, 3) #['c','c','c'] 반환



7 . random.shuffle(seq)

셔플 함수는 데이터의 순서를 무작위로 랜덤하게 바꾸어 주는 함수 입니다.

매개변수 x에는 시퀀스 데이터 타입이 들어가게 됩니다. 하지만 내부의 값을 무작위로 바꿔야 하기 때문에 

내부인자를 변경할 수 있는 리스트만 가능하게 됩니다. (문자열, 튜플 및 range(a,b)는 불가능)



random.suffle(리스트) 의 반환은 없고, 인자로 들어온 리스트 내부의 데이터를 무작위로 섞습니다.



arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

print(arr)    # [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]



random.shuffle(arr)    # 셔플셔플셔플 빰빰빰빠밤

print(arr)    # [10, 5, 6, 7, 8, 9, 2, 3, 4, 1]  무작위로 변경됨.







```



과제

```
#과제
# 1. a 리스트에서 중복 숫자를 제거해 보자.

# a = [1, 1, 1, 2, 2, 3, 3, 3, 4, 4, 5]
#
# a=set(a)
# print(a)
#
# # 2. while문을 사용해 1부터 1000까지의 자연수 중 3의 배수이면서 7의 배수인
# # 수의 합을 구해 보자.
#
# b=0
# sum=0
# while b<=1000:
#     b=b+1
#     if b%3==0 and b%7==0:
#         sum=sum+b
# print(sum)
#
# # 3. while문을 사용하여 다음과 같이 별(*)을 표시하는 프로그램을 작성해 보자.
# # 1)
# # *
# # **
# # ***
# # ****
# # *****
#
# star='*'
# num=0
# while num<=4:
#     num +=1
#     print(num*star)
#
# # 2)
# #      *
# #     **
# #    ***
# #   ****
# #  *****
#
# star='*'
# num=0
# while num<=4:
#     num +=1
#     print("{0:>5}".format(num*star))

#3)adv
 #     *
 #    ***
 #   *****
 #  *******
 # *********
#
# star='*'
# num=-1
# while num<=10:
#     num +=2
#     print("{0:^11}".format(num*star))


# 4.for문을 사용해 1부터 100까지의 숫자를 출력해 보자.

# for i in range(1,101):
#     print(i, end=" ")


# 4-1.(adv)
# for문을 사용해 2부터 100까지의 숫자 중에서 소수를(prime number) 출력해 보자.
# *소수란? 1과 자기 자신으로만 나누어 떨어지는 수(ex. 2, 3, 5, 7, 11, 13,...)
#
# for i in range(2,101):
#     for d in range(2,i):
#         if i%d ==0:
#             break
#     else:
#         print(i,end=' ')
# print('')

# 5. A 학급에 총 10명의 학생이 있다. 이 학생들의 중간고사 점수는 다음과 같다.
# score=[70, 60, 55, 75, 95, 90, 80, 80, 85, 100]
# for문을 사용하여 A 학급의 평균 점수를 구해 보자.
# sum=0
# for num in score:
#     sum +=num
# print(str(sum/len(score))+'점')

#6. 로또 당첨 번호 제작(adv)
# *주의:중복된 수 나오면 안됨
# 이번 주 로또 당첨 번호 :  3 7 13 22 25 29

# import random
# num=random.sample(range(1,46),6)
# print("이번 주 로또 당첨 번호 :",num)

#출제자 의도
import random
b=[]
for i in range(6):
    b.append(random.randint(1,46))
    if len(set([]))==6:
        break




#간단하게 아주 잘함
import random
answer=set()
while len(answer)<6:
    num=random.randrange(1,46)
    answer.add(num)
print(answer)


# 7. 자판기(pro, 커피 한 잔에 300원이라 가정, 초기 커피는 10개)
# 돈을 넣어 주세요: 500
# 거스름돈 200를 주고 커피를 줍니다.
# 돈을 넣어 주세요: 300
# 커피를 줍니다.
# 돈을 넣어 주세요: 100
# 돈을 다시 돌려주고 커피를 주지 않습니다.
# 남은 커피의 양은 8개입니다.
# 돈을 넣어 주세요: 0
# 종료합니다

# num=10
# while num>=0:
#     num-=1
#     price = input("동전을 넣어주세요:")
#     sum = int(price)
#     if sum==300 :
#         print("커피를 줍니다")
#         print('남은 커피의 양은'+str(num)+'개입니다.')
#     elif sum>300:
#         count=sum-300
#         print("거스름돈"+str(count)+'를 주고 커피를 줍니다')
#         print('남은 커피의 양은'+str(num)+'개입니다.')
#     elif sum <300 and sum>=100:
#         print("돈을 다시 돌려주고 커피를 주지 않습니다")
#         print('남은 커피의 양은' + str(num) + '개입니다.')
#     else:
#         print('종료합니다')
#         break

가장 참고가됬던것 
price = input('가격을 입력하세요:')
num=input('개수를 입력하세요:')
sum=int(price)*int(num)
print('총액은',sum,'원입니다')
```

