# Day 3

## 시퀸스 

```
시퀀스 자료형
#연속적으로 저장
# 리스트, 튜플, 문자열, range,bytes,bytearray 등은 모두 값이 연속적으로 저장되어 있는 시퀀스 자료형


```

### 데이터 존재 유무

```
# 작성 방법: 찾고자하는 값 in 시퀀스 객체

a=[0,10,...90]

a=list(range(0,100,10))

#a에 30이 있는지 확인?

print(30 in a) #ture

print(45 in a) #false

#a에 30이 없는지 확인?

print(30 not in a) #ture
print(45 not in a) #false

print("5가 있나요?",5 in (1,2,3,4,5))
print("5가 있나요?",5 not in (1,2,3,4,5))

print("hello 문자열에 h문자가 있나요?",'h' in 'hello')

print(1 in range(5))# true
```

### 시퀀스 객체 연결(+,*)(range는 불가)

```
# 시퀀스 객체 연결(range는 불가능)

a=[1,2]
b=[3,4]

print(a+b)

# print(range(0,4)+range(4,6)) 에러
# range 객체들을 연결할 수 없으므로, range->list로 변경 다음 연결
print(list(range(0,4))+list(range(4,6)))

print('hi'+'hello')

# 문자열 연결 : +
# 문자열과 숫자를 연결
# print('hi'+100) #에러 발생

# 문자열과 숫자 연결==> 숫자-> 문자(열)로  변경을 먼저....
print('hi'+str(100))
print('hi'+str(100.111))


# 시퀀스 반복(*), 단 range는 *연산자 사용 불가
# 시퀀스객체 *정수 or   역도 가능

print([1,2,3]*5)
print(5*[1,2,3])

print(range(0,5,1)*3) 에러...

print(list(range(0,5,1))*3)
```

### len(시퀀스 객체)

시퀀스 데이터(요소) 개수

```
a=list(range(10,50,10))

print(len(a))

b=(1,2,3,4)
print(len(b))
print(len(range(1,10,2)))
print(len(("hello")))
print(len(("h el'lo")))# 띄어쓰기,기호도 길이에 포함

print(len("안녕하세요"))#len함수는 길이를 구함.
```

#### 참조 (구버전 len)

```
print(len("안녕하세요"))#len함수는 길이를 구함.
# 파이썬 2.7 버전에서는 바이트 수가 나옴 (15)
# 3.xx버전에서는 글자수가 나옴(5)


# 한글이나 한자는 바이트가 다름 so encode를 사용하면 byte수를 알수 있음
s='안녕하세요'
print(len(s.encode('utf-8')))
# utf-8 에서는 한글 한글자가 3byte, 3*5=15바이트

print(s.encode('utf-8'))
b'\xec\x95\x88\xeb\x85\x95\xed\x95\x98\xec\x84\xb8\xec\x9a\x94'
```

### 시퀀스 인덱스,slicing

```
a=[5,6,7,8,9]

print(a[3])
8

a=(5,6,7,8,9)
print(a[3])
8
r=range(1,10,2) #(1,3,5,7,9)
print(r[2])
5

s='hello'
print(s[3])

# del 시퀀스 객체[인덱스]: 튜플, range, 문자열도 삭제 안됨 정수정하고싶은면 list() 써야함
b=[10,20,30,40]

del b[1]
print(b)

h="hello"
# del h[2] 에러 발생 문자열 삭제 안됨
print(h)

#slicing: 시퀀스 객체[시작인덱스:끝인덱스]

a=[10,20,30,40]

print(a[0:-1])
print(a[0:0])
print(a[0:0])
print(a[1:-1:1])
print(a[3:1:-1])

print(a[0:len(a)]) #a[0:4]=a[0]~a[3]
print(a[:3:2]) #a[0]~a[2], 2칸씩 건너귀기 -> a[0], [2] 참조

#range도 슬라이싱이 된다
r=range(20)

print(r[3:8])
print((r[:15:3]))
print(list(r[:15:3]))

s='hello python'

print(s[:10])
print(s[:10:2])

slice 객체를 이용하여 slicing
print(range(20)[slice(3,9,2)])

print(list(range(5,20)[slice(3,9,2)])) #[8, 10, 12]

a=list(range(10))

print(a)

a[1:4]='a'
print(a)
print("="*50)
a[1:4]=['a','b','c']
print(a)

a=list(range(10))
a[2:7:2]=['x','y','z']

print(a)


# a[2:7:2]=['x','y'] 에러 값부족
# a[2:7:2]=['x','y','z','zz'] 에러  값많음

del a[2:9:2]

print(a)

```

## 딕셔너리

```
#IT(프로그램 개발자) 직무 유형 : SI(시스템통합), SM(시스템유지보수)


#딕셔너리(사전):단어-의미 구조와 유사하게 이름=홍길동 생일= 2020014등과 같은  형식으로 표현
#                            딕셔너리=키(key)=(value)의 쌍으로 표현
#                            딕셔너리={키:값, 키:값,...}
#딕셔너리는 시컨스 객체가 아님. 데이터 참조 방법이 다름
#키는 변하지 않는 값, 값에는 변하는 값을 표현
#상수:문자상수(따옴표로 묶어서), 숫자상수(1,2,3,...)
# [1,10,15,20,30,70] 데이터 사이에 연관 관계가 없음
# 리스트(튜플) 구조로 연관 관계가 있는 데이터를 표현하기가(이해하기도) 어려움
#ex) 게임 캐릭터 정보를 리스트로 표현
# ['홍길동', 10, 100, 20, 200, 50, ...]


{'아이디':'홍길동', '레벨': 10, '체력':100,'mp': 20,'st': 200,'dp': 50}

dic={'아이디':'홍길동', '레벨': 10, '체력':100,'mp': 20,'st': 200,'dp': 50}
print(dic)

#키가 중복되면, 마지막 키와 값만 저장
dic={'아이디':'홍길동', '레벨': 10, '체력':100,'mp': 20,'st': 200,'dp': 50,'아이디':'임꺽정'}
print(dic)
{'아이디': '임꺽정', '레벨': 10, '체력': 100, 'mp': 20, 'st': 200, 'dp': 50}

dic={[10,20]:30} # 키에는 딕셔너리, 리스트 등 자료구조가 올 수 없음
print(dic)#에러


# 빈 딕셔너리
b=list()
print(b)

a={}
print(a)
b=dict()
print(b)


c=dict(아이디='홍길동', 레벨= 10, 체력=100,mp= 20,st= 200,dp= 50,) 올바름

c=dict('아이디'='홍길동', '레벨'= 10, '체력'=100,mp= 20,'st'= 200,'dp'= 50,) #키 값을 상수로 바꿔 준다는 말임 그래서 오류
print(c)

```

### zip이용한 딕셔너리,dict함수이용

```
#zip 은 묶어주는 함수 각각을 대응 시켜줌
#dict(zip([키리스트],[값리스트]))
print(dict(zip(['a','b'],[1,2]))) #zip 객체를 dict로 변환
{'a': 1, 'b': 2}

c=dict(zip(['아이디','레벨','체력','마나','방어력'],['홍길동',10,100,200,50])) #c=dict(아이디='홍길동', 레벨= 10, 체력=100,mp= 20,st= 200,dp= 50,)

print(c)
{'아이디': '홍길동', '레벨': 10, '체력': 100, '마나': 200, '방어력': 50}

dic={'아이디':'홍길동', '레벨':10, '체력':100, '마나':20, '공격력':200, '방어력':50}
c1=dict(아이디='홍길동',레벨=10, 체력=100, 마나=20, 공격력=200, 방어력=50) #올바른 문법
#한글 변수도 가능
#c=dict('아이디'='홍길동',레벨=10, 체력=100, 마나=20, 공격력=200, 방어력=50) 오류
c2=dict(zip(['아이디','레벨','체력','마나','공격력','방어력'],['홍길동',10,100,20,200,50])) #올바른 문법
#dict(zip([키리스트], [값리스트]))

print(dic)
print(c1)
print(c2)
{'아이디': '홍길동', '레벨': 10, '체력': 100, '마나': 20, '공격력': 200, '방어력': 50}
#print(dict(zip(['a','b'],[1,2])))#zip 객체를 dict로 변환

#리스트 내부에 (키, 값) 형식의 튜플로 표현
c3=dict([('아이디','홍길동'),('레벨',10), ('체력',100), ('마나',20), ('공격력',200),('방어력',50)])
print(c3)
{'아이디': '홍길동', '레벨': 10, '체력': 100, '마나': 20, '공격력': 200, '방어력': 50}
#dict([(튜플1),(튜플2),...])

#중괄호로 표현
c4=dict({'아이디':'홍길동','레벨':10, '체력':100, '마나':20, '공격력':200,'방어력':50})
print(c4)
{'아이디': '홍길동', '레벨': 10, '체력': 100, '마나': 20, '공격력': 200, '방어력': 50}

print(dic)
{'아이디': '홍길동', '레벨': 10, '체력': 100, '마나': 20, '공격력': 200, '방어력': 50}



```

### 딕셔너리 데이터 추가/삭제

```
딕셔너리 데이터 추가/삭제
a={'nn':'bear'}

print(a)
#딕셔너리 a에 데이터 추가
a['addr']='seoul'

a[100]=300
#딕셔너리변수명['키이름]=값
print(a)
a['hobby']=['a','b','c']
print(a)
{'nn': 'bear', 'addr': 'seoul', 100: 300, 'hobby': ['a', 'b', 'c']}
# 딕셔너리 데이터 삭제

print(a)#{'nn': 'bear', 'addr': 'seoul', 100: 300, 'hobby': ['a', 'b', 'c']}

# del a[2] 에러,.. 시퀀스가 아니기 떄문에
del a[100] key를 입력해야함
print("삭제 후 : ", a)
#del 딕셔너리변수명[키] => 키와 값을 모두 제거

dic={'아이디':'홍길동', '레벨': 10, '체력':100,'마나': 20,'공격력': 200,'방어력': 50}
dict.clear() #모든 요소삭제
print(dic)
{}


```

### 딕셔너리 key,value값 뽑아내기

```
dic={'아이디':'홍길동', '레벨': 10, '체력':100,'mp': 20,'st': 200,'dp': 50}
print(dic)

print(dic.keys())
dict_keys(['아이디', '레벨', '체력', 'mp', 'st', 'dp'])

print(dic.values())
dict_values(['홍길동', 10, 100, 20, 200, 50])
#key와 값을 추출
print(dic.items())
dict_items([('아이디', '홍길동'), ('레벨', 10), ('체력', 100), ('mp', 20), ('st', 200), ('dp', 50)])
print("="*100)



dic={'아이디':'홍길동', '레벨': 10, '체력':100,'마나': 20,'공격력': 200,'방어력': 50}
print(dic['아이디'])
print(dic.get('홍길동')) # 키의 연결된 값을 추출

# print(dic['민첩']) #keyError: '민첩'없음
print(dic.get('민첩'))#None



```

### 딕셔너리의 인덱션

```
dic={'아이디':'홍길동', '레벨': 10, '체력':100,'mp': 20,'st': 200,'dp': 50}


mykey=dic.keys()
# print(mykey[0]) #mykey=dict_keys(리스트객체)  그래서 오류  리스트로 바꿔줘야함
#리스트로 저장하면 요소하나하나가 메모리에 저장되지만 dict_keys로 하나로 저장됨 위 같은경우는
listmykey=list(mykey)

dic={'아이디':'홍길동', '레벨': 10, '체력':100,'mp': 20,'st': 200,'dp': 50}

dic['저항력']=100

print(dic)
{'아이디': '홍길동', '레벨': 10, '체력': 100, 'mp': 20, 'st': 200, 'dp': 50, '저항력': 100}
print(dic['mp'])
20

# print(dic['민첩성']) 없는 키를 참조하려고 하면 에러 발생
# 딕셔너리에 키가 있는지 확인?

print('아이디' in dic) # not in
True
print('민첩성' in dic)
false

print(len(dic))
7
```





## 과제

```
# 과제
# 1. 리스트 생성 2016년 11월 영화 예매 순위 기준 top3는 다음과 같습니다. 영화 제목을 movie_rank 이름의 리스트에 저장해보세요. (순위 정보는 저장하지 않습니다.)
# 순위   영화
# 1    닥터 스트레인지
# 2    스플릿
# 3    럭키

movie_rank=['닥터 스트레인지','스플릿','럭키']
print(movie_rank)

# 2. movie_rank 리스트에 "배트맨"을 추가하라.
movie_rank=['닥터 스트레인지','스플릿','럭키']

movie_rank.extend(['베트맨'])

print(movie_rank)

#3. movie_rank 리스트에는 아래와 같이 네 개의 영화 제목이 바인딩되어 있다. "슈퍼맨"을 "닥터 스트레인지"와 "스플릿" 사이에 추가하라.

movie_rank = ['닥터 스트레인지', '스플릿', '럭키', '배트맨']

movie_rank.insert(1,'슈퍼맨')

print(movie_rank)

#4. movie_rank 리스트에서 '럭키'를 삭제하라.

movie_rank = ['닥터 스트레인지', '슈퍼맨', '스플릿', '럭키', '배트맨']

# del movie_rank[3]
movie_rank.remove('럭키')

print(movie_rank)

#5. movie_rank 리스트에서 '스플릿' 과 '배트맨'을 를 삭제하라.
movie_rank = ['닥터 스트레인지', '슈퍼맨', '스플릿', '배트맨']

# del movie_rank[2:]
movie_rank.pop()
movie_rank.pop()

print(movie_rank)

# 6. price 변수에는 날짜와 종가 정보가 저장돼 있다. 날짜 정보를 제외하고 가격 정보만을 출력하라. (힌트 : 슬라이싱)

price = ['20180728', 100, 130, 140, 150, 160, 170]

print(price[1:])

# 7.슬라이싱을 사용해서 홀수만 출력하라.

nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

print(nums[::2])

# 8.슬라이싱을 사용해서 리스트의 숫자를 역 방향으로 출력하라.

nums = [1, 2, 3, 4, 5]

print(nums[::-1])

#9.interest 리스트에는 아래의 데이터가 저장되어 있다.=>삼성전자 Naver 출력

interest = ['삼성전자', 'LG전자', 'Naver']

interest.remove(interest[2])

print("\t".join(interest))


# 10. interest 리스트에는 아래의 데이터가 바인딩되어 있다.

interest = ['삼성전자', 'LG전자', 'Naver', 'SK하이닉스', '미래에셋대우']
# interest 리스트를 사용하여 아래와 같이 화면에 출력하라.
# 출력 예시:
# 삼성전자 LG전자 Naver SK하이닉스 미래에셋대우

print('\t'.join(interest))

# 11. interest 리스트에는 아래의 데이터가 바인딩되어 있다.
interest=['삼성전자', 'LG전자', 'Naver', 'SK하이닉스', '미래에셋대우']
# join() 메서드를 사용해서 interest 리스트를 아래와 같이 화면에 출력하라.
# 출력 예시:
# 삼성전자
# LG전자
# Naver
# SK하이닉스
# 미래에셋대우

print("\n".join(interest))

# 12. 리스트에 있는 값을 오름차순으로 정렬하세요.

data = [2, 4, 3, 1, 5, 10, 9]

print(sorted(data))
=====================
data.sort()

print(data)



# 13.홍길동 씨의 주민등록번호는 881120-1068234이다. 홍길동 씨의 주민등록번호를 연월일(YYYYMMDD) 부분과 그 뒤의 숫자 부분으로 나누어 출력해 보자.
# ※ 문자열 슬라이싱 기법을 사용해 보자.

res1='881120-1068234'

print(res1[0:6],res1[7:])


#14 (1,2,3) 튜플에 값 4를 추가하여 (1,2,3,4)를 만들어 출력해 보자.
# ※ 더하기(+)를 사용해 보자.

a=(1,2,3)
a=a+(4,)
print(a)
===================================
a=tuple(list(a)+[4])

print(a)


#15 다음과 같은 딕셔너리 a가 있다.
# 다음과 같은 딕셔너리 a가 있다.
a = dict()
# a
# {}
#
# 다음 중 오류가 발생하는 경우를 고르고, 그 이유를 설명해 보자.
a['name'] = 'python'
# print(a)
a[('a',)] = 'python'
# a[[1]] = 'python' #키 값이 리스트에 들어가 있어서 안됨
# print(a)

a[250] = 'python'

print(a)

# 16 딕셔너리 a에서 'B'에 해당되는 값을 추출해 보자.
a = {'A':90, 'B':80, 'C':70}
# ※ 딕셔너리의 pop 함수를 사용해 보자.

print(a.pop('B'))
```