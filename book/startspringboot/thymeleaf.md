# Thymeleaf
## Thymeleaf을 이용해 개발에 필요한 리스트
- 별도의 라이버리 
- 추가 플러그인
- 자동 재시작 기능 

## 객체 화면의 출력 
동작방식은 EL과 굉장히 비슷 
```html
<h1 th:text="${vo}">Thymeleaf</h1>
```

## HTML 출력하기 - utext
```html
<div th:utext="${'<h3>'+vo.mid+'</h3>'"></div>
```

## 리스트를 화면에 출력 
루프의 처리는 `th:each`를 이용해서 처리할 수 있다. 리스트나 java.util.Iterable, java.util.Map, 배열 등을 사용 할 수 있다. 
- `index` 0부터 시작하는 인덱스 번호
- `count` 1부터 시작하는 번호
- `size` 현재 대상의 length 혹은 size
- `odd/even` 현재 번호의 홀수/짝수 여북
- `first/last` 처음 요소인지 마지막인지 요소 판단

## 지역변수의 선언, if ~unless 제어 처리 
- if unless는 if ~else 문과 비슷 아래와 깉이 사용한다. 
```html
<td th:if="${member.uid == target}">IF</td>
<td th:unless="${member.uid == target">UNLESS</td>
```

## 인라인 스타일 Thymeleaf 사용하기 
EL을 사용해서 자바스크립트 코드를 작성하는 방법을 Thymeleaf에서도 지원한다. `th:inline`을 사용해서 javascipt나 text를 지정해서 사용할 수 있다. 기본적으로 Thymeleaf의 inlining은 `text`로 지정된다. 
```html
<script th:inline="javascript">
    var result = [[${member.uid}]]
<script>
<td>[[${member.uid}]]</td>
```
## Thymeleaf 유틸리티 객체 

- Expression Basic Objects(표현식 기본 객체)
    - #ctx
    - #vars
    - #locale
    - #httpServletRequest
    - #httpSession
- Expression Utility Objects(표현식 유틸 객체)
    - #dates
    - #calendars
    - #numbers
    - #objects
    - #bools
    - #arrays
    - #lists
    - #sets
    - #maps
    - #aggregates
    - #messages

## Thymeleaf 링크 처리 
일반적인 웹 페이지의 링크는 크게 절대경로과 현재 url기준으로 이동하는 상대(context-relative)경로 2가지로 구분된다. 

스프링 부트에서는 프로젝트를 실행하면 `/`을 기준으로 동작하기 때문에 경로에 대한 스트레스 없이 작성 할수 있다. 하지만 특정경로에서 프로젝트가 실행하는 경우는 문제가 될수 있다. 

`Thymeleaf`는 이러한 문제를 해결하기 위해 `@{}`를 이용해 경로에 대한 처리를 자동으로 처리할 수 있다. 
```html
<li><a th:href="@{http://localhost:8080/sample}"></a></li>
<li><a th:href="@{/sample}"></a></li>
<li><a th:href="@{~/sample}"></a></li>
```
`@{/sample}`의 경우는 컨텍스트 경로가 반영된다. 

링크를 이용해서 파라미터를 전송 할 수도 있다. 
```html
<li><a th:href="@{/sample(p1='aaa',b='bbb')}"></a></li>
```

## Thymeleaf 레이아웃 기능 
`th:insert` `th:replace` `th:include`와 같은 속성들을 이용해서 기존 페이지의 일부분을 다른 내용으로 쉽게 변경할 수 있다. 

```html
<div th:fragement="header"></div>

<div th:fragement="footer"></div>
```

조각(fragement)을 만들어서 넣어줄 페이지에 넣어준다. 
```html
<div th:insert="~{fragement/header::header}"></div>

<div th:insert="~{fragement/footer:footer}"></div>
```


