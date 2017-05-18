# `**kwargs`

## 사용법

사용법은 아래와 같은 친구분. 존재는 알고 있었지만 친하지 않아서 정리해보기로 했다.

```
def some_function(func_reference, **kwargs):
    print('run some function: %s' % func_reference('test', **kwargs))
    
def reference_function(query, multiple=1):
    return query * multiple

print('step 1')    
some_function(reference_function)

print()
print('step 2')
some_function(reference_function, multiple=3)
```

```
결과:
step 1
run some function: test

step 2
run some function: testtesttest
```

참고로 비슷한 친구인 `*args` 는 keyword 가 포함되지 않은 경우, `**kwargs` 는 키워드가 붙은 경우를 담당한다.

## kwargs 의 형태

kwargs 는 어떤 식으로 넘어갈까?

```
def some_function2(**kwargs):
    print(len(kwargs))
    print(kwargs)

print('step 1')
some_function2()

print()
print('step 2')
some_function2(a=1, b=2)
```

```
결과:
step 1
0
{}

step 2
2
{'a': 1, 'b': 2}
```

음, 실제로는 dictionary 형태로 관리가 되는구나. 그리고 kwargs 가 없는 경우에는 빈 dictionary 가 들어가는 것도 알 수 있다.

## 매개변수가 없는 함수 인스턴스를 가져올 경우

```
def some_function(func, **kwargs):
    func(**kwargs)

def reference_function():
    print('test')
    
some_function(reference_function)
```

```
결과:
test
```

아무것도 받지 않는 함수의 경우에도 kwargs 가 빈 dictionary 로 들어가면 문제없이 실행된다. 물론 위 코드에서 `some_function(reference_function, a=1)` 같은 식으로 kwargs 에 무언가를 넘겨주면 에러가 난다.

```
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-7-60e1dc0ba5ca> in <module>()
      5     print('test')
      6 
----> 7 some_function(reference_function, a=1)

<ipython-input-7-60e1dc0ba5ca> in some_function(func, **kwargs)
      1 def some_function(func, **kwargs):
----> 2     func(**kwargs)
      3 
      4 def reference_function():
      5     print('test')

TypeError: reference_function() got an unexpected keyword argument 'a'

```

