# 잡다한 linux tips

그때그때 찾아보면 되긴 하지만 한번 정리해두면 기억에 오래 남아 TIL 에 정리해본다.

### 외장 HDD mount
`fdisk -l` 해서 외장하드가 무엇인지 확인한다. 안 뜰때에는 USB를 뒤쪽 메인보드 USB 슬롯에 꽂았는지 확인한다. 파티션 이름 (예를 들면 `/dev/sdc1` 등 뒤에 숫자 붙은거) 을 확인하여, 빈 dir 를 만든 다음에 거기에 mount 한다.

```
mkdir tempdisk
mount /dev/sdc1 tempdisk
```
모든게 다 끝나고 mount 해제 할 때에는 `umount /dev/sdc1`, 또는 해당 폴더만 mount 해제 할때에는 `umount tempdisk` 한 다음 `rmdir tempdisk` 하자.


### cp options
`cp` 야 그냥 copy 할때 항상 쓰는 명령어지만, 유용한 옵션들이 몇개 있다.

* `cp -p` 을 쓰면 옮길 때 파일 update 시점이 파일을 옮기는 시점이 아니라 이전에 파일이 update 된 시점을 유지할 수 있다.
* `cp -n` 하면 옮기는 위치에 동일한 이름의 파일이 존재하지 않을 때에만 옮길 수 있다. copy if file not exist.
