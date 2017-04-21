# Jupyter Notebook 에서 debugging 하는 방법
사실 Jupyter notebook 보다는 Pycharm 에서 debugging 하는 걸 더 선호하는 편이지만, 큰 모델을 이미 Jupyter notebook 에 띄워둔 상태라던가 하는 경우에는 디버깅이 필요할 때가 가끔 있다.

## 방법 1
```
%%debug
코드
```

위와 같이 쓰면 ipdb 를 이용하는 것처럼 debugging 할 수 있다. 주요 command 는 다음과 같은 것들이 있다. 
- n : next line (step in 하지 않음)
- s : step in
- u : step out
- b filename:linenum : set break point
- c : continue (break point 를 만날때까지 실행)
- tbreak : 한번만 걸리게 하는 temporary break point
- disable N(break point number): break point 를 disable 함

여기서 break point 를 만드는 코드는 ```b 폴더 1/폴더 2/파일.py:108``` 이런식으로 들어가면 된다. 지금 작업하고 있는 파일에 들어온 상태면 line num 만 적어주어도 됨.

근데 좀 불안정한 것 같다...

## 참고
1. http://frid.github.io/blog/2014/06/05/python-ipdb-cheatsheet/ ipdb cheat sheet 정리가 잘 되어 있다.
