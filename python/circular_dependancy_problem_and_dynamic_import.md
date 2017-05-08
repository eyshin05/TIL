# 순환 의존성 해결하기

A 모듈에서 B 모듈을 필요로 하는데, B 모듈을 불러우기 위해서 A 모듈의 일부가 필요한 경우가 있다.

```
# A.py
from B import get_something

class A_class:
  def __init__(self):
    self.something = get_something()
    
# B.py
from A import A_class

def get_something():
  return something
```

(여러가지 상황에서 발생할 수 있지만) 예를 들자면 이런 경우에 순환 의존성이 생길 수 있다.
해결하는 방법도 여러가지 있지만 그 중 하나가 동적 임포트이다.

```
class A_class:
  def __init__(self):
    from B import get_something
    self.something = get_something()
    
# B.py
from A import A_class

def get_something():
  return something
```

이렇게 import 문의 위치를 함수 내로 옮겨주면 함수가 실행될 때 import 하게 되므로 동적 임포트라고 한다.

## 참고서적
1. 파이썬 코딩의 기술 / 길벗: Better way 52. 순환 의존성을 없애는 방법을 알자
(이 책에 다른 해결방법을 비롯하여 더 자세한 설명이 서술되어 있다.)
