# git init
``` shell
git init
```

# git clone
처음으로 원격 저장소에서 로컬 저장소로 불러올 때 사용함

# git push
원격 저장소로 코드 동기화

# git pull
리포지토리 불러오는데 사용 가능
최신화 하는데 사용함
원격 저장소에 변경된 코드를 가져온다.

# git add
파일을 tracked로 전환한다.

# git reset
파일을 untracked로 전환한다.

# git fetch
로컬에 원격 트래킹 저장소 갱신한다.
로컬 코드에 변화를 주지 않는다.

# git commit
코드 변경사항을 기록하는 단위
여러 개의 파일에 여러 라인을 수정하더라도 하나로 묶을 수 있다.
commit 단위마다 메세지 입력이 가능하다.


# git checkout
해당 커밋으로 이동한다.

# git merge
Branch를 병합하는 명령어다.

```
git merge --squach
```


# git rebase
브랜치가 참조하는 Commit 기준점을 변경하는 명령어

# git log
git의 히스토리를 확인 가능하다.

# origin 설정
```shell
git remote add origin [url]
```

