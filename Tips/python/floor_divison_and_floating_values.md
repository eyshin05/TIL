# Floor Division

파이썬3 에서 floor division 이란 다음과 같은 연산자를 의미한다.

```
>>> 5//2
2
```

## Floor division 의 float by float 연산

그런데 이것을 float by float 연산으로 하면 다음과 같은 현상들을 관찰할 수 있다.

```
>>> 0.99//0.01
98.0
>>> 0.99/0.01
99.0
>>> math.floor(0.99/0.01)
99
```

이게 어떻게 된 건지 궁금해서 좀 더 파보았다.

## float 의 부정확함

float 을 처음 배울때 float 자료형이 정확하지 않다는 내용을 배운다.
실제로 살펴보면 다음과 같이 그 내용을 관찰할 수 있다. 

```
>>> '{:.34f}'.format(0.01)
'0.0100000000000000002081668171172169'
>>> '{:.34f}'.format(0.99)
'0.9899999999999999911182158029987477'
```

즉 위와 같은 내용을 통해 보면 0.99 보다 작은 값을 0.01 보다 큰 값으로 나눈 몫을 구하기 때문에 98이 나온다는 것을 이해할 수 있다. 

```
>>> '{:.34f}'.format(0.99/0.01)
'99.0000000000000000000000000000000000'
```

반면 true_division 할 때에는 정확한 값이 나온다. 그치만 왜 true divison 할 때에는 정확한 값이 나오는 걸까?

## Python 에서의 부동소수점 자리수

```
>>> a = 0.1000000000000001
>>> a
0.1000000000000001
>>> a = 0.10000000000000001
>>> a
0.1
```

파이썬에서는 소수점 17자리수에서 반올림 해서 표시하는 것으로 보인다. 

```
>>> a = 1.0000000000000001
>>> a
1.0
>>> 0.99 * a
0.99
>>> '{:.34f}'.format(0.99 * a)
'0.9899999999999999911182158029987477'
>>> '{:.34f}'.format(0.99)
'0.9899999999999999911182158029987477'
```

음...
float float 연산에서 아예 17 자리수 이하의 값은 무시해버리는 것으로 보인다. 

##  교훈

* float 연산은 부정확하다는 것을 인식하고 쓰자
* float // float 연산은 쓰지 말자
  * 대부분의 연산은 float 자료형에서 발생하는 작은 오차 값을 무시하고 진행되지만, floor division 은 예외이다.

