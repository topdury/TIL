# day 8

## pow()거듭제곱

```
pow(3,2)==3**2

```

## round()반올림

```
round(3.141592,4) #소수 4번째 자리까지 출력
=3.1416
```

### 사사오입 법칙

```
반올림시 정수 부분이 홀수면 올림

짝수면 내림
round(4.5)  #결과는 4
round(3.5)  #결과는 4

```

## 올림,내림

### 올림

```
import math #math 모듈을 먼저 import해야 한다.
 math.ceil(-3.14)    #결과는 -3
 math.ceil(3.14) #결과는 4
```

## 내림

```
 math.trunc(-3.14)   #결과는 -3
 #마치 int같이 작용한다
 
 
 math.floor(-3.14)   #결과는 -4
 #floor는 무조건 아랫쪽으로 향해 내림한다
```

### zip함수

```
zip(*iterable)
※ 여기서 사용한 *iterable은 반복 가능(iterable)한 자료형 여러 개를 입력할 수 있다는 의미이다.

각 항끼리 묶어줌
print(list(zip([1,2],[3,4],[5,6],[7,8])))
[(1, 3, 5, 7), (2, 4, 6, 8)]

list(zip([1, 2, 3], [4, 5, 6]))
[(1, 4), (2, 5), (3, 6)]

list(zip([1, 2, 3], [4, 5, 6], [7, 8, 9]))
[(1, 4, 7), (2, 5, 8), (3, 6, 9)]

list(zip("abc", "def"))
[('a', 'd'), ('b', 'e'), ('c', 'f')]
```







