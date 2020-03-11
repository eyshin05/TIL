# jupyter notebook 에서 STDOUT 을 바로 파일에 쓰기

파일입출력을 필요하면 쓰긴 하지만 그냥 상황을 보기 위해 코드를 짜다보면 모든 정보를 print 문으로 적기 마련이고, 이걸 일일히 file write 로 고쳐주기가 귀찮을 때도 있다.

혹시 stdout 을 file pointer 로 바꾸는 방법이 없나 찾아봤더니 있었다...


```
import sys
file = open('file', 'w')

sys.stdout, backup = file, sys.stdout

print('test')

sys.stdout = backup
file.close()
```

이렇게 해 주면 print 한 test 가 화면에 표시되지 않고 파일에 적힌다.

sys.stdout 은 참고로 `ipykernel.iostream.OutStream` object ...

출처: https://stackoverflow.com/questions/4675728/redirect-stdout-to-a-file-in-python
