# Rday2

## over index

```
p<-c(2,3,5,7,11,13,17,19)

p[2]<-13
p[c(6,8)]<-c(100,200)
p

p[15]<-99 #[1]   2  13   5   7  11 100  17 200  NA  NA  NA  NA  NA  NA  99
p # 없는 인덱스에 값을 넣으면 그 값 사이는 NA이 됩니다.

```

## 불인 인덱싱

````
p<-c(2,3,5,7,11,13,17,19)

p[p<10 #p<10보다 작은 값들만 참조 출력
  
p
p[c(TRUE,TRUE,FALSE)] 
# 2(TURE)13(TURE)5(FALSE)7(TURE)11(TURE)100(FALSE)17(TURE) 200(TURE)NA  NA  NA  NA  NA  NA  99(FALSE)
#TRUE만 출력되서 [1]   2  13   7  11  17 200  NA  NA  NA  NA 출력 NA는 불인이 적용안되기 때문에 그냥 출력
````

## which():true위치 인덱스 추출 함수

```
data<-c(100:111) #12  데이터(1월~12월까지)
data
which(data>105) #[1]  7  8  9 10 11 요건에 맞는 인덱스번호가 출력

month.abb[which(data>105)] #[1] "Jul" "Aug" "Sep" "Oct" "Nov"
month.name[which(data>105)]
```

### which.max(),min()

```
data<-c(100:111)

which.min(data) #1 data에 저장된 자료중 최솟값의 인덱스
which.max(data) #12 data에 저장된 자료중 최댓값의 인덱스
```

## names():벡터에 이름을 정의

```
#요일별 교통사고 사망자수 데이터

traffic.death<-c(100,90,80,70,120,150,200) #월~일 사망자수

#토요일 사망자수
tracffic.death[6]

#names:벡터에 이름을 정의하는 함수
names(traffic.death)<-c("mon","tue","wed","thu","fri","sat","sun")

traffic.death
# mon tue wed thu fri sat sun 
# 100  90  80  70 120 150 200 

names(traffic.death)#[1] "mon" "tue" "wed" "thu" "fri" "sat" "sun"

traffic.death["sat"]
#sat 
#150 

traffic.death[c("sat","wed")]
```

### 조건에 맞는 name을 인덱스

```
traffic.death[c("sat","wed")]

#사망자수가 100명 이상인 요일만 출력

names(traffic.death[traffic.death>=100]) #[1] "fri" "sat" "sun"
```

## factor():카테고리 구분이 목적인 범주형데이터

```
review<-c("good","good","bad","indifferent","bad","good")
#문자벡터
review #[1] "good"  "good"  "bad" "indifferent" "bad"  "good"

review.factor<-factor(review)

review.factor 
#[1] good   good    bad   indifferent bad   good   
#Levels: bad good indifferent


str(review.factor)
#Factor w/ 3 levels bad good indifferent: 2 2 1 3 1 2


str(review)
#chr [1:6] "good" "good" "bad" "indifferent" "bad" "good"
```

### 사전카테고리 설정:벡터안에 있는 요소값만 level로 지정되기 때문에 

````
#요일을 factor로 삼고 싶을때
everyday<-c("mon","mon","fri","tue","tue")
#everyday.factor<-factor(everyday) #이렇게 하면 요일이 전체가 level로 안잡히기 때문에
#everyday.factor
#[1] mon mon fri tue tue
#Levels: fri mon tue #알파벳 순서로 레벨이 잡힘

everyday.factor<-factor(everyday, levels=c("mon","tue","wed","thu","fri","sat","sun"))
everyday.factor
#[1] mon mon fri tue tue
#Levels: mon tue wed thu fri sat sun #레벨로 따로 잡으면 알파벳순서가 아닌 있는 그대로
````

### 참고as.numeric(review.factor):팩터형->숫자벡터로변환

```
as.numeric(review.factor) #팩터형 ->숫자벡터로 변환 #[1] 2 2 1 3 1 2
```

## levels():레벨의 이름을 지어주기

```

review<-c("good","good","bad","indifferent","bad","good")

levels(review.factor)<-c("B","G","I")

review.factor
#[1] G G B I B G
#Levels: B G I

```

### nlevels():level의 길이

```
#review.factor의 길이
nlevels(review.factor)#3

length(levels(review.factor)) #3
```

## factor(x,levels= ,ordered=TURE): 서열 팩터

```
#서열 팩터:순서가 있는 범주형 데이터,부등호 기호로 서열 표시

eval<-c("Medium","Low","High","Medium","High")
eval.factor<-factor(eval)
eval.factor #그냥 팩터
#[1] Medium Low    High   Medium High  
#Levels: High Low Medium

eval.ordered<-factor(eval, levels=c("Low","Medium","High"),ordered = TRUE)

eval.ordered #서열팩터
#[1] Medium Low    High   Medium High  
#Levels: Low < Medium < High 
```

## table():각 레벨별 빈도

```
table(eval.factor)#알파벳순서
#  High    Low Medium 
#    2      1      2

table(eval.ordered) #정해진 서열대로
#Low Medium   High 
#1      2      2 
```

## 숫자벡터->팩터로 변환 labels=

```
#숫자벡터->팩터로 변환
#남:1,여:2

sex<-c(2,1,2,2,1,0)

sex.factor<-factor(sex,levels=c(1,2), labels=c("Male","Female"))

sex.factor

#[1] Female Male   Female Female Male  <NA>
#Levels: Male Female

# 3. 주사위를 7번 던져서 나온 3,2,5,1,5,6,5의 값을 
# 1)여섯 개의 레벨을 갖는 팩터로 저장하시오.
num<-c(3,2,5,1,5,6,5)
num
num.factor<-factor(num,levels = c(1,2,3,4,5,6))
num.factor
# 2)각 레벨에 one, two, ... six로 이름 부여하시오.
num.factor<-factor(num,levels = c(1,2,3,4,5,6), labels =c("one","two","three",'four',"five","six"))

# 3)레벨별 발생 빈도를 출력하시오.
table(num.factor)
```

## 행렬

#행렬:2차원 벡터,벡터에 차원을 부여(dim함수)
#행렬은 벡터로 구성, 벡터는 타입이 모두 동일
#matrix함수로도 행렬생성

### dim():행렬생성

```
dim(x)
dim(x) <- value


v<-1:12
dim(v)<-c(3,4)
v
#     [,1] [,2] [,3] [,4]
#[1,]    1    4    7   10
#[2,]    2    5    8   11
#[3,]    3    6    9   12

dim(v) #위와 같습니다

```

### matrix():matrix(data = NA, nrow = 1, ncol = 1, byrow = FALSE,  dimnames = NULL)

```
v<-1:12


matrix(data=v ,nrow=3,ncol=4)
#      [,1] [,2] [,3] [,4]
# [1,]    1    4    7   10
# [2,]    2    5    8   11
# [3,]    3    6    9   12

#기본적으로 열방향으로 칸이 채워짐

#행방향으로 칸을 넣고 싶으면
matrix(data=v ,nrow=3,ncol=4, byrow = TRUE)
#      [,1] [,2] [,3] [,4]
# [1,]    1    2    3    4
# [2,]    5    6    7    8
# [3,]    9   10   11   12

matrix(data=v ,3, 4, byrow = TRUE) #안써도 자동으로 됨



matrix(0,3,4) #데이터모두 0으로
#      [,1] [,2] [,3] [,4]
# [1,]    0    0    0    0
# [2,]    0    0    0    0
# [3,]    0    0    0    0
atrix(NA,3,4)

mat<-matrix(v,ncol=4) #v벡터가 12개이니까 열를 4로 지정하면 자동으로 행=3으로 구성함 
#행렬은 2차원 벡터
```

### 행렬 여러함수적용

```
v<-1:12
mat<-matrix(v,ncol=4) 

str(mat) #int [1:3, 1:4] 1 2 3 4 5 6 7 8 9 10 ... 
dim(mat) #3 4 #행열값
dim(mat)[1]#3
dim(mat)[2]#4
nrow(mat)#3
ncol(mat)#4
length(mat) #12
```

### 행과 열에 이름부여하기

```
#행과 열에 이름 부여하기

rnames<-c("r1","r2","r3")
cnames<-c("c1","c2","C3","c4")

matrix(v ,3, 4, byrow = TRUE, dimnames = list(rnames,cnames))

#    c1 c2 C3 c4
# r1  1  2  3  4
# r2  5  6  7  8
# r3  9 10 11 12
```

### r,cbind(a1,b1):두벡터의 결합

```
#두 벡터를 결합하여 행렬을 생성
v1<-1:5
v2<-6:10

rbind(v1,v2)
#     [,1] [,2] [,3] [,4] [,5]
# v1    1    2    3    4    5
# v2    6    7    8    9   10

cbind(v1,v2)
#       v1 v2
# [1,]  1  6
# [2,]  2  7
# [3,]  3  8
# [4,]  4  9
# [5,]  5 10
```

### r,cbind(a1,b1):벡터와 행렬의 결합

```
1:3
4:6

cbind(1:3,4:6 ,matrix(7:12,3,2))
#      [,1] [,2] [,3] [,4]
# [1,]    1    4    7   10
# [2,]    2    5    8   11
# [3,]    3    6    9   12
```

### r,cbind(a1,b1):행렬과 행렬의 결합

```
#행렬과 행렬과 결합하여 새로운 행렬 생성

matrix(1:6,2,3)
matrix(7:12,2,3)

rbind(matrix(1:6,2,3),matrix(7:12,2,3))
#      [,1] [,2] [,3]
# [1,]    1    3    5
# [2,]    2    4    6
# [3,]    7    9   11
# [4,]    8   10   12
```

### 행렬의 인덱싱(1차원)

```
v<-1:12
mat<-matrix(v,3,4)
mat
#      [,1] [,2] [,3] [,4]
# [1,]    1    4    7   10
# [2,]    2    5    8   11
# [3,]    3    6    9   12

mat[1,] #출력 결과: 벡터(1차원)
#[1]  1  4  7 10
mat[,3]
#[1] 7 8 9

```

### 중요)행렬의 인덱싱(2차원)

```
mat[1,,drop=FALSE] #2차원 상태로 추출
#      [,1] [,2] [,3] [,4]
# [1,]    1    4    7   10

mat[,3,drop=FALSE]
#      [,1]
# [1,]    7
# [2,]    8
# [3,]    9

mat[2:3,] #두개의 행을 출력하는거니까 행렬상태로 바로출력
#      [,1] [,2] [,3] [,4]
# [1,]    2    5    8   11
# [2,]    3    6    9   12

mat[1:2,2:3]

mat[c(1,3),]
#      [,1] [,2] [,3] [,4]
# [1,]    1    4    7   10
# [2,]    3    6    9   12

mat[,c(1,4)]
mat[,-c(1,4)]#1,4열 빼고 출력
#      [,1] [,2]
# [1,]    4    7
# [2,]    5    8
# [3,]    6    9
```

### 행열 값 변경

```
#행렬 값 변경
mat[1,3]<-77
mat
#       [,1] [,2] [,3] [,4]
# [1,]    1    4   77   10
# [2,]    2    5    8   11
# [3,]    3    6    9   12

mat[2,]<-c(22,55)
mat
#      [,1] [,2] [,3] [,4]
# [1,]    1    4   77   10
# [2,]   22   55   22   55
# [3,]    3    6    9   12

mat[2:3,3:4]<-c(1,2,3,4)
mat

#      [,1] [,2] [,3] [,4]
# [1,]    1    4   77   10
# [2,]   22   55    1    3
# [3,]    3    6    2    4
```

### 행렬생성 퀴즈

```
#퀴즈(카페에 업로드)
#matrix 생성하시오
#           seoul busan daegu gwangju jeonju
# seoul       0    350   300    300     200
# busan      350    0    50     200     190
# daegu      300    50    0     180     200
# gwangju    300    200  180     0      80
# jeonju     200    190   200    80     0



rnames <- c("seoul","busan","daegu","gwangju","jeonju")
v <- c(0, 350, 300, 300, 200,350,0,50,200,190,300,50,0,180,200,300,200,180,0,80,200,190,200,80,0)
city.distance.mat<-matrix(v,5,5,byrow = TRUE, dimnames=list(rnames,rnames))

city.distance.mat["seoul","busan"]
#[1] 350

city.distance.mat[,"seoul"]
#  seoul   busan   daegu gwangju  jeonju  #seoul열만 출력
#     0     350     300     300     200 

city.distance.mat[c("seoul","gwangju"),
        seoul busan daegu gwangju jeonju
seoul       0   350   300     300    200
gwangju   300   200   180       0     80
```

### 행렬의 사칙연산:두행렬의 차원이 같아야함

```
#행렬과 길이가 1인벡터(스칼라)간 연산
mtx +  1
mtx -  1
mtx *2
mtx /2

#행렬간 연산할때는 반드시 두 행렬의 차원이 같아야 함
matrix(1:6, 2, 3)
matrix(6:1, 2, 3)

matrix(1:6, 2, 3)+matrix(6:1, 2, 3)

matrix(1:6, 2, 3)+matrix(6:1, 3, 2)



matrix(1:6, 2, 3)*matrix(6:1, 2, 3)
#element-wise product
matrix(1:6, 2, 3)
matrix(6:1, 2, 3)
```

### %*%:행렬곱셈

```
w<-c(1,2,3,4,5,6)
mtx<-matrix(w,2,3)

#행렬의 곱셈은 앞의 행렬의 열과의 뒤의 행렬의 행이 일치

w
#[1] 1 2 3 4 5 6
# matrix(w,2,3)%*%matrix(w,2,3)

matrix(w,2,3)%*%matrix(w,3,2) #행렬의 곱

#      [,1] [,2]
# [1,]   22   49
# [2,]   28   64

mtx<-matrix(w,2,3)
mtx
#       [,1] [,2] [,3]
# [1,]    1    3    5
# [2,]    2    4    6

mtx%*% 1:3 #2행 3열%*% 길이3인벡터->3행 1열

#      [,1]
# [1,]   22
# [2,]   28
```

## t():행열 반전

```
w<-c(1,2,3,4,5,6)
mtx<-matrix(w,2,3)

#t함수:행열 반전
mtx
#       [,1] [,2] [,3]
# [1,]    1    3    5
# [2,]    2    4    6

t(mtx)
#       [,1] [,2]
# [1,]    1    2
# [2,]    3    4
# [3,]    5    6
t(t(mtx))
#       [,1] [,2] [,3]
# [1,]    1    3    5
# [2,]    2    4    6
```

## 행,열 단위 sum,mean

```
rowSums(mtx) #행합
#[1]  9 12
colSums(mtx) #열합
rowMeans(mtx)#행평균
colMeans(mtx)

```

## 과제

```
# 1. 변수 x에 1~10까지 값 할당, y에 3~1까지 값 할당
# - letters 상수벡터를 이용하여 x에 알파벳 소문자 이름 부여
# - x+y를 수행하고 결과를 설명
x<-1:10
y<-3:1
names(x)<-c(letters[1:10])
x
x+y
# a  b  c  d  e  f  g  h  i  j 
# 4  4  4  7  7  7 10 10 10 13 

# 긴백터에 맞춰서 짧은 벡터가 반복되서 더해짐


# 2. 숫자 2,5,3을 원소로 갖는 벡터 생성한 후 rep함수를 이용하여 다음 벡터를 생성
# - 2,5,3,2,5,3,2,5,3,2,5,3,2,5,3
# - 2,5,3,2,5,3,2,5,3,2
# - 2,2,5,5,5,5,5,3,3,3

rep(c(2,5,3),time=5)
rep(c(2,5,3),length.out=10)
rep(c(2,5,3),time=c(2,5,3))

<-c("one","two","three",'four',"five","six")
# 3. 주사위를 7번 던져서 나온 3,2,5,1,5,6,5의 값을 
# 1)여섯 개의 레벨을 갖는 팩터로 저장하시오.
num<-c(3,2,5,1,5,6,5)
num
num.factor<-factor(num,levels = c(1,2,3,4,5,6))
num.factor
# 2)각 레벨에 one, two, ... six로 이름 부여하시오.
num.factor<-factor(num,levels = c(1,2,3,4,5,6), labels =c("one","two","three",'four',"five","six"))

# 3)레벨별 발생 빈도를 출력하시오.
table(num.factor)


# 4. 1~12까지의 숫자 벡터로 3*4행렬 생성하고 변수에 저장하시오.
# 알파벳 소문자 상수 벡터 letters를 이용하여 행과 열이름을 각각 지정하시오.
# a  b   c   d
# a  1  4
# b 2   5   ...
# c  3  6       12

v<-1:12
al.matrix<-matrix(v,3,4, dimnames = list(letters[1:3],letters[1:4]))

al.matrix

# 5. 4번에서 생성한 행렬로부터 1번째와 3번째 열을 추출하여 부분행렬을 생성하고,
# 2번째와 4번째 열을 추출하여 부분행렬을 생성하고,
# 이들을 열의 방향으로 결합한 새로운 행렬을 생성하시오.


al.matrix[,c(1,3),drop=FALSE]

al.matrix[,c(2,4),drop=FALSE]


new.al.matrix<-cbind(al.matrix[,c(1,3),drop=FALSE],al.matrix[,c(2,4),drop=FALSE])
new.al.matrix


# 6. 4번과 5번문제에서 생성한 두 행렬에 대해 +, -, *, /, %*% 연산을 수행하시오

al.matrix+new.al.matrix
al.matrix-new.al.matrix
al.matrix*new.al.matrix
al.matrix/new.al.matrix

al.matrix%*%t(new.al.matrix)

# 7. 1~9999까지 정수로 9개의 열을 갖는 행렬을 생성하시오.
# 마지막 세 개 행과 마지막 두 개 열로 구성된 3*2 부분행렬을 만드시오.

num1<-1:9999

num1.matrix<-matrix(num1,,9)
num1.matrix[1109:1111,8:9]
```

