# Node-js6와 ES2015 소개

## let and const Keywords 
- let : block 단위 변수
- const : 변하지 않는 상수

과거 `javascript` 경우는 변수 스코프가 함수 단위였다. 하지만 
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


## Arrow Function 
ES2015에서 부터 제공되는 Arrow Function은 function함수 문법을 보다 간결하게 변화 시켰다. 
```javascript
// without Arrow Function
const numbers = [1,2,3,4,5];
const even = numbers.filter(function(x){
    return x%2 === 0;
})
```

```javascript
//with arrow function
const numbers = [1,2,3,4,5];
const even = numbers.filter( x => x%2 ===0 );
```
> Note: `Arrow Function`은 `lexical scope`를 가지고 있다. `arrow function`에서 this는 부모 block의 this를 의미

```javascript
function DelayedGreeter(name) {
    this.name = name;
}

DelayedGreeter.prototype.greet = function(){
    setTimeout( function cb(){
        console.log('Hello' + this.name);
    }, 500);
}

const greeter = new DelayGreeter('World');
greeter.greet();   
```
Hello undefined를 print한다. 

Arrow Function에서는 
```javascript
DelayedGreeter.prototype.greet = function() {
    setTimeout( () => console.log('Hello' + this. name), 500);
}
```
Hello World를 print 한다. 


