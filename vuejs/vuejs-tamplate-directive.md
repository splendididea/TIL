# Vue JS 기본 템플릿과 디렉티브 정리

## 1. Vue-cli 템플릿
- simple
- browserify
- broserrify-simple
- webpack
- webpack-simple
- pwa 
- etc ..


### 2 기본 디렉티브 

#### 2.1 v-text, v-html 디렉티브 
- v-text, {{}} : innerText 속성에 연결됨, 태그 문자열을 html 인코딩 하여 나타내기 때문에 화면에는 태그 문자열이 그대로 노출 
- v-html : innerHTML 속성에 연결 태그 문자열을 파싱하여 화면에 나타냄 
> v-html은 XSS (Crossing Site Scripting) 공격에 취약 v-text 를 쓰는것이 더 안전 

#### 2.2 v-bind 디렉티브 
요소(Element)에 속성들을 바인딩한다. 
v-bind:value="message" v-bind:src="경로"
v-bind는 생략이 가능하다. 

#### 2.3 v-model 디렉티브 
양방향 데이터 바인딩이 필요한 경우 사용 
하나의 model 객체를 두 개의 Vue 객체가 참조할 수 도 있다. 

#### 2.4 v-show, v-if, v-else, v-else-if 디렉티브 
v-show 는 v-if와의 차이점은 v-if는 조건에 맞지 않으면 렌더링하지 않는다. 
하지만 v-show 는 일단 렌더링을 하고 display 스타일 속성으로 화면에 보여줄지 여부를 결정한다.

#### 2.5 반복 렌더링 디렉티브 v-for
데이터가 배열이거나 유사배열인 경우 data in datas, 객체인 경우 해시맵 구조이기 때문에 key로 value값을 구한다. 
index를 사용하려면 구성요소 구문에 index를 추가 
- 배열, 유사배열 : v-for="(data, index) in datas" 
- 객체의 경우 : v-for="(val, key, index) in datas"
> Note `v-for`디렉티브는 `v-if`디렉티브와 함께 사용할 경우 `v-for` 디렉티브가 먼저 적용된다.
여러 요소를 렌더링 할 경우 tamplate을 사용한다. 

#### 2.6 여러개 요소를 묶어 반복 렌더링 <template>
for문을 돌릴때 한 조건을 충족시키는 요소를 반복적으로 렌더링 시키고 싶은 경우 사용한다. 예를들어 table 구성 요소를 담는 for문 중간 5번째 글마다 특정 글을 삽입하고 싶다면 `<tamplate>`를 사용한다. 

