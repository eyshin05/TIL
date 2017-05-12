# Python Integer Reference
이런 비슷한 코드를 짜다가 멍청한 짓을 하고 있다는걸 알았다.

```
class A:
    def __init__(self):
        self.turn = 0
        self.bs = [B('1', self.turn), B('2', self.turn), B('3', self.turn)]

    def run_3turns(self):
        for i in range(3):
            for b in self.bs:
                b.print_turn()
            self.turn += 1


class B:
    def __init__(self, name, turn):
        self.name = name
        self.turn = turn

    def print_turn(self):
        print('%s: %d' % (self.name, self.turn))
```

음 물론 실행해보면 다음과 같이 나온다.

```
a = A()
a.run_3turns()

# 결과:
# 1: 0
# 2: 0
# 3: 0
# 1: 0
# 2: 0
# 3: 0
# 1: 0
# 2: 0
# 3: 0
```

integer 는 immutable 이니까 += 1 을 해버리면 다른 instance 가 만들어져버린다. 그래서 reference 같은걸 명시적으로 줄 수 없나 봤더니 stack overflow 에서도 `a = [0]` 같이 쓰길래 그냥 class 로 wrapping 하기로 했다.

```
class Turn:
    def __init__(self):
        self.turn = 0

    def clear(self):
        self.turn = 0

    def add(self, num=1):
        self.turn += num

    def get(self):
        return self.turn

    def __int__(self):
        return self.get()


class A:
    def __init__(self):
        self.turn = Turn()
        self.bs = [B('1', self.turn), B('2', self.turn), B('3', self.turn)]

    def run_3turns(self):
        for i in range(3):
            for b in self.bs:
                b.print_turn()
            self.turn.add()


class B:
    def __init__(self, name, turn):
        self.name = name
        self.turn = turn

    def print_turn(self):
        print('%s: %d' % (self.name, self.turn.get()))
```

그냥 integer 에 조금 더 살을 붙여서 캡슐화 했을 뿐이다.

```
a = A()
a.run_3turns()

# 결과
# 1: 0
# 2: 0
# 3: 0
# 1: 1
# 2: 1
# 3: 1
# 1: 2
# 2: 2
# 3: 2

```

~~약간 멍청함 기록 같은 느낌이지만...~~ 🙄 만약 더 좋은 방법이 생각나면 추가하겠습니다.
