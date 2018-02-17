# 돔 추상화의 내부 

## 리액트의 이벤트 


## DOM 이벤트 리스너 
HTML은 이해하기 쉬은 이벤트 처리 API를 제공하나 이 API는 전역 스코프를 오염시키며 메모리 누수의 원인이 된다. 

onTouchStart|onTouchMove|onTouchEnd|onTouchCancel| 
---|---|---|---|---|
onTouchStart|onDoubleClick|onMouse


## React 진행 방식 
리액트의 컴포넌트는 this.state 안에 여러 데이터를 가질 수 있다. this.state는 특정 컴포넌트 전용, this.setState()를 호출해 변경 할 수 있다. 

> NOTE: 상태가 업데이트 되면 컴포넌트의 반응형 렌더링이 트리거되고 해당 컴포넌트와 그 자식이 다시 렌더링된다. 리액트는 가상 DOM을 이용하므로 이 작업이 아주 빠르게 수행된다. 

## JSX와 HTML의 비교 
---
### JSX와 HTML의 차이 
- 태그 특성은 낙타 표기법으로 작성
- 모든 요소는 짝이 맞아야 한다. 
- 특성 이름이 HTML언어 사양이 아닌 DOM API에 기반을 둔다. 

### JSX의 특이점 

#### 단일 루트 로드 
리액트 컴포넌트는 단일 루트 노드만 렌더링 할 수 있다. 
```javascript
reutrn(
    <h1>hello World</h1>
)
```
위의 return문은 다음과 같이 변환된다.  
```javascript
return React.createElement("h1", null, "Hello World");
```
하지만 아래 코드는 유효하지 않다. 
```javascript
return(
    <h1>hello World</h1>
    <h2>Have a nice Day<h2>
)
```
이것은 javascript의 속성이다. return문은 단일 값만 리턴하는데 위 코드는 두 값을 리턴하려고 한다.(React.createElement를 두번 호출)
해결책은 간단핟. 모든 반환값을 루트 객체 하나에 매핑하면 된다. 
```javascript
return(
    <div>
        <h1>hello World</h1>
        <h2>Have a nice Day<h2>
    </div>
)
```
```javascript
return React.createElement("div", null, React.createElement('h1', null, 'Hello World'),
                                         React.createElement('h2', null, 'Hello World'));
```
단일 값만 반환이 가능하다. 

### 조건 절
JSX의 특성상 javascript로 변환되는 과정에서 if절은 사용할 수 없다. 하지만 두가지 대체 방법이 있다. 
- 삼항식 사용
- 조건을 밖으로 이동 
---
#### 삼항식 사용
```javascript
render() {
    return(
        <div className={condition ? "salutation" : "" }>
            hello JSX
        </div>
    )
}
```
위 코드는 아래와 같이 수정된다.
```javascript
React.createElement("div", {className: condition ? "salutation" , ""  }, "Hello JSX");
```

#### 조건을 밖으로 이동
```javascript
render() {
    let className = "";
    if(condition){
        className = "salutation"      
    }
    return(
        <div className={className}>
            Hello JSX
        </div>
    )
}
```
### JSX의 주석
```javascript
let content = {
    <Nav>
        {/* 자식 주석이므로 {}로 감싼다. */}
        <Product 
            /*
                다중 
                행 
                주석
            */
            name={window.isLoggedIn ? window.name : '' } // 행 끝 주석
        />
    </Nav>
}
```

### 동적 HTML렌더링
리액트는 XSS 공격 방지 기능을 기본적으로 내장 HTML 태그를 동적으로 생성하고 JSX에 추가하는 작업을 기본적으로 금지 
이 설정은 보안을 위해 바람직 하지만 HTML을 동적으로 생성해야 하는 경우도 있다. 그런 경우 XSS 보호 기능을 끄고 모든 
내용을 곧바로 렌더링 하는 dangerouselySetInnerHTML 속성을 제공 

### 마크다운 렌더링 

마크다운 렌더링을 위해 marked 라이브러리를 사용한다. 

---
## JSX를 배제하고 리액트 사용 
일반 자바스크립트로 리액트 요소 만들기 

```javascript
let child1 = React.createElement('li', null, 'First Text Content');
let child2 = React.createElement('li', null, 'Second Text Content');
let root = React.createElement('ul',{ className: 'my-list'}, child1, child2 );
React.reder(root, document.getElementById('example'));
```
## 요소 팩토리 

```javascript
React.DOM.form({className: "component"}, 
                React.DOM.input({type:'text', placeholder: 'Name'})
                React.DOM.input({type:'text', placeholder: 'Comment'})
                React.DOM.input({type:'submit', placeholder: 'Post'})
                )
```

JSX와 구조 분해 할당을 통해 좀 더 깔끔하게 구문을 작성할 수 있다. 
```javascript
import React, {Component} from 'react';
import {render} from 'react-dom';

    let {
        form, 
        input
    } = React.DOM

    class CommentForm extends Component {
        render(){
            return form({className: "commentForm"},
                input({type:'text', placeholder: 'Name'})
                input({type:'text', placeholder: 'Comment'})
                input({type:'submit', placeholder: 'Post'})
            )
        }
    }
```

## 커스텀 팩토리 
커스텀 컴포넌트를 위한 팩토리를 만들 수 있다. 
```javascript
let Factory = React.createFactory(ComponentClass);

let root = Factory({custom:'prop'});
render(root, document.getElementById('example'));
```

## 인라인 스타일링 
리액트는 자바스크립트를 이용한 인라인 스타일링을 지원한다. 
- 셀렉터 없이 스타일의 범위 지정 가능
- 특정성 충돌이 예방됨
- 소스 순서에 관계가 없음 

## 인라인 스타일 정의 
리액트 컴포넌트에서는 인라인 스타일을 자바스크립트 객체로 지정한다. 
스타일 이름은 DOM속성과 일관성을 위해 낙타 표기법을 적용해 지정한다.(예: node.style.backgroundImage)


## ref
리액트 컴포넌트는 렌더링 할 때 항상 가상 DOM을 대상으로 작업한다. 

