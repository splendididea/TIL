# 인덱스 처리
댓글 목록과 같은 데이터의 경우 특정 게시물 번호에 영향을 받기 때문에 게시물 번호에 대한 인덱스를 걸어놓으면 데이터가 많을 때 성능의 향상을 기대할 수 있다. 

```java
@Table(name = "tbl_board" , indexes = {@Index(unique=false,
                                columnList="board_bno")})
public class BoardReply{

}
```
@Table에는 인덱스를 설계 할 때 @Index와 같이 상요해서 테이블 생성 시에 인덱스가 설계되도록 지정 할 수 있다. 