2011년 GitHub CIO인 Scott Chacon의 제안

워크플로우를 단순화 해야한다.

# 브랜치
## main

## feature

## 흐름
main -> feature -> feature -> main
필요하면 feature 브랜치에서 feature 브랜치를 만들면 된다.

# 정책
main 브랜치는 언제든지 배포 가능
모든 브랜치는 main 브랜치에서 파생
local 브랜치에서 commit 정기적으로 remote 브랜치로 push
도움이 필요하거나 코드 병합할 준비되면 pull request 생성
다른 사람이 변경된 코드를 승인하면 main 브랜치에 merge

이는 상시 배포에 적합
