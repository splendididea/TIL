# REST 방식 처리 
## REST 방식과 RestController 
- GET 정보를 보여주기 위한 목적으로 설계 하나의 고유한 데이터를 찾는 이름이나 태그가 된다. 
- POST 정보의 가공이 목적, 정확한 목적을 가지고 특정한 작업을 수행 



전송방식|역할
-------|---
GET|특정 리소스를 조회(read)
POST|특정 리소스를 생성하는 용도
PUT|특정 리소스를 수정
DELETE|특정 리소스를 삭제 

`명사`가 url의 구분이 되고, 전송 방식이 동사의 역할을 하게 된다. 

Spring MVC 에서는 REST방식의 설계와 사용을 위해 어노테이션을 제공한다. 
- `@RequestBody` 클라이언트가 보내는 `JSON`데이터의 수집 및 가공
- `@ResponseBody` 클라이언트에게 전송되는 데이터에 맞는 MIME 타입을 결정
- `@PathVaraible` URL의 경로에 포함된 정보 추출
- `@RestController` 컨트롤러의 모든 메소드 리턴 타입으로 `@ResponseBody`를 기본으로 지정
- `@JsonIgnore` 객체내의 json 데이터를 자동으로 변환 처리를 하다보면 lombok의 toString처럼 무한 반복되는 경우를 막기위해 json 변환처리를 막는다. 

