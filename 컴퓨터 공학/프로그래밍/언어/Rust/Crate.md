러스트 코드 파일들의 모음으로 외부의 크레이트를 불러올 수 있다.

Cargo.toml 파일의 \[dependencies\] 밑에 크레이트 이름을 작성해서 불러올 수 있고
build를 하면 Cargo.lcok에 기록하는데
다음에 빌드를 할 때는 Cargo.lock의 파일이 존재하므로 
Cargo.lock의 파일을 읽어서 그 내용을 바탕으로 빌드한다.

따라서 Cargo.toml의 파일들을 수정하고 업데이트 하려면
```shell
cargo update
```
를 통해 할 수 있다.
