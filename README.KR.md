# 자체 서명된 HTTPS 로컬 깃티 서버

[English](./README.md)

## 도대체 왜??

- 와이 낫? 😎

## 실행 방법

### 1. 자체 서명된 OpenSSL 인증서 생성

- 터미널에서 해당 프로젝트 경로로 이동 후 아래 명령어 실행
  
```bash
cd <path-to-project-directory>
docker run --rm -v "$(pwd)/certs:/certs" -it alpine/openssl req -x509 -newkey rsa:4096 -keyout /certs/localhost.key -out /certs/localhost.crt -days 365 -nodes -subj "/C=US/ST=YourState/L=YourCity/O=YourOrganization/CN=localhost"
```

*주의사항: 해당 인증서는 365일간 유효하다. 365일 후에는  **반드시** 새로 생성하여야 한다.*

### 2. `.env` 파일 작성하기

- `.env.example`을 기반으로 `.env` 파일을 생성&작성한다. 

### 3.docker-compose.yml 파일 실행하기

- 아래 명령어를 실행한다.

```bash
docker compose up -d
```

### 4. 깃티 사이트 접속하기

- 서버가 제대로 설치되었다면 [여기](https://localhost:8003), 혹은 https://YOUR_LOCAL_IP:PORT 에서 접속 가능하다.

*주의사항: http 가 아닌 https를 주소에 써야한다.*