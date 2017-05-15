# Using Queue
파이썬에서 queue 를 쓰려고 검색했을때 가장 먼저 나오는 라이브러리는 [Queue class](https://docs.python.org/2/library/queue.html) 인데, 읽어보면 알 수 있듯이 이건 syncronized queue class, 쓰레드나 멀티 프로세싱 등을 할때 데이터를 저장하는 용도로 쓰이는 class 이다. 흔히 생각하는 간단한 큐 클래스와는 조금 다르다.

그럼 큐를 사용하기 위해서는 어떻게 하면 좋을까? `list` 에 `insert(0, item)` & `pop()` 을 사용하면 구현할 수 있지만 insert 함수가 최적화가 되어 있을지 의문이었다. 잘 모르지만 리스트니까 별로 안 되어 있을것 같았다...

그래서 찾아보니 `collections.deque` 가 있다. [double ended queue](https://docs.python.org/3.5/library/collections.html#collections.deque) 이다. 여기서 `append(item)`, `popleft()` 를 쓰면 enqueue, dequeue 되는 것 같다.

참고로 stack 은 list 로 간단하게 구현할 수 있다... `append(item)`, `pop()` 하면 된다.
