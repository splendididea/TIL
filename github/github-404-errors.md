# SourceTree remote repository clone시 404에러 처리 방법

`github`에 등록해 놓은 `repository`를 clone 하려했는데 404에러 발생
``` zsh
$ git clone https://github.com/splendididea/TIL.git
Cloning into 'TIL'...
fatal: unable to access 'https://github.com/splendididea/TIL.git/': Received HTTP code 404 from proxy after CONNECT
```
네트워크 > Git / Mercurial에 프록시 서버 설정 추가 체크 해제 