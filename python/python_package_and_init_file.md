
# Python Package (`__init__.py`)
써먹지 않으면 배워도 까먹는 것들이 있다. 그 중 하나가 python package... `__init__.py` 는 왜 만들어야 하는가 제대로 알고있지 않아서 안 만들고 자동완성이 왜 안되지..? 하다가 이번 기회에 한번 정리해보기로 하였다.

## PEP 420
[Link](https://www.python.org/dev/peps/pep-0420/)

파이썬 3.3 에서부터는 `__init__.py` 가 없어도 패키지로 인식한다고 한다. 즉 파이썬 2 에서는 `__init__.py` 가 있어야 패키지로 인식했다는 뜻이다.

이 내용은 원래 알고 있었는데, 어설프게 알고 있어서 `__init__.py` 가 아무 역할을 하지 않는거라고 생각하고 있었다. 그러나 실제로는 그렇지 않은 모양이다.

## 파이썬 패키지란?
파이썬에서 모듈은 하나의 파일을 의미한다. 즉 `chatbot.py` 라고 하면 chatbot 에 관련된 클래스나 함수를 모아놓은 chatbot 모듈이다.

패키지는 모듈을 모아놓은 컬렉션이다. 파일이 아니라 폴더로 생각하면 된다. 위에서 보았듯 파이썬 2에서는 폴더 내에 `__init__.py` 가 있어야 패키지로 인식했지만, 파이썬 3에서는 init 파일이 없어도 패키지로 인식이 가능하다.

패키지가 되면 파이썬에서 import 할때 `.`을 찍어서 접근할 수 있다. 아래는 예시이다.

```
from pingpong.chatbot import Chatbot
```

여기에서 pingpong 은 패키지, chatbot 은 모듈, Chatbot 은 클래스 혹은 함수 (명명법을 보건대 클래스일 것 같지만) 가 될 것이다.

즉 위와 같이 쓰는 데에는 굳이 `__init__.py` 파일이 없어도 된다는 말이다.

## 그럼 `__init__.py`가 언제 필요한가?

#### 1. 패키지 사용자가 `from 패키지 import *` 을 사용할때 이때 모듈 내의 어떤 코드를 import 하게 할지를 정할 수 있다.

```
# pingpong 패키지의 __init__.py
__all__ = ['chatbot'] # 여기에 string 형태로 module 이름을 적어주면 from pingpong import * 했을때 chatbot 이 import 된다.
```

#### 2. Nested 된 module 안에 접근할 때 사용할 수 있다.
이 부분이 궁금해서 찾아보기 시작한 것 같은데 한참 검색한 뒤에 알게 되었다.

```
from package.file import File
```
`__init__.py` 가 비어있거나 만들어지지 않은 상태이면 다음과 같은 방법으로 패키지 안에 있는 모듈 안에 있는 클래스에 접근할 수 있다.

그러나 `__init__.py` 에 다음과 같이 적어주면, 패키지 이름으로 클래스에 접근할 수 있게 만들어준다.

```
# 출처: http://mikegrouchy.com/blog/2012/05/be-pythonic-__init__py.html
# __init__.py
from file import File

# 패키지를 사용하는 부분
from package import File
```

tensorflow github 에서도 비슷한 예시를 본 것 같아서 찾아보니 비슷한 식으로 쓰는 것 같다.
https://github.com/tensorflow/tensorflow/blob/90733a8024532f6993d11f0a89deaecb2bba59fe/tensorflow/python/__init__.py


## 정리: `__init__.py` 는 어떻게 만드는가?
그냥 빈 파일을 만들어두어도 된다. 위에서 본 것 같은 특별한 역할이 필요한 것이 아니라면 빈 파일만 만들어두자. stack overflow 같은데서 많은 사람들이 `__init__.py` 는 비어있는 상태로 두는 것이 Best 라고 이야기한다.

그리고 `__all__` 로 모듈의 public / private 을 명시적으로 관리해야 하거나, 깊숙한 곳에 있는 클래스의 접근성을 위하여 코드를 추가할 수 있다.

...정도로 정리할 수 있을 것 같다.

## 참조
공부하면서 본 자료들을 정리해둔다.

1. http://python-guide-kr.readthedocs.io/ko/latest/writing/structure.html
2. http://pythonstudy.xyz/python/article/18-패키지
3. 파이썬 코딩의 기술 Better way 50 / 브렛 슬라킨 지음 / 김형철 옮김 / 길벗
4. [Be Pythonic: __init__.py](http://mikegrouchy.com/blog/2012/05/be-pythonic-__init__py.html)
