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
