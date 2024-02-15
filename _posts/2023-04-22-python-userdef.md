---
title: Python-사용자-정의-함수
author: arrow-economist
date: 2023-04-22 00:38:00 +0800
categories: [Python]
tags: [Python]
---

# #Python #def #functions

C언어 포스팅을 하다가 갑자기 파이썬 관련 글을 포스팅하게 된 이유는, 그냥 C 배우는 김에 파이썬도 복습할 겸 올리고 싶어서다. 능숙하게는 다루지 못하고 그냥 다른 언어로 있는 코드를 파이썬으로 번역하는 정도로밖에 다루지 못해서, 이김에 파이썬도 좀 배워보고자 한다.

프로그래밍을 하다 보면, 내가 원하는 방식대로 함수를 만들어야 할 때가 대부분이다. 그럴 때는 사용자 정의 함수를 사용하게 되는데, 파이썬에서 함수를 정의하는 방법은 다음과 같다.

```python
def hola():
	print("Hello!")

hola()
```

우선 함수를 정의할 때는 `def`를 쓴다. 그리고 그 다음에는 내가 쓰고싶은 함수명을 입력해주면 된다. 여기에서는 `hola`가 그 부분이다. 그리고 소괄호를 쓴 다음에 콜론까지 써줘야한다. 그리고 그 다음 줄부터는 들여쓰기가 시작되는데, 파이썬 언어는 기본적으로 들여쓰기로 어떤 코드에 무엇이 포함되어 있는지를 판단하기 때문에 `def` 부분 들여쓰기에 주의해야한다. 예를 들어 `print("Hello!")`라고 입력한다면, 이 함수 `hola()`를 호출할 때마다 `Hello!`가 프린트 되게 된다.

이 예시에는 입력변수, 즉 파라미터가 들어가있지 않은 경우다. 파라미터가 들어간다면, 다음과 같이 쓸 수 있겠다.

```python
def say_hello(name, age):
	print("hello", name)
	print("you are", age,  "years old")

say_hello("Arrow",  20)
```

`say_hello`라는 함수를 정의했는데, 여기에는 `name`과 `age` 두 변수가 들어간다. 변수가 여러 개인 경우엔 콤마로 구별해주면 된다. 그리고 파라미터를 밑의 함수 정의 구간에서 자유롭게 사용해주면 된다. 다음과 같이 표현한다면,

`hello Arrow you are 28 years old`

라는 결과가 뜨게 될 것이다. 그럼 좀 더 복잡하게 만들 수도 있을까? 물론이다. 마지막으로 간단하게 만들어본 함수를 보여줄 예정이다.

```python
def gpa_cal(g1, g2, g3):
	grades = {'A': 4, 'B+': 3.5, 'B': 3, 'C+': 2.5, 'C': 2, 'D+': 1.5, 'D': 1, 'F': 0}
	a1 = grades.get(g1, 0)
	a2 = grades.get(g2, 0)
	a3 = grades.get(g3, 0)
	my_gpa = (a1 + a2 + a3) / 3
	print(my_gpa)

gpa_cal("A", "B+", "A")
```

내가 만든 `gpa_cal` 함수는 3개의 과목에서 받은 각각의 학점을 입력하면 내 gpa를 계산해준다. 우선 `grades`는 딕셔너리형 자료로 정의가 되었고, `get`함수를 통해 점수로 변환한 뒤에 평균을 내주었다. `gpa_cal("A", "B+", "A")`라고 입력하면 `3.833`과 같은 점수가 출력되게 될 것이다.

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc0Mjg3OTEwNF19
-->