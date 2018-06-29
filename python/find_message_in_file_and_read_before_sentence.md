# 파일을 다 읽지 않으면서 이전 문장 가져오기

파이썬의 mmap 모듈을 사용할 수 있다는 것을 알았다.

```python
import mmap

with open(filename, 'rb', 0) as file, \
    mmap.mmap(file.fileno(), 0, access=mmap.ACCESS_READ) as s:
        
    index = s.find('\n테스트\n'.encode())
    s.seek(s.rfind('\n'.encode(), 0, index-3)+1)
    print(s.readline().decode().strip())
```

### 설명
* mmap 를 이용하면 텍스트 파일을 byte 로 접근할 수 있다.
* 찾으려는 메시지 `'\n테스트\n'` 의 byte `.encode()` 를 mmap class instance 에서 찾아서
* 그 위치 직전의 메시지 구분자 (여기선 개행문자) 를 찾고
* 그 사이 byte 를 가져와서 decoding 하면 된다.
