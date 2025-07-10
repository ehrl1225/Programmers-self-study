# Git-flow 브랜치

## feature
기능 개발 브랜치

## develop
개발 중인 코드가 모이는 곳

## release
배포 준비 단계
배포할 코드가 모이는 곳

## hotfix
배포된 코드 이슈를 긴급 대응할 때 생성

## main
고정 브랜치
최신 배포 코드
언제 배포하든 문제가 없어야 함

## 흐름
main -> develop -> feature -> ... ->feature -> develop -> develop(안한 feature들) -> release -> main

## hotfix의 경우
main -> hotfix -> hotfix -> main

# 언제 사용하는가?
- 버저닝이 필요한
- 정기 배포
따라서 앱 애플리케이션에 적합

