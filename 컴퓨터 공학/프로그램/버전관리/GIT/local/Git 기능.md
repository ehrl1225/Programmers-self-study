여기 적혀있는 기능은 [[Git 명령]]을 통해 사용 가능
# 로컬 저장소
개인 컴퓨터에 존재하는 저장소
원격 저장소 코드의 복제다.
로컬 저장소의 코드를 원격 저장소로 올린다.

# 원격 저장소
로컬 저장소가 바라보는 공유 저장소
별도의 서버로 관리한다.

# untracked
동기화 하지 않을 파일들이다.

# tracked
동기화할 파일들을 말한다.

# HEAD
코드를 바라보는 시점
이전 코드로 돌아갈 수 있다.

# Branch
Repository에 존재하는 분기
언제든 만들고 지우는 것이 가능하다.

# Merge
만든 Branch를 병합한다.

## Fast-Forwrad 병합
순차적 커밋에 맞춰 병합함
브랜치를 생성한 시점과 Merge 시점이 동일한 경우 사용

## 3-way 병합
공통 Branch A를 바탕으로 Branch B 생성
Branch A와 Branch B 각각 Commit 존재
갈래로 나온 시점인 Branch A를 기준으로
Branch A와 Branch B 변경 사항을 병합 시도

## Squach and Merge
여러 commit을 하나로 만든다.

# Conflict
동일한 라인을 수정하는 경우 코드 충돌이 발생한다.
대부분 Git이 해주지만 나머지는 

# Rebase
커밋 순서 재배열
브랜치를 만들고 시간이 지나 다시 병합하려 하면 충돌이 발생할 수 있음
그래서 브랜치를 만들고 시간이 지나 base 브랜치에 rebase를 하고나서
merge를 하면 충돌이 발생하지 않음
브랜치가 참조하는 Commit의 기준점을 변경하는거임

# 커밋 취소
## Revert
새로운 commit을 생성한다.
특정 commit 변경사항을 취소하고 취소한 변경 사항을 반영하는 commit을 생성한다.

## Reset
이전 commit 상태로 돌아가고 이후 commit은 제거된다.

### soft reset
파일을 변경하진 않고 이전 기록은 새로운 브랜치로 만든다.

# 그 외 기능
# Cherry-pick
브랜치 commit 일부를 HEAD로 바라보는 branch에 적용한다.
자주 안쓰임

# Stash
코드의 변경 사항을 commit하지 않고 임시 저장

# submodule
Git Repository를 다른 Git Repository에 포함시키는 기능

