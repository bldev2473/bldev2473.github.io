---
title: "[Python] 문법 정리"
date: 2020-12-11 00:10:00 -0000
categories: Python
---

## 컴프리헨션 (Comprehension)
#### 리스트 컴프리헨션
```python
[표현식 for 임시변수명 in 원본리스트명]
```

#### 집합 컴프리헨션
```python
{표현식 for 임시변수명 in 원본집합명}
```

#### 딕셔너리 컴프리헨션
```python
{표현식 for 임시변수명 in 원본딕셔너리명}
```

#### 제너레이터 컴프리헨션
```python
(표현식 for 임시변수명 in 반복가능객체명)
```

## 함수
#### 함수 정의
```python
def 함수명(매개변수명1, 매개변수명2):
  pass
```

#### 위치 인수
- 위치 인수 (Positional Argument): 함수 호출 시 적절한 위치에 순서대로 넣는 인수 

#### 임의 인수
- 임의 인수 (Arbitrary Arguments): 위치와 개수가 정해져 있지 않아 임의로 전달할 수 있는 인수
  
```python
def 함수명(*매개변수명):
  pass
```

#### 고정 인수 + 임의 인수
```python
def 함수명(매개변수명, *args):
  pass
```

#### 키워드 인수
- 키워드 인수 (Keyword Argument): 함수 호출 시 ‘키=값’ 형태로 전달하는 인수

#### 키워드 인수와 딕셔너리 언패킹
```python
def 함수명(**매개변수명):
  pass
```

#### 고정 인수 + 키워드 인수
```python
def 함수명(매개변수명, **kwargs):
  pass
```

#### 임의 인수 + 키워드 인수
```python
def 함수명(*args, **kwargs):
  pass
```

#### 고정 인수 + 임의 인수 + 키워드 인수
```python
def 함수명(매개변수명, *args, **kwargs):
  pass
```

#### 매개변수 초기화
```python
def 함수명(매개변수명=초기값):
  pass
```

## 클래스
#### 클래스 정의
```python
class 클래스명:
  pass
```

#### 인스턴스 메서드 정의
```python
class 클래스명:
  def 메서드명(self):
    pass
```

#### 인스턴스 속성 정의
```python
class 클래스명:
  def __init__(self):
    self.속성명1 = 값1
    self.속성명2 = 값2
```

```python
class 클래스명:
  def __init__(self, 매개변수명1, 매개변수명2):
    self.속성명1 = 매개변수명1
    self.속성명2 = 매개변수명2
```

```python
class 클래스명:
  def __init__(self, *args):
    self.속성명1 = args[0]
    self.속성명2 = args[1]
    self.속성명3 = args[2]
```

```python
class 클래스명:
  def __init__(self, **kwargs):
    self.속성명1 = kwargs[‘키명1’]
    self.속성명2 = kwargs[‘키명2’]
    self.속성명3 = kwargs[‘키명3’]
```

```python
class 클래스명:
  def __init__(self, *args, **kwargs):
    self.속성명1 = args[0]
    self.속성명2 = args[1]
    self.속성명3 = args[2]
    self.속성명4 = kwargs[‘키명1’]
    self.속성명5 = kwargs[‘키명2’]
    self.속성명6 = kwargs[‘키명3’]
```

#### 인스턴스 속성 제한
```python
class 클래스명:
  __slots__ = ['속성명1', '속성명2']
```

#### 클래스 메서드 정의
```python
class 클래스명:
  @classmethod
  def 메서드명(cls, 매개변수명1, 매개변수명2):
    pass
```

#### 정적 메서드 정의
```python
class 클래스명:
  @staticmethod
  def 메서드명(매개변수명1, 매개변수명2):
    pass
```

#### 클래스 속성 정의
```python
class 클래스명:
  속성명1 = 값1
  속성명2 = 값2
```

#### 인스턴스 메서드 접근 제어
```python
class 클래스명:
  def __메서드명(self):
    pass
```

#### 인스턴스 속성 접근 제어
```python
class 클래스명:
  def __init__(self)
    self.__속성명 = 값
```

#### 클래스 상속
```python
def 상위클래스명:
  pass
```

```python
def 하위클래스명(상위클래스명):
  pass
```

#### 클래스 다중 상속
```python
def 상위클래스명1:
  pass
```

```python
def 상위클래스명2:
  pass
```

```python
def 하위클래스명(상위클래스명1, 상위클래스명2):
  pass
```

#### 다이아몬드 문제 (Diamond Problem)
```python
class A:
  def method(self):
    pass
 
class B(A):
  def method(self):
    pass

class C(A):
  def method(self):
    pass
  
class D(B, C):
  pass
```

```python
D.mro()
```

#### 추상 클래스
```python
from abc import ABC, abstractmethod
 
class 추상클래스명(ABC):
  @abstractmethod
  def 메서드명(self):
    pass
```

## 클로저
#### 클로저 정의 (함수 사용)
```python
def 외부함수명(매개변수명):
  변수명 = 값
  def 내부함수명(매개변수명):
    return 값
  return 내부함수명
```

#### 클로저 정의 (람다식 사용)
```python
def 외부함수명(매개변수명):
  변수명 = 값
  return lambda x: 값
```

#### 클로저 사용
```python
변수명1 = 외부함수명(인자명)
변수명2 = 외부함수명(인자명)
```
```python
변수명1(인자명)
변수명2(인자명)
```

## 예외 처리
#### 예외 처리
```python
try:
  pass
except:
  예외 발생 시 실행할 코드
```

```python
try:
  pass
except:
  예외 발생 시 실행할 코드
else:
  예외가 발생하지 않을 때 실행할 코드
```

```python
try:
  pass
except:
  예외 발생 시 실행할 코드
else:
  예외가 발생하지 않을 때 실행할 코드
finally:
  예외 발생 여부와 관계없이 항상 실행할 코드
```

#### 특정 예외 처리
```python
try:
  pass
except 예외명:
  예외 발생 시 실행할 코드
```

#### 에러 메시지 출력
```python
try:
  pass
except 예외명 as 변수명:
  예외 발생 시 실행할 코드
  print(변수명)
```

#### 예외 발생 시키기
```python
try:
  raise 예외명(‘에러메시지’)
except Exception as e:
  print(e)
```

```python
try:
  try:
    raise 예외명(‘에러메시지’)
  except Exception as e:
    print(e)
    raise
except Exception as e:
  print(e)
```

## 이터레이터 (Iterator)
#### iterable, iterator
- 반복 가능한 객체 (iterable 객체): iterator를 반환할 수 있는 객체
- 이터레이터 (iterator) 객체: 상태를 가지고 있고 next()를 호출하여 다음 값을 만들어낼 수 있는 객체

#### iterable 객체로 iterator 생성
```python
iterable객체명.__iter__
iter(iterable객체명, 반복을끝낼값)
```

#### iterable 객체의 요소들을 차례대로 꺼내기
```python
iterator객체명.__next__
next(iterator객체명, 기본값)
```

## 제너레이터 (Generator)
#### 제너레이터 정의
```python
def 제너레이터함수명:
  yield 값1
  yield 값2
  yield 값3
```

```python
def 제너레이터함수명:
  yield form 반복가능한객체명
```

#### 반복문과 제너레이터
```python
for i in 제너레이터함수명():
  print(i)
```


