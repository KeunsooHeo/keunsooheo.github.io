---
layout: dark-post
title: 파이썬 강의 - 반복문 for
date: 2018-11-07
author: Geunsu Heo
categories: [python lecture]
tags: [python,lecture]
sitemap:
  changefraq: daily
  priority: 1.0
---

## 반복문 for
이번 시간에는 다른 반복문인 for문을 배운다. for문은 while과 다르게 조건에 의해 반복이 되는 것이 아니라 나열가능한 자료형의 요소들을 하나하나 꺼내며 반복하는 반복문이다. 아래의 for문의 구조를 살펴보자
```
for 변수명 in 나열 가능한 자료형(리스트, 튜플, 문자열):
  #시작 시 자료형의 첫 요소를 변수에 넣고 문장을 실행
  #수행할 문장
  #문장이 끝나면 다음 요소를 변수에 넣고 다시 실행
```

### for 기본 구조
#### 리스트와 사용하기
for문에서 많이 사용하는 나열가능한 자료형을 들자면 리스트를 들 수 있다. 리스트를 사용하여 for문이 어떻게 작동이 되는지를 살펴보도록 하자.
```python
li = [1,2,3,4,5,6,7,8,10]
for a in li:
  print("for문 진행 중 a값: ",a)

print("for문이 끝나고 a값: ",a)
```
```
for문 진행 중 a값:  1
for문 진행 중 a값:  2
for문 진행 중 a값:  3
for문 진행 중 a값:  4
for문 진행 중 a값:  5
for문 진행 중 a값:  6
for문 진행 중 a값:  7
for문 진행 중 a값:  8
for문 진행 중 a값:  10
for문이 끝나고 a값:  10
```
for문이 끝나면 마지막에 할당된 요소가 a값에 들어있는 것을 확인할 수 있다. 하지만 이 변수는 for문 내에서만 사용을 하기 위한 변수이므로 for문이 끝나고 나서는 사용하지 않는 것을 권장한다.

#### 문자열과 사용하기
for문에 문자열도 사용이 가능하며 아래 예제를 for문을 사용하여 쉽게 자료형을 처리할 수 있다.
```python
str1 = input("문자열을 입력해주세요 : ")
symbol = input("찾을 알파벳을 입력해주세요 : ")
count = 0
for ch in str1:
  if ch == symbol:
    count += 1;

print("찾은 %s의 개수 : %d" % (symbol,count))
```
이처럼 우리가 이전 예제에서 풀었던 알파벳 숫자세기도 for문을 사용하면 쉽게 풀 수 있다.
```python
str1 = "PYthon is very cool"
sym = input("찾을 알파벳").lower()
count = 0
for ch in str1.lower():
  if ch == sym:
    count += 1

print("찾은 %s의 개수 : %d" % (sym,count))
```

### 튜플과 사용하기
튜플과 사용하는 경우는 2,3개의 값을 한 번에 받을 때 많이 사용하며 아래 예제를 보며 for문 변수를 여러 개를 한 번에 처리할 수 있는 것을 확인해보자
```python
tuple_list = [(1,2),(3,6),(5,6)]
for a,b in tuple_list:
  print("a:",a)
  print("b:",b)
```
```
a: 1
b: 2
a: 3
b: 6
a: 5
b: 6
```
>물론 여기서 튜플 대신 리스트를 사용해도 된다. 하지만 튜플의 사용 목적 중 대표적인 것이. 이러한 몇 개의 쌍을 한 번에 처리하는데 있다. 따라서 쌍으로 처리를 할 필요가 있을 때는 튜플을 사용하도록 하겠다.
> 
---

## range()
for문과 같이 사용되는 함수로 원하는 수를 나열해주는 함수이다. 매개변수, 함수 괄호 안에 넣어주는 값을 몇 개를 넣어주느냐에 따라서 실행되는 방식이 달라진다.
#### 정수 두 개 range(start,end)
정수 두 개를 입력한 경우를 먼저 보자. range(a,b)로 했을 때 a이상 b미만의 정수를 순서대로 나열한다. 아래의 예를 살펴보자
```python
print(range(1, 5)) #range(1, 5)
print(list(range(1, 5))) #[1,2,3,4]
```
위처럼 1부터 5미만까지의 정수를 나열하며 마지막 숫자 5는 포함하지 않는 것을 확인할 수 있다. 이때 주의할 점은 range()함수의 결과는 range로 단독으로 사용시 리스트나 튜플같은 나열가능한 자료형으로 바꿔서 사용하는 것이 편하다.  
#### 정수 한 개 range(end)
정수 한 개만 넣어주면 0부터 b까지를 나열하며 이때도 b는 포함하지 않는다. 즉 위의 두 개의 경우에서 시작점을 0으로 잡는다.
```python
print(range(5)) #range(0, 5)
print(list(range(5))) #[0,1,2,3,4]
```
#### 정수 세 개 range(start,end,step)
정수 세 개의 경우는 마지막 매개변수는 step으로 몇 개씩 뛰어넘어서 나열할 것인지를 나타내는 요소이다.
```python
print(range(0,5,2)) #range(0, 5, 2)
print(list(range(0,5,2))) #[0,2,4]
```
### range()를 사용하기
이 range()를 이용하여 for문을 사용해보자. 1부터 10까지 출력하는 예제를 통해 range()가 왜 for문과 같이 사용되는지 알 수 있을 것이다.
```python
for a in range(1,11):
  print(a,end=' ')
``` 
```
1 2 3 4 5 6 7 8 9 10
```

---
### break, continue
우리가 for문과 다른 반복문 whlie을 배울 때 배웠던 break, continue는 for문에서도 사용이 가능하다. while문에서 했던 것처럼 0~10까지의 짝수를 출력해보면서 적용해보자
```python
for a in range(1,100):
  if a>10:
    break
  if a%2 == 1:
    continue
  print("%2d은(는) 짝수입니다."%a)
```
```
 2은(는) 짝수입니다.
 4은(는) 짝수입니다.
 6은(는) 짝수입니다.
 8은(는) 짝수입니다.
10은(는) 짝수입니다.
```
---
### enumerate
또한 for문과 같이 사용되는 함수로 enumerate()를 들 수 있다. enumerate()안에는 나열가능한 자료형이 들어가며 for문과 같이 사용 시 요소의 인덱스와 요소를 같이 처리할 수 있다. 아래 예제를 통해서 감을 잡아보도록 하자.
```python
st = "python"
for i, ch in enumerate(st):
  print("%d번째 요소 %s" % (i,ch))
```
```
0번째 요소 p
1번째 요소 y
2번째 요소 t
3번째 요소 h
4번째 요소 o
5번째 요소 n
```
위와 같이 enumerate()를 사용하면 for문안의 앞 변수는 인덱스가 들어갈 변수, 뒤 변수는 요소가 들어갈 변수로 지정해야한다.
---
#### 참고 도서
[점프투파이썬](https://wikidocs.net/22)

--
### 예제 1 배수 찾기
사용자로부터 정수 1<=n<10을 입력받아 1~100까지 수 중에서 n의 배수를 모두 출력해주는 프로그램을 작성하시오.
```
정수를 입력해주세요 : 3
1~100사이의 3의 배수는 아래와 같습니다.
3
6
9
(이하 생략)
```
### 예제 2 리스트 분석하기
Alice의 과목 점수를 리스트로 나열하면 [89,36,64,94,56]이다. Alice의 과목 평균 점수와 합계 점수 그리고 최대 점수를 출력하여라
```
평균 : 67.8
합계 : 339
최대 점수 : 94
```

### 예제 3 구구단 출력
아래와 같은 구구단을 출력하시오.
```
2 4 6 8 10 12 14 16 18 
3 6 9 12 15 18 21 24 27 
4 8 12 16 20 24 28 32 36 
5 10 15 20 25 30 35 40 45 
6 12 18 24 30 36 42 48 54 
7 14 21 28 35 42 49 56 63 
8 16 24 32 40 48 56 64 72 
9 18 27 36 45 54 63 72 81 
```

### 예제 4 enumerate
길이가 5이고 음이 아닌 정수가 들어가있는 리스트가 있다. 이 리스트에서 11이상의 정수가 있다면 모두 10의 나머지로 만드는 프로그램을 작성하시오.(이때 리스트는 코드에 작성)
```
변경 전 : [1,19,80,9,20]
변경 후 : [1,9,0,9,0]
```
