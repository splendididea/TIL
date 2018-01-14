# 페이징 처리

페이징 처리를 위해 넘기는 파라미터
- 페이지 관련 
    - 페이지 번호 
    - 페이징당 사이즈

- 검색관련 
    - 검색 종류(type)
    - 검색 키워드(keyword)

---
## PageableDefault를 이용한 페이지 처리

Controller 메소드 작성시 파라미터로 PageableDefault인자를 전달한다. 
```java
@GetMapping("/list")
public void list(@PageableDefault(direction=Sort.Direction.DESC, sort="bno", size=10, page=0) Pageable page){
}
```
위처럼 PageableDefault를 사용하고 호출시 파라미터로 인자값을 넘기면 간단하게 페이징 처리를 할 수 있다. 

## PageVO를 작성하는 방식 
PageableDefault의 단점
- 페이지 번호가 0부터 시작하여 직관적이지 못하다
- 고의적으로 size값을 늘리는것을 막을 수 없다.
- 브라우저에서 전달되는 값에 의해 조절이 가능하므로 공격에 취약하다. 

