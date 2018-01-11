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