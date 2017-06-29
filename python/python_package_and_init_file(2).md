정리를 해놔도 별로 보지를 않으니 또 삽질을 했지만...
그래도 나름 좋은 정보라서 업데이트 한다 =ㅅ=

[저번](https://github.com/eyshin05/TIL/blob/master/python/python_package_and_init_file.md)과는 달리 `__all__` 과 함께 `__init__` 을 업데이트 하는 방법이다.

## 방법

오픈 소스 패키지처럼 다양하게 사용할 목적으로 API를 작성할 때,

* 릴리즈 간의 변경 없이 안정적인 기능을 제공하려면 내부 코드 구조를 숨겨야 함
* `__all__` 로 API 공개 부분을 제한하고
* 아래처럼 써주면 `__all__` 부분을 `package.utils.model` 라고 쓰는 대신 `package.model` 이라고 쓸 수 있는것 같군요

```
# __init__.py
__all__ = []
from . models import *
__all__ += models.__all__
from . utils import *
__all__ += utils.__all__
```

## 덧붙임
그러나 오픈 소스 패키지 처럼 공개된 패키지가 아니라 단순히 협업 / 팀 프로젝트 용 python project 라면 굳이 이렇게 할 필요가 없을 것이다 . . . 

특별한 이유가 없으면 default 로는 빈 `__init__.py` 을 쓰자.

## 출처
코딩의 기술 Better way 50. 모듈을 구성하고 안정적인 API 를 제공하려면 패키지를 사용하자
