---
title: "[Python] 객체 복사"
date: 2021-01-07 00:10:00 -0000
categories: Python
---

## 객체 복사
#### 1) 얕은 복사: 객체를 참조
- 얕은 복사를 하는 것은 객체를 참조하는 것이며 복사한 객체를 변경했을 때 기존의 객체도 변경됨

1. 변수명 할당  
```python
a = b
```

2. copy 모듈 사용  
```python
import copy as cp
newObj = cp.copy(obj)
```

#### 2) 깊은 복사: 기존의 객체로 새로운 객체를 생성
- 깊은 복사를 하는 것은 기존의 객체로 새로운 객체를 생성하는 것이며 복사한 객체를 변경해도 기존의 객체는 변경되지 않음

1. 리스트 깊은 복사  
```python
newList = myList[:]
```

2. 셋 깊은 복사  
```python
newSet = mySet.copy()
```

3. 딕셔너리 깊은 복사  
```python
newDict = myDict.copy()
```

4. 기타 객체 깊은 복사  
```python
import copy as cp  
newObj = cp.deepcopy(myObj)
```
