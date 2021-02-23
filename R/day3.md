# Rday3

## 배열

 행렬의 일반화된 데이터 형식, 차원을 속성으로 갖는 벡터

 벡터(1차원), 행렬(2차원) 모두 배열이라고 할 수 있음
### dim(x) <- value

```
a<-1:24

dim(a)<-c(3,4,2) #3차원, 2개의 면,3행 4열
a
# , , 1
# 
# [,1] [,2] [,3] [,4]
# [1,]    1    4    7   10
# [2,]    2    5    8   11
# [3,]    3    6    9   12
# 
# , , 2
# 
# [,1] [,2] [,3] [,4]
# [1,]   13   16   19   22
# [2,]   14   17   20   23
# [3,]   15   18   21   24
```

### array(data = NA, dim = length(data), dimnames = NULL)

```
ary<-array(1:24, c(3,4,2))
ary[1,3,2]
ary[1,,]
ary
ary[,1,] #1열에 해당하는 것들을 출력
ary[,,2] #2면에 해당하는 것들을 출력

#ary배열의 2번째 면에 있는 1열의 값을 추출
ary[,1,2]
#[1] 13 14 15 #행렬이 아닌 1차원벡터로 출력됬음

#2차원 행렬로 출력
ary[,1,2,drop=FALSE]
```

## 리스트

리스트는 다양한 데이터 타입을 저장할 수 있음
벡터와 행렬은 원소의 데이터 타입이 모두 같아야함

```
lst<-list(0.6,0.9,0.5)
lst
# [[1]]은 원소의 위치(인덱스)를 의미
# [1] 0.6은 원소의 값
# 
# [[2]]
# [1] 0.9
# 
# [[3]]
# [1] 0.5
```

리스트에는 스칼라,벡터(숫자/문자),행렬,함수 저장가능

```
lst<-list(1.5,"apple",c(2,3,4),matrix(1:6,ncol=3),mean)
lst
# [[1]]
# [1] 1.5
# 
# [[2]]
# [1] "apple"
# 
# [[3]]
# [1] 2 3 4
# 
# [[4]]
# [,1] [,2] [,3]
# [1,]    1    3    5
# [2,]    2    4    6
# 
# [[5]]
# function (x, ...) 
#   UseMethod("mean")
# <bytecode: 0x0000021a1dcb3928>
#   <environment: namespace:base>

lst<-list()
lst
lst[[1]]<-1,5
lst[[2]]<-"apple"
lst[[3]]<-c(2,3,4)
lst[[4]]<-matrix(1:6,ncol=3)
lst[[5]]<-mean
lst # 위와 결과 같음
```


### names(x)<-value

```
lst<-list(0.6,0.9,0.5)
lst
names(lst)<-c("n1","n2","n3")
lst
#이름을 주면 [[1]]형식이 $이름으로 변경됨
# $n1
# [1] 0.6
# 
# $n2
# [1] 0.9
# 
# $n3
# [1] 0.5

lst$n1 #리스트에서 이름을 이용한 인덱싱
# [1] 0.6

lst
names(lst) #lst에 담긴 이름들을 알수 있음
# [1] "n1" "n2" "n3"
length(lst) #lst에 길이


```

#### 이름을 사전에 설정하는 방법

```
#직접 설정도 가능
product<-list(id="a001",name="mouse",price=30000)
product

product$name
product[["name"]]
# [1] "mouse"
```

### list 인덱싱,[[]],[] 방법1

```
# lst[[n]] :lst리스트의 n번째 원소가 선택, 원소의 형식을 그대로 가지고 출력.
# lst[n]:lst리스트의 n번째 원소가 선택,원소가 리스트 형식으로 출력

product<-list("a001","mouse",30000)
product

product[[3]] #[1] 30000, 벡터형식 그대로 출력

product[3]
#리스트 형식 그대로 출력
# [[1]]
# [1] 30000
```

두개이상 인덱싱 결과는 리스트

```

product[c(1,2)]

product[c(TRUE,FALSE,TRUE)]

product[-1]
# [[1]]
# [1] "mouse"
# 
# [[2]]
# [1] 30000
```

#### $name: 리스트 인덱싱방법2

```
#두개 이상의 원소 참조,출력 결과는 리스트
product[c("name","price")]
# $name
# [1] "mouse"
# 
# $price
# [1] 30000

product[["name"]]

product[["nn"]] #없는 이름으로 접근하면 null
# NULL
# product[[4]]#첨자의 허용범위가 벗어남 에러 발생


lst<-list(one=1,two=2,three=list(a=3.1, b=3.2))
lst

lst[["three"]]
lst$three
# $a
# [1] 3.1
# 
# $b
# [1] 3.2

lst$three$a
lst[["three"]][["a"]]#벡터
# [1] 3.1

lst[["three"]]["a"]#리스트
# $a
# [1] 3.1
```

## 리스트 요소값 변경

```
#리스트 조작:[[]],$기호 사용하여 요소 접근
product<-list(id="a001",name='mouse',price=30000)

#리스트 요소값 변경
product$price<-50000
product[["price"]]<-40000
product[[3]]<-50000
```

**값을 1개 할당 할때는[[]],[]모두 가능**

```
product[3]<-40000
prodcut["price"]<-40000
product
```

**하나의 원소에 여러 개의 값을 할당할때는 [[]],[]는 다름**

```
product<-list(id="a001",name='mouse',price=30000)
# [[]]는 할당 데이터가 벡터 형식
# []는 할당하고자 하는 값을 리스트 형식으로 변환해야 함

product[[3]]<-c(40000,50000)
product

#에러 발생
product[[3]]<-c(20000,30000)
product

#요건 가능
product[3]<-list(c(20000,30000))
product
# [1] "a001"
# 
# $name
# [1] "mouse"
# 
# $price
# [1] 20000 30000

```

**두 개 이상의 원소 값들을 동시 변경할때는 []를 사용**

```
product[1:3]<-list("a02","monitor",99999)
product
# $id
# [1] "a02"
# 
# $name
# [1] "monitor"
# 
# $price
# [1] 99999
```

### 리스트에 요소값 추가(추가 할때는 []<-c()가능

리스트형식아니여도됨

$name<-c(value) 역시 가능

```
#리스트에 데이터를 추가하는 여러가지 방법
product[[4]]<-c("domestic","export")
product
# $id
# [1] "a02"
# 
# $name
# [1] "monitor"
# 
# $price
# [1] 99999
# 
# [[4]]
# [1] "domestic" "export"

product$madein<-c("korea","india")
product
# $id
# [1] "a02"
# 
# $name
# [1] "monitor"
# 
# $price
# [1] 99999
# 
# [[4]]
# [1] "domestic" "export"  
# 
# $madein
# [1] "korea" "india"

product[["madein2"]]<-c("usa","china")
product
# $id
# [1] "a02"
# 
# $name
# [1] "monitor"
# 
# $price
# [1] 99999
# 
# [[4]]
# [1] "domestic" "export"  
# 
# $madein
# [1] "korea" "india"
# 
# $madein2
# [1] "usa"   "china"

product["madein3"]<-list(c("usa2","china2"))
product
```

### 리스트 여러개 원소를 한번에 추가

```
#리스트에 여러개 원소를 한번에 추가(리스트 구조로 저장,타입이 모두 같은 경우에는 벡터 구조도 가능)

당연한 애기인게 일반 벡터는 요소에 타입이 같아야만하기 때문에
[]<-c() 이때 괄호 안에는 숫자와 문자 원소가 같이 있으면 문자로 통일되어 추가

product[8:10]<-list(0.1,0.2,"0.3")
product
# 각각 원하는대로 잘 저장됨
# [[8]]
# [1] 0.1
# 
# [[9]]
# [1] 0.2
# 
# [[10]]
# [1] "0.3"
product[8:10]<-list(0.1,0.2,0.3)
product
# [[8]]
# [1] 0.1
# 
# [[9]]
# [1] 0.2
# 
# [[10]]
# [1] 0.3
product[11:13]<-c(0.1,0.2,"0.3") #
product
# 전부 문자로 적용됨
# [[11]]
# [1] "0.1"
# 
# [[12]]
# [1] "0.2"
# 
# [[13]]
# [1] "0.3"


n<-c("one","two","three")
v<-c(100,200,300)
mylist<-list()
mylist[n]<-v
mylist
# $one
# [1] 100
# 
# $two
# [1] 200
# 
# $three
# [1] 300


```

### 리스트 원소 제거

```
#리스트에서 원소 제거는 Null을 할당
mylist[["two"]]<-NULL
mylist

# $one
# [1] 100
# 
# $three
# [1] 300


mylist[c("one","three")]<-NULL
mylist
# named list() #빈리스트 출력

```

### 리스트 조건에 따른 원소제거(불인 참조)

```
n<-c("one","two","three")
v<-c(100,200,300)
mylist<-list()
mylist[n]<-v
mylist
# $one
# [1] 100
# 
# $two
# [1] 200
# 
# $three
# [1] 300

#조건에 따른 원소 제거(불인참조)
mylist<200
# one   two three 
# TRUE FALSE FALSE 

mylist[mylist<200]<-NULL
mylist
# $two
# [1] 200
# 
# $three
# [1] 300
```

## 리스트의 결합(벡터와 같음)

```
#리스트 결합(벡터와 같음)
w1<-list("a","b","c")
w2<-list("d","e","f")

c(w1,w2)
# [1] "a"
# 
# [[2]]
# [1] "b"
# 
# [[3]]
# [1] "c"
# 
# [[4]]
# [1] "d"
# 
# [[5]]
# [1] "e"
# 
# [[6]]
# [1] "f"
```

## unlist():리스트->벡터 (리스트 연산시)

```
unlist(mydata)
# [1] 1.5 2.0 3.5 4.5
mean(unlist(mydata)) #리스트로는 연산함수 사용불가
# [1] 2.875
min(unlist(mydata))
max(unlist(mydata))
```

## class():자료타입 확인

```
#자료 타입을 확인
class(product[[3]]) #숫자 벡터
# [1] "numeric"
class(product[3])#리스트
# [1] "list"
```

##  데이터 프레임생성

#데이터 프레임:행과 열로 구성,2차원 구조(행렬과 같음)
#행렬은 모든 데이터 타입이 일치
#데이터 프레임은 서로 다른 데이터 타입을 가질 수 있음(리스트와 같음)
#데이터 프레임은(2차원구조),리스트는(1차원 구조)

#리스트랑 다르게 데이터 프레임 상태로 연산이 가능함

#데이터프레임은 **동일한 길이**의 벡터로 이루어진 리스트를 구성요소로 하는 2차원데이터 

### data.frame():벡터로부터 데이터 프레임생성

```
v1<-c("a1","a2","a3")
v2<-c(10,20,30)
# v3<-c("x","y")
data.frame(v1,v2)
#   v1 v2
# 1 a1 10
# 2 a2 20
# 3 a3 30

data.frame(v1,v2,v3) #v3는 2개밖에 없어서 동일한 길이의 벡터가 아니라서
# Error in data.frame(v1, v2, v3) : 
#   arguments imply differing number of rows: 3, 2

v3<-c("x","y","z")

df<-data.frame(v1,v2,v3): 이러면 정상적으로 출력

#   v1 v2 v3 (피처들)
# 1 a1 10  x
# 2 a2 20  y
# 3 a3 30  z
# (행이름):1,2,3
str(df)
# 'data.frame':	3 obs. of  3 variables:
# $ v1: chr  "a1" "a2" "a3"
# $ v2: num  10 20 30
# $ v3: chr  "x" "y" "z"

# #observation->obs
# #3 variables(features)
# 
#    x1 x2 ... x10000
# 0  0  20 ...   255
#    0  20 ...   255
#    0  20 ...   255
#    ...
# 99 0  20 ...   255 
```

### 행 이름으로 특정 벡터를 지정

```
data.frame(row.names = v1,v2,v3)
#    v2 v3
# a1 10  x
# a2 20  y
# a3 30  z

#프레임 함수 안에서 직접 열 이름을 지정
p<-data.frame(id=v1, name=v2, price=v3)

#   id name price
# 1 a1   10     x
# 2 a2   20     y
# 3 a3   30     z
```

### stringAsFactors :데이터프레임 생성할때 데이터타입을 팩터로 지정 # 데이터 프레임함수 안에서 사용

**stringAsFactors=FALSE #팩터로 문자열을 읽지 않겠다. 즉 문자열로 읽겠다**
**stringAsFactors=TRUE #팩터로 문자열을 읽겠다. 즉 문자열을 팩터로 읽겠다**

```
# (데이터를 Factor형태로서 string(문자열)을 읽겠습니까?)

p<-data.frame(id=v1, name=v2, price=v3, stringsAsFactors = TRUE)
str(p)
# 원래 chr이던 id랑 price가 카테고리인 팩터가 됨
# 'data.frame':	3 obs. of  3 variables:
# $ id   : Factor w/ 3 levels "a1","a2","a3": 1 2 3
# $ name : num  10 20 30
# $ price: Factor w/ 3 levels "x","y","z": 1 2 3


# 문자열 총 10개,stringAsFactors=FALSE
# 2개 팩터(chr -> factor변환), 8개 문자백터
```

### as.data.frame():행렬,리스트로부터 데이터 프레임생성

```
mat<-matrix(c(1,2,3,4,5,6), ncol=2)
mat
#      [,1] [,2]
# [1,]    1    4
# [2,]    2    5
# [3,]    3    6
#행렬 ->데이터프레임

num<-as.data.frame(mat)
#   V1 V2
# 1  1  4
# 2  2  5
# 3  3  6
```

**데이터 프레임은 리스트와 행렬의 특징을 둘다 갖기 때문에**

```
colnames(num) #열 이름
# [1] "V1" "V2"

colnames(num)<-c("d1","d2") #행렬의 열 변경방식을 그대로 적용가능
num
#   d1 d2
# 1  1  4
# 2  2  5
# 3  3  6
```

#### 리스트->데이터프레임

```
v1<-c("a1","a2","a3")
v2<-c(10,20,30)
v3<-c("x","y","z")

lst<-list(v1,v2,v3)
# [[1]]
# [1] "a1" "a2" "a3"
# 
# [[2]]
# [1] 10 20 30
# 
# [[3]]
# [1] "x" "y" "z"

p<-as.data.frame(lst) #요소값으로 열이름을 만들어버림
#   c..a1....a2....a3.. c.10..20..30. c..x....y....z..
# 1                  a1            10                x
# 2                  a2            20                y
# 3                  a3            30                z

colnames(p)<-c("id","name","price")
p
#   id name price
# 1 a1   10     x
# 2 a2   20     y
# 3 a3   30     z

```

### data프레임에서의 lenght(): 열의 개수

**행렬에서는 전체 원소개수가 나오지만 데이터 프레임에서는 열에 갯수만 나옴**

```
length함수 :행렬에서 전체 원소 개수,데이터프레임에서는 열의 개수가 나옴

length(p)#데이터 프레임에서는 열의개수
# [1] 3
ncol(p)#열의 개수
# [1] 3
nrow(p) #행의 개수
# [1] 3
```

## datasets패키지

```
#datasets패키지:r설치시 기본적으로 내장되어 있는 데이터셋

# https://stat.ethz.ch/R-manual/R-devel/library/datasets/html/00Index.html

str(state.abb) #50개주
str(state.name)
str(state.region)
str(state.area) #평방면적

us.state<-data.frame(state.abb,state.name,state.region,state.area)

us.state
```

## 데이터 프레임의 인덱싱

**리스트 방식과 행열에서의 인덱싱 방식을 둘다 사용가능**

**[[]],[],$,[ , , ,]**

```
#state.name 열 출력
#[[]] or []사용하여 열 추출
#[[]]:열 하나를 벡터 or 팩터로 출력
#[]:데이터 프레임이 추출, 하나 또는 여러개의 열을 추추
us.state[["state.name"]] :자료구조가 문자벡터
us.state["state.name"] :자료구조가 데이터 프레임
```

```
#행렬 인덱싱 사용 가능
us.state[,2] #1차원 벡터로 나옴
us.state[,2,drop=FALSE] #행렬에서는 drop=FALSE 적용시,출력결과 타입 행렬
#데이터 프레임에서는 타입이 데이터프레임

us.state[,c(2,4)] #행렬과 같이 두개 이상시 데이터프레임으로 자동으로 나옴

us.state$state.name #벡터로 나옴
us.state[,'state.name']

us.state[c("state.name", "state.area")] #리스트 인덱싱
us.state[,c("state.name", "state.area")] #행렬 인덱싱
#둘다 같은 결과가 나옴
```

## 데이터 프레임에서 행추가(rbind(추가할곳,추가할것))

```
product<-data.frame(id,name,price)
product
str(product)

#rbind():데이터 프레임에 행 추가

product<-rbind(product,c("a4","40","k"))
product
#   id name price
# 1 a1    x    10
# 2 a2    y    20
# 3 a3    z    30
# 4 a4   40     k
```

### 여러행 추가:데이터 프레임을 만들어서 추가

```
#여러 행 추가 #추가할 데이터프레임을 만들어서 추가

new.rows<-data.frame(id=c("a5","a6"),
           name=c("a","b"),
           price=c(50,60))
new.rows
#   id name price
# 1 a5    a    50
# 2 a6    b    60

product<-rbind(product,new.rows)
product

만약

```

### 문자값을 숫자값으로 바꾸기:as.numeric()

```
만약
new.rows<-data.frame(id=c("a5","a6"),
           name=c("a","b"),
           price=c('50','60'))
new.rows
#   id name price
# 1 a5    a    50
# 2 a6    b    60
이라면 price에 원소는 타입이 chr이게 됨 이걸 바꿀때

product<-rbind(product,new.rows)
product

##문자 값을 숫자값으로 바꾸기
product$price<-as.numeric(product$price)
```



## 데이터 삭제

```
product<-product[-4,] #잘못된 데이터를 삭제
product
product<-rbind(product,c("a4","k",40))
product
#   id name price
# 1 a1    x    10
# 2 a2    y    20
# 3 a3    z    30
# 4 a4    k    40

```

## 과제

```
# 1. 다음 리스틍서 A를 a로 변경하시오
c<-list(c(3,5,7),c("A","B","C"))
str(c[2])

c[[2]][1]<-"a"


# 2. 다음 리스트는 중간고사 및 기말고사 점수이다. 
# 중간고사 평균, 기말고사 평균, 전체 평균을 계산하시오

score<-list(math=list(95,90),eng=list(80,90),kor=list(85,80))
score
(score[[1]][[1]]+score[[2]][[1]]+score[[3]][[1]])/3
(score[[1]][[2]]+score[[2]][[2]]+score[[3]][[2]])/3

unlist(score)

score


# 전체평균
mean(unlist(score))

# 3. 다음은 1월~12월까지 월평균 기온이다.
temp<-list(-2.4, 0.4, 5.7, 12.5, 17.8, 22.2, 24.9, 25.7, 21.2, 14.8, 7.2, 0.4)
# 1) 월 이름(Jan~Dec)을 지정한 리스트를 만드시오.
names(temp)<-month.abb
temp
# 2) 0도 미만인 월을 추출하시오
names(temp[temp<0])
# 3) 연평균 기온보다 작은 월을 추출하시오.
mean(unlist(temp))
names(temp[temp<mean(unlist(temp))])
# 4) 연평균 기온보다 큰 월을 리스트에서 제거하시오.
temp[temp>mean(unlist(temp))]<-NULL
temp


# 4. 리스트 list(a=1, b=2)와 벡터 pi를 결합하여 새로운 리스트를 생성하고,
# 생성한 리스트에서 pi를 추출하시오.

lst<-list(a=1, b=2)

lst['pi']<-pi
lst

lst[3]
lst['pi']

# 5. 1. 행렬 X가 다음과 같이 정의되도록 R로 작성하라.
#    c1 c2 c3
# r1  1  4  7
# r2  2  5  8
# r3  3  6  9
# ① matrix() 함수를 이용하라.
v<-1:9
rname<-c('r1','r2','r3')
cname<-c('c1','c2','c3')
mat<-matrix(v ,3,dimnames = list(rname,cname))
mat


# ② cbind()와 rbind() 함수를 이용하라.
r1<-c(1,4,7)
r2<-c(2,5,8)
r3<-c(3,6,9)
rcm<-rbind(r1,r2,r3)
colnames(rcm)<-cname
rcm

c1<-c(1:3)
c2<-c(4:6)
c3<-c(7:9)

ccm<-cbind(c1,c2,c3)
rownames(ccm)<-rname
ccm


# ③ dim() 함수를 이용하라.
v<-1:9
dim(v)<-c(3,3)
dimnames(v)<-list(rname,cname)
v

# 6. 앞 문제의 행렬 X에 대해 다음을 알아내는 방법을 R로 답하라.
# ① 행과 열의 개수.    
nrow(mat)
ncol(mat)

#② 행벡터 및 열벡터의 이름.
rownames(mat)
colnames(mat)

# ③ 원소의 개수
length(mat)

# 7. 다음 두 행렬 A, B에 대해 물음에 답하라.
A<-matrix(c(1,4,1,0,1,2), 2, byrow=T)    
B<-rbind(c(1,0,1),c(-1,1,-1))
A
B
# ① A+B, A-B, B*A, B/A
A+B
A-B
B*A
B/A
# ② 행렬 A의 2행 벡터를 c(1,2,1)로 치환하라.
A[2,]<-c(1,2,1)
A 

# ③ 행렬 B의 1열 벡터와 2열 벡터를 교환하라.
r<-B[,1]
r
B[,1]<-B[,2]
B[,2]<-r
B

# ④ 행렬 A의 2행을 제거하라.
A<-A[-2,]
A

# ⑤ 행렬 B에서 1보다 작은 원소를 0으로 치환하라.
B[B<1]<-0
B

# 8. 행렬과 배열(array)의 차이점을 말하고, 3×2×3 배열의 예를 하나 만들어보아라.

ary<-array(1:18,c(3,2,3))

ary

#행렬은 벡터값들이 행과 열이라는 구조를 갖는 것..(2차원)
#배열은 행렬을 여러장 쌓아 올린것입니다(다차원)

# 9. 다음과 같은 번호(ID), 성명(name), 성적(score)를 성분으로 하는 리스트가 있다. 물음에 답하라.
L=list(ID=c(1,2,3), 
       name=c('Kim', 'Lee', 'Park'),
       score=c(80, 95, 75))
L
# ① length(L)은 얼마이며, 이것은 무엇을 의미하는가?
length(L) #3
#성분(id,name,score)의 개수

# ② 이름 성적 75을 80으로 수정하라.
L[['score']][3]<-80
L
# ③ L$name=='Park'의 결과를 쓰고, 무엇을 의미하는지 설명하라.
L$name=="Park"
# [1] FALSE FALSE  TRUE
# L이라는 list안에 name에 요소에 "prak"가 인가요?

# ④ L$score[L$name=='Park']의 결과를 쓰고, 문장이 무엇을 의미하는지 설명하라.
L$score[L$name=='Park']
#80
# L리스트의 name에서 Park이 있나요?->TURE->TURE의 인덱스번호->3
# ->L$score[3]=>80


# ⑤ 1번 학생의 이름과 성적을 알아내는 문장을 만들어 보아라.
c(L$name[1],L$score[1])


# 10. 다음의 표를 데이터프레임으로 작성해 보아라.
# 
# id	age	sex 	height	weight
# 1	  21	'남'	175	    80
# 2	  22	'여'	165	    55
# 3	  31	'여'	155	    45
# 4	  40	'여'	160	    50

id<-c(1,2,3,4)
age<-c(21,22,31,41)
sex<-c('남','여','여','여')
height<-c(175,165,155,160)
weight<-c(80,55,45,50)
df<-data.frame(id,age,sex,height,weight)

# 11. 다음 데이터를(자료구조는 자유선택) 저장한 후, 유클리디안 거리를 활용하여 
# 손흥민과 가장 유사하게 평점을 준(거리가 가까운) 사람의 이름과 거리를 
# 출력하시오.
# 
# critics={
#   'BTS':{'밀정':5, '경이로운소문':4, '국제시장':1.5},
#   '손흥민':{'밀정':4,'경이로운소문':5, '국제시장':2},
#   '레드벨벳':{'밀정':2.5, '경이로운소문':2, '국제시장':1},
#   '트와이스':{'밀정':3.5, '경이로운소문':4, '국제시장':5}
rname<-c("밀정","경이소문","국제시장")
cname<-c('bts','son','vel','twi')
v<-c(5,4,1.5,4,5,2,2.5,2,1,3.5,4,5)
comment<-matrix(v,3,4 ,dimnames = list(rname,cname))
dfcomment<-as.data.frame(comment)


sqrt(sum((dfcomment['son']-dfcomment['bts'])^2))
# 1.5
sqrt(sum((dfcomment['son']-dfcomment['vel'])^2))
# 3.5
sqrt(sum((dfcomment['son']-dfcomment['twi'])^2))
# 3.807887

# bts가 가장 유사
```

