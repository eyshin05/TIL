# `**kwargs`

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

음, 이해했다.
