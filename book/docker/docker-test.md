# Docker 테스트 

NGINX container로 테스트를 진행한다. 
## image, container 다운 및 실행
```bash
docker image pull nginx
docker container run -d --name nginx-test -p 8080:80 nginx
```
nginx를 받아서 실행시킨다. localhost:8080 으로 서비스 확인이 가능하다.

## image, container 중지 및 삭제 
```bash
docker container stop nginx-test
docker container rm nginx-test
docker image rm nginx
```
container는 실행할 때 만든 name으로 중지 및 삭제한다. 
image는 다운받은 이미지 이름으로 지운다. 