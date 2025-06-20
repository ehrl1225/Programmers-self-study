일단 최신화를 해야하고

```bash
sudo apt update -y
sudo apt upgrade -y
```

필수 패키지 설치하고

```bash
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```

Docker GPG키 & 저장소 추가

```bash
curl -fsSL <https://download.docker.com/linux/ubuntu/gpg> | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] <https://download.docker.com/linux/ubuntu> $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Docker 패키지 목록 업데이트 하고

```bash
sudo apt update -y
```

docker를 설치한다.

```bash
sudo apt install -y docker-ce docker-ce-cli containerd.io
```

User 계정에 Docker 권한을 추가하고

```bash
sudo usermod -aG docker $USER
```

Docker를 실행시키면 된다.

```bash
sudo service docker start
```

```bash
docker pull mariadb:latest
```

로 최신 버전 MariaDB를 설치할 수 있고

```bash
docker run --name mariadb -p 3306:3306 -e MYSQL_ROOT_PASSWORD=pw_mariadb -d mariadb:latest
```

로 MariaDB가 설치된 도커 컨테이너가 생성된다.

```bash
echo "docker start mariadb" > start
chmod +x start
echo "docker exec -it mariadb /bin/bash" > connect
chmod +x connect
echo "docker stop mariadb" > stop
chmod +x stop
```

대충 이걸로 mariadb 컨테이너를 실행시키거나 접속하거나 정지시키거나 하는 파일을 만들었다.

WSL2 도 VM이고 docker은 WSL2 안에 있으니까 VM 안에 있는 VM인데 호스트 컴퓨터인 windows에서 WSL2 안에 있는 docker의 mariadb에 연결되는 걸 보면 신기하다.

wsl2에 mariaDB를 설치한 Docker를 실행시키고
윈도우에서 3306 포트로 접속을 하니까 접속이 되었음

