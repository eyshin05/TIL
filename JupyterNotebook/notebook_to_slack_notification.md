# 노트북에서 코드 돌아가면 슬랙으로 알림받기

## Slack WebHooks integration 설정
http://zeddios.tistory.com/123

## 개요
위 링크를 따라서 설정하게 되면 curl 로 알림을 보낼 수 있다. 나의 경우에는 내 본인 계정으로 DM이 오게 설정해두었다.

노트북에서 코드가 다 돌아가고 나서, 혹은 exception이 났을 때 알림을 받고 싶다면 이를 응용해서 실행할 수 있다(있을 것이다... 아직 해 보지는 않았음).

## 코드
```
!curl -s -d "payload={\"text\":\"running code end!\"}" "WEBHOOK_URL"
```

노트북에서 앞에 느낌표를 달면 bash script 가 실행된다.

비슷한 방법으로 만약 코드의 top 상황을 3시간마다 알고 싶다면 아래의 코드를 터미널에서 사용할 수 있다.

```
while true; do 
  text=$(top -bn1 | head -n 20); 
  curl -s -d "payload={\"text\":\"server top message:\n$text\"}" "webHook URL"; sleep 10800; 
done
```
