# Docker로 어플리케이션 실행 

- Docker를 사용해서 Application 실행하기
- Docker build command 사용
- 멀티 컨테이너를 만들어 Application 실행하기 

## Docker Images
`Docker Image`는 libraries, binaries를 포함한 실행 가능한 application이다. Docker Image 안에 이러한 파일들은 read-only이므로 image안 content들은 바뀔 수 없다. 
만약 image안에 content를 바꾸고 싶다면 새로운 layer를 추가해야 한다. 

## Docker Container 
`docker engine`은 docker명령어들로 container를 시작, 종료, 재시작을 할 수 있다. 
사용자가 이 명령어들을 사용하면 Docker 엔진이 `SIGTERM(-15)`을 `container`가 안에서 돌고 있는 메인 프로세스에 보낸다. 

`SIGTERM`신호는 프로세스가 스스로 자연스럽게 종료되도록 요청한다.
대부분의 프로세스들은 이러한 signal을 제어하고 자연스럽게 종료되도록 돕는다. 
그러나 프로세스가 실패하면 Docker engine은 유예기간을 갖는다. 




