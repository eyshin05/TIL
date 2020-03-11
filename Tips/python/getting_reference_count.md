# Python Reference Count
[위키백과: 쓰레기 수집 (컴퓨터 과학)][1]

오 이거 하면서 알게 된건데 괄호가 들어간 url 은 다음과 같이 링크하면 된다.

```
[위키백과: 쓰레기 수집 (컴퓨터 과학)][1]
~내용~
  [1]:ko.wikipedia.org/wiki/쓰레기_수집_(컴퓨터_과학)
```
그냥 관련 자료 찾다가 쓰레기 수집이라는 용어가 너무 이상해보여서 링크해보았다.

## 사용법                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              

```
>>> import sys
>>> a = 1
>>> sys.getrefcount(a)
809
>>> b = '1'
>>> sys.getrefcount(b)
2
```

여기서 1은 python이 -5 ~ 255 사이의 값을 singleton 으로 관리해서 809 인 것 같고,
여튼 저런식으로 reference count 를 구할 수 있다.

참고로 b 가 2 인 이유는 getrefcount 함수에 b 가 매개변수로 들어가서 매개변수까지 counting 되어서 그렇기 때문에, getrefcount 함수의 결과값에서 1을 뺀 값이 실제 refcount 로 보면 된다.

  [1]:ko.wikipedia.org/wiki/쓰레기_수집_(컴퓨터_과학)
