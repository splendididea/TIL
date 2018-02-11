# Node-js6와 ES2015 소개

## let and const Keywords 
- let : block 단위 변수
- const : 변하지 않는 상수

과거 javascirpt의 경우는 변수 스코프가 함수 단위였다. 하지만 
es6 문법의 let은 block 단위로 변수를 제어한다. 
```javascript
if(false){
    var x = 'hello';
}
console.log(x);
```
위와 같이 작성을 하면 undefined가 출력되고 이런 코드는 많은 문제를 야기했다. 
```javascript
if(false){
    let x = "hello";
}
console.log(x);
```
반면 `es6`에서 바뀐 문법인 `let`을 다른 `block`에서 사용해서 `let`을 사용하면 
`ReferenceError : x is not defined` 오류를 낸다. 
