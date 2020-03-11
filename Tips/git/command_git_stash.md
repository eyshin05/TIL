# Git Stash

작업중인 코드이거나 하는 이유로 아직 commit 하기 어려운데 git pull 을 받아야 하는 경우, git stash 로 문제를 해결할 수 있다.

> Stash 명령을 사용하면 워킹 디렉토리에서 수정한 파일만 저장한다. Stash는 Modified이면서 Tracked 상태인 파일과 Staging Area에 있는 파일들을 보관해두는 장소다. 아직 끝나지 않은 수정사항을 스택에 잠시 저장했다가 나중에 다시 적용할 수 있다.

출처: https://git-scm.com/book/ko/v1/Git-도구-Stashing


## 사용법

간단하게 `git stash` 하면 하던 작업들이 stashing 되고, `git stash apply` 를 하면 다시 되돌려준다.


## stashpull

```git config alias.stashpull '!git stash && git pull && git stash apply && git stash drop stash@{0}'```

이렇게 설정해두면 한번에 stash & pull 을 할 수 있다고 한다. (해 보지는 않았다)


## 참고 사이트

1. https://git-scm.com/book/ko/v1/Git-도구-Stashing
