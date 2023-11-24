## 도커 설치하기

> 데비안 인스턴스 기준으로 설명 / 윈도우는 그냥 찾아서 설치하면 됨

-   터미널에서 아래 명령어 실행

```bash
sudo apt-get update -y &&
sudo apt-get install -y ca-certificates curl gnupg &&
sudo install -y -m 0755 -d /etc/apt/keyrings &&
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg &&
sudo chmod a+r /etc/apt/keyrings/docker.gpg &&
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null &&
sudo apt-get update -y
```

-   위 명령어 실행 후 아래 명령어 실행

```bash
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

-   설치 확인

```bash
docker -v
```

<br> <br>

## 프로젝트 실행

```bash
docker compose up --build
```

## 트러블 슈팅

-   환경변수를 찾을 수 없다는 오류 : `.env` 잘 있나 확인

-   볼륨을 연결할 수 없다는 오류 (No Such ~~)

VM 재부팅 후 아래 명령어 실행

```bash
docker system prune -af
docker compose down
```

-   npm 관련 에러
    -   특정 스크립트를 찾을 수 없는 경우 (ex. npm run) : `package.json` 인코딩 확인 (개행이 LF인지, 인코딩이 UTF-8이 맞는지)
