# Day 7

## 파이썬 라이브러리:수많은 파이썬 함수

### abs(): 절댓값 출력

```
#abs() 절댓값을 출력
print(abs(3)) #3
print(abs(-3))#3
print(abs(-1.2))#1.2
```

### all():모두 참->True

```
#all함수: 모두 참 -> True

print(all([1,2,3]))  #1,2,3 모두 다 참
print(all([1,2,3,0]))  #1,2,3,0  0이 있으므로 거짓
```

### any():어느 것 하나라도 참->True

```
#any함수 : 어느 하나라도 참 => 참, 모두 거짓 => 거짓

print(any([1,2,3,0])) #ture
print(any([0,""])) #모두 거짓
print(any([]))# 비어있는 리스트는 거짓 =>거짓

```

### chr함수:아스키코드->문자를 출력<-->ord함수

```
# chr함수: 아스키코드 -> 문자를 출력 함수

print(chr(65)) #A

# ord함수: 문자 => 아스키 코드 출력 함수

print(ord('A')) #65
```

### eval():문자열 수식->정수형으로 바꿔서 계산결과를 내줌

```
# eval():문자열로 구성된 수식 -> 입력 ->문자열을 실행한 결과를 리턴(매우 유용할듯)
print("10+20")
print(type("10+20"))# str
print(eval("10+20"))
30
print(eval("10+20*(3+10)"))
270
print(type(eval("10+20"))) # int

print(eval('divmod(5,3)')) #(1,2)

```

### filter():원하는 데이터를 걸러내는 함수

```
filter(): 원하는 데이터를 걸러내는 함수
filter(함수이름, 1번째 인수에 있는 함수에 입력될 반복 반복 가능한 자료형)
filter함수에 리턴값이 True(참)인 값들만 묶어서 돌려준다.

#1. fiilter함수를 사용하지 않는 경우
def pos(a):
    res=[]
    for i in a:
        if i>0:
           res.append(i)
    return res


print(pos([1,3,-5,-7,9]))#[1,3,9]

#2. filter함수
def pos2(a):
    return a>0
# filter를 쓸때는 무조건 Ture or false가 나와야한다
filter(pos2,[1,3,-5,-7,9]) #
print(list(filter(pos2,[1,3,-5,-7,9]))) #[1, 3, 9]


#3.filter + 람다 함수
print(list(filter(lambda a:a>0,[1,3,-5,-7,9]))) #[1, 3, 9]



```

### hex함수 :16진수로 변경

```
#hex함수 :16진수로 변환(거의 안씀)

print(hex(234))
#16wlstn ea=e*16+1=14*16+1+10*1=234

#int함수 : '3' -> 3
print(int('3'))
print(float('3.4'))
print(int('ea',16)) #진수 변환도 가능
```

### enumerate: for문 과 사용되며 인덱스를 같이 데이터와 표현

```
#enumerate :열거형 데이터를 표현하는 함수, for 문과 함께 사용,
#리스트,튜플, 문자열(시퀀스) 데이터 -> 입력 -> 인덱스를 포함하는 enumerate 객체 생성

for idx,i in  enumerate(['aaa','bbb','ccc']):
    print(idx,i)
0 aaa
1 bbb
2 ccc

```

## 컴프리헨션(식을 짮게)

### 리스트 내포(컴프리헨션)

```
#일반적인 리스트 저장 표현
num=[]
for n in range(11):
    num.append(n)
print(num)

# 리스트 내포(컴프리헨션)
print([n for n in range(11)]) # for 왼쪽에 값이 리스트에 요소로 저장됨

print([n*2 for n in range(11)])

#1~10까지 짝수만 저장
evenNum=[]

for i in range(1,11):
    if i%2==0:
        evenNum.append(i)

print(evenNum)
#내포 사용
print([i for i in range(1,11) if i%2==0])


#다중 반복문 컴프리헨션
#리스트
# [(메뉴,후식),...]
# [('쌉밥','사과'),
#  ('쌉밥','아이스크림'),
#  ('쌉밥', '커피'),
#  ('치킨', '사과'),
#  ('치킨', '아이스크림'),
#  ('치킨', '커피'),
#  ('피자', '사과'),
#  ('피자', '아이스크림'),
#  ('피자', '커피')]
#

li=[]
for x in ['쌈밥','치킨','피자']:
    for y in ['사과','아이스크림','커피']:
        li.append(x,y)
print(li)

print([(x,y,z) for x in ['쌈밥','치킨','피자'] for y in ['사과','아이스크림','커피']for z in ['사','아','커']])


#0~9까지 수 중에서 5보다 작으면서 2로 나누어 떨어지는 수를 리스트에 저장하시오[0,2,4]

print([i for i in range(10) if i<5 if i%2==0])


print([ x+y for x in range(10) for y in range(10)])

```

#### 리스트 내포와 동시에 예약어 사용가능

```
#일반적인 구문: [표현식 for 변수명 in 시퀀스]


 words=['Computer','Coke','Bread']

 #리스트 컴프리헨션으로 표현
 #['computer','coke','bread']

 print([a.lower() for a in words])
```



### 셋과 딕셔너리 컴프리헨션

```
# 셋{} 컴프리헨션
print({x+y for x in range(10) for y in range(10)})



# 딕셔너리{} 컴프리헨션{키:값,키:값,...}
print({x+y:"값" for x in range(10) for y in range(10)})

score={'철수':50,'영희':70,'순심':100}
print({name:score for name, score in score.items() if name !='순심'})


score={'철수':50,'영희':70,'순심':100}

참고 몰라도 됨(가독성이 떨어질수 있음
점수가 60점 이상이면 pass, 미만이면 fail

출력={'철수'=fall'영희':pass,'순심'pass'}
print({name:"pass" if score>=60 else "fail" for name, score in score.items()})

```

## 딕셔너리 응용

### .update,setdefailt

```
#update 와 setdefailt
#update는 없으면 키,value 을 추가 하고중복되면 수정해준다
#setdefailt는 빈 키를 추가한다

x={'a':10,"b":20,'c':30}
print(x)#{'a': 10, 'b': 20, 'c': 30}

x['aa']=40
print(x)#{'a': 10, 'b': 20, 'c': 30, 'aa': 40}

x.setdefault('d') #키 d가 추가, 값이 None저장
print(x)#{'a': 10, 'b': 20, 'c': 30, 'aa': 40, 'd': None}

x['a']=100
print(x)#{'a': 100, 'b': 20, 'c': 30, 'aa': 40, 'd': None}
x.update(b=200)
print(x)#{'a': 100, 'b': 200, 'c': 30, 'aa': 40, 'd': None}

x['z']=99
print(x)#{'a': 100, 'b': 200, 'c': 30, 'aa': 40, 'd': None, 'z': 99}

x.update(c=50,s=50,k=80)
print(x)#{'a': 100, 'b': 200, 'c': 50, 'aa': 40, 'd': None, 'z': 99, 's': 50, 'k': 80}


# print(list(zip([1,2],['one','two'])))
# zip함수를 update에 들어 갈수 있다..
x.update(zip(['aa','a'],[999,777]))
print(x)
{'a': 777, 'b': 200, 'c': 50, 'aa': 999, 'd': None, 'z': 99, 's': 50, 'k': 80}
```

### 딕셔너리 삭제(.pop,.del),if문에 응용

```
x={'a':10,'b':20,'c':30,'d':40}
# x.pop()#딕셔너리는 순서가 없기때문에 오류남
x.pop('c')
print(x)#{'a': 10, 'b': 20, 'd': 40}



x={'a':10,'b':20,'c':30,'d':40}

v=x.pop('b')

print(v)

x={'a':10,'b':20,'c':30,'d':40}

v=x.pop('z',0) #키가 없을때는 0을 리턴
print(v)
0

#####pop을 if에 응용
if x.pop('z',0)==0:

else:


####del 삭제법
x={'a':10,'b':20,'c':30,'d':40}
del x['b']
print(x)
{'a': 10, 'c': 30, 'd': 40}

#딕셔너리에 모든것을 삭제
x.clear()
print(x)

```

### 리스트를 이용해 ->dict만들기: fromkey

```
li=['a','b','c'] #키 리스트
d=dict.fromkeys(li)

print(d)#{'a': None, 'b': None, 'c': None}


d2=dict.fromkeys(li,10)
print(d2)#{'a': 10, 'b': 10, 'c': 10}


```

### 참고 #딕셔너리에서 z를 찾았는데 없다면 0을 출력하라

```
#참고 #딕셔너리에서 z를 찾았는데 없다면 0을 출력하라
from collections import defaultdict #collections 모듈에서 defaultdict함수를 가져옴
d2=defaultdict(int)
print(d2['z'])
```

### 딕셔너리 값출력(key,item,value)

```
d3={'a':10, 'b':20}
#키만 출력
for k in d3:
    print(k)
for k in d3.keys():
    print(k)

#값만 출력
for v in d3.values():
    print(v)

#키,값 쌍을 출력
for k,v in d3.items():
    print(k,v)
```

### 리스트->dict 컴프리헨션

```
keys=['a','b','c','d']
dict.fromkeys(keys)

# for key, value in dict.fromkeys(keys): #dict.fromkeys(keys)자체가 딕셔너리이기 때문에 안됨
#     print(keys)

d4={key:value for key, value in dict.fromkeys(keys).items()} #dict.fromkeys(keys)자체가 딕셔너리이기 떄문에 안됨
print(d4)
{'a': None, 'b': None, 'c': None, 'd': None}
```

### 퀴즈

```
#퀴즈
x = {'a': 10, 'b': 20, 'c': 30, 'd': 40}

#newx는 x에  저장된 데이터에서 'b'를 뺸 나머지를 저장

newx={k:v for k,v in x.items() if k!='b'}
print(newx)
{'a': 10, 'c': 30, 'd': 40}


#newx는 x에  저장된 데이터;에서 값이 20인 자료를 뺸 나머지를 저장

newx={k:v for k,v in x.items() if v!=20}
print(newx)
{'a': 10, 'c': 30, 'd': 40}
```

### dict에서의 copy사용

```
# 딕셔너리={키1:값{키a:값a,키b:값b},키2:{키c:값c,키d:값d}}

영화평점={"BTS":{'머큐리':4.5,'매트릭스':4.0},"소녀시대":{'머큐리':3.5,'매트릭스':3.0}}

print(영화평점['BTS']['매트릭스'])

영화평점['BTS']['매트릭스']=5

print(영화평점['BTS']['매트릭스'])


x={'a':0,'b':1}

y=x #실제로는 딕셔너리가 1개 만들어짐
print(x is y) #변수 이름만 다를 뿐 x,y는 같은 객체 #Ture

x['a']=100
print(y)

y=x.copy()#완전히 다른 2개의 딕셔너리가 만들어짐
print(y is x)#false

x['a']=111
print(x)#{'a': 111, 'b': 1}
print(y)#{'a': 100, 'b': 1}

x={'a':{'python':'3.8'},'b':{'python':'2.8'}}

y=x.copy()

y['a']['python']="2.7777"
print(y)#{'a': {'python': '2.7777'}, 'b': {'python': '2.8'}}

print(x)#{'a': {'python': '2.7777'}, 'b': {'python': '2.8'}}

```

### 다중 딕셔너리에서 deepcopy사용

````
#중첩 딕셔너리에서는 copy메서드 대신 copy모듈의 deepcopy 함수를 활용
x={'a':{'python':'3.8'},'b':{'python':'2.8'}}

import copy
y=copy.deepcopy(x)
y['a']['python']="2.7777"
print(y)#{'a': {'python': '2.7777'}, 'b': {'python': '2.8'}}

print(x)#{'a': {'python': '3.8'}, 'b': {'python': '2.8'}}

````

## 과제

```
#1.다음 입사 문제
#1차원의 점들이 주어졌을 때, 그 중 가장 거리가 짮은 것의 쌍을 출력하는 함수를 작성하시오
#(단 점들의 배열은 모도 정렬되어 있다고 가정한다.)
# 예를 들어 S={1,3,4,8,13,17,20}이어 주어 졌다면, 결과값은(3,4)가 될 것이다
S={1,3,4,8,13,17,20}

num_set=[]
value_set=[]

def min_unmset():
    global S
    S=list(S)
    for i in range(len(S)-1):
        num=(S[i],S[i+1])
        num_set.append(num)
        num=S[i+1]-S[i]
        value_set.append(num)
    res=dict(zip(num_set,value_set))
    min_v=min(value_set)
    for key,value in res.items():
        if value==min_v:
            print(key)


min_unmset()

#류경희 씨 답변
s = [1,3,4,8,13,17,20]

def short_pair(n):

    list=[] #list=[2,1,4,5,5,3]

    for i in range(len(n)-1):

        list.append(n[i+1]-n[i])

    for j in range(len(list)):

        if list[j]==min(list):

            return print(n[j],n[j+1])

short_pair(s)





2.회문(palindrome)? 순서를 거꾸로 해서 읽어도 제대로 읽을떄와 같은 단어 or 문장
rotator,sos (nurses run)
문제: 임의의 단어(문장)을 입력받아 회문 여부를 출력=> True or False로 출력

def palind(a):
    if a[:]==a[::-1]:
        print("True")

    else:
        print("False")
palind('nurses run'.replace(" ",""))




#강사님 답변
# 1.단어는 level 같은 홀수에 경우
w=input("단어를 입력하세요:")
isPalindrome=True
w=w.replace(''," ")
for i in range(len(w)//2):  #5글자면 가운데를 중심으로 2번비교 6글자면 3번비교하면 되기 때문에
    if w[i] != w[-1-i]: #왼쪽문자와 오른쪽문자가 다른 경우
        isPalindrome=False
        break
print(isPalindrome)


2.w=input("단어를 입력하세요:")
print(w==w[::-1])

3.w='level'
print(w)
print(''.join(reversed(w)))
print(w==''.join(reversed(w)))


```