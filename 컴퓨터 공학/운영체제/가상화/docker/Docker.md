개발된 환경을 이미지로 저장하고
이미지를 DockerHub에 올릴 수 있고
이미지 여러 개를 함께 연결 되어서 동작하게 설정된 상태를 명령어 텍스트나 문서 형태로 저장이 가능하다.
이 환경을 컨테이너라는 독립된 공간에 저장한다.
가상 머신은 물리적 자원을 지정해서 분할해 사용해서 성능에 한계가 있는데
도커는 실행 환경만 독립적으로 돌려서 자원의 제한으로 부터 자유롭다.

Dockerfile에서 실행될 스크립트를 작성할 수 있다.

Container Engine을 통해서 Container를 돌리고
운영체제를 돌리지 않기에 가볍다.

# Dockerfile
- 어떤 파일을 사용할 지
- 어떤 라이브러리를 설치해야 하는지
- 어떤 환경 변수를 설정해야하는지
- 어떻게 실행해야하는지 스크립트
를 설정할 수 있다.

# Image
어플리케이션을 실행하는데 필요한 코드, 설정, 에셋, 라이브러리를 포함한 것으로
스냅샷이라고 보면 된다.
수정은 불가능하다.

# Container
이미지를 독립된 공간에서 실행시킬 수 있는 것을 의미한다.
Container에서는 수정이 가능하다.

# 배포
Container Registry에 Push를 하면 다른 컴퓨터가 PULL 해서 받아 올 수 있다.

## 공개
- docker hub
- red hat quay.io
- github packages

## 비공개
- aws
- google cloud
- microsoft azure

# 빌드
예시로
```shell
docker build -f Dockerfile -t fun-docker .
```
이걸로 현재 위치의 Dockerfile을 읽어서 fun-docker라는 이름으로 빌드하는 것이다.
