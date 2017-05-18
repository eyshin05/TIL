#Jupyter Notebook Duct-taping

나는 클래스나 모듈을 주로 PyCharm 으로 짜고, 테스트 할때에는 Jupyter Notebook 으로 하는데, 테스트 중 버그가 있어서 PyCharm 으로 수정하게 되면 import 문으로는 고친 코드를 불러올 수 없기 때문에 여러가지 방법을 사용하게 되었다.

## importlib

먼저 전체 모듈을 다시 불러오는 게 편한 경우가 있다. 고친 코드가 하나의 메소드면 functools 같은걸 쓰면 되는데, 모듈 내에서 산발적으로 발생하게 되는 경우에는 `importlib.reload` 를 쓰게 된다.

근데 `importlib.reload` 로 path 깊숙히 있는 (주로 `from path1.path2.module import class` 이런식으로 불러오게 되는) 코드를 가져올 때에는 좀 헷갈리는데, 이렇게 쓰면 된다.

```
import importlib
import path1.path2.module 
importlib.reload(path1.path2.module)

instance = path1.path2.module.class(class_init_parameter)

instance.method()
```

## Monkey patch

하나의 메소드만 바꿔끼면 되는 경우라면 monkey patch 라고 불리는 방법을 쓰면 되는데, 그냥 갈아끼면 된다. 이 방법은 Jupyter Notebook 내에서 메소드를 바로 고쳐서 갈아끼는 방식으로 쓴다.

```
class Class:
    def __init__(self, name):
        self.name = name

    def class_method(self):
        print(self.name)

instance = Class('apple')
instance.class_method()

def class_method(self):
    print('name: %s' % self.name)

Class.class_method = class_method
instance.class_method()
```
```
결과:
apple
name: apple
```

## functools
위 방법 대신에 functools 라는 모듈을 쓰기도 하는데, 이런식으로 쓰면 된다.

```
from functools import partial
def class_function(self, params):
  # 갈아끼울 메소드 내용

class_instance.class_function = partial(class_function, class_instance)
```

훌륭하신 동료분이 알려준 방법이다. 한동안 monkey patch 방법을 자세히 몰라서 이 방법만 계속 썼었는데 정리하고 나니 차이점이 좀 보인다 🤔

코드로 유추해 볼 때 monkey patch 와의 차이점은, monkey patch 는 Class 에 선언된 method 자체를 갈아끼우는 방식이고, functools 를 이용하면 한 instance 에서만 method 를 갈아끼울 수 있다는 점인 것 같다.

그리고 functools 는 decorator 를 이용한다고 하니 역시 내부적으로 동작하는 방식이 다른거겠지 싶다.


## 참고 사이트
1. https://docs.python.org/3/library/functools.html
2. http://stackoverflow.com/questions/5626193/what-is-a-monkey-patch
