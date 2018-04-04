# ECMAScript 6의 비구조화(Destructing)과 파라미터 핸들링(Parameter Handling)

## 비구조화(Destructing)

아래 예제 처럼에서 비구조화를 변수선언시 사용 할 수 있다. 
```javascript
let obj = { first: 'a', second: 'b' };
let {first: f, second: s} = obj;
```

## 1.1 조립(Constructing) vs 추출(Extracting)
```javascript
let obj = {};
obj.first = 'k';
obj.second = 't';
```
ECMAScript 6에서 비구조화는 데이터 추출과 같은 문법 사용이 가능하게 한다. 
```javascript
let obj = {first: 'k', second: 't'};
let {first: f, second: s} = obj;
```
Object literal은 다수의 properties를 동시에 만들수 있게 한다. 
```javascript
let [x, y] = ['a', 'b'];
```
