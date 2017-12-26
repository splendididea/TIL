# Webpack 
Webpack은 모던 자바스크립트 애플리케이션 개발을 위한 모듈러, 모듈과 모듈이 사용하는 정적 파일(CSS, Image)
## Webpack 장점 
- 초기 로딩 타임을 줄인다. 
- 정적 자원들까지 모듈화가 가능
- Babel,Typescript 등과 같은 트랜스파일러와 손쉽게 통합 
- HMR(Hot Module Replacement)를 지원하기 때문에 코드 수정될 때마다 자동으로 번들링을 수행하고 페이지 갱신 
- 다양한 로더(loader)가 제공 
- 다양한 플러그인 제공 

## Webpack의 기본 골격 
``` javascript 
webpack = require('webpack'); 
module.exports = [
    entry : {

    },
    output : {

    },
    module : {
        rules : [

        ]
    },
    plugins : [

    ]
]
```
- entry : 처음 로드하는 파일을 지정 
- output : 번들링된 결과물의 출력 방법을 지정 
- module : 프로젝트 내부에서 사용하는 다양한 유형의 모듈을 수행하는 방법 지정 