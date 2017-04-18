# search 할 때 dict, list, set 걸리는 시간 비교

```
In [1]: a = list(range(100))

In [2]: b = {key:True for key in a}

In [3]: c = set(a)

In [10]: %timeit 73 in a
# The slowest run took 5.80 times longer than the fastest. This could mean that an intermediate result is being cached.
# 1000000 loops, best of 3: 848 ns per loop

In [11]: %timeit 73 in b
# The slowest run took 60.12 times longer than the fastest. This could mean that an intermediate result is being cached.
# 10000000 loops, best of 3: 28.9 ns per loop

In [12]: %timeit 73 in c
# The slowest run took 55.84 times longer than the fastest. This could mean that an intermediate result is being cached.
# 10000000 loops, best of 3: 32.6 ns per loop

In [14]: sys.getsizeof(a)
Out[14]: 1008

In [15]: sys.getsizeof(b)
Out[15]: 6240

In [16]: sys.getsizeof(c)
Out[16]: 8416
```

Set 의 element search 속도가 궁금해서 해 본 실험. 속도는 dict 와 비슷하니 비슷하게 해싱하고 있다고 봐도 되는걸까?

근데 size 가 dict 보다 큰 것은 의외였다... :fearful: 
