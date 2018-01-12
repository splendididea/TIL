# Linux 에서 http/https post 호출 방법 
Http/Https Post 호출 하려면 wget을 사용한다. 
get:
```bash
wget http://example.com
```
post:
```bash
wget --post-data "username=Yarkee" http://example.com
```
[stackoverflow](https://stackoverflow.com/questions/15711841/how-to-make-http-https-post-requests-manually)
