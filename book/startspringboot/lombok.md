# Lombok 어노테이션 
Lombok을 사용하면 어노테이션만으로 코드가 컴파일될 때 추가 코드를 만들 수 있다. 

어노테이션 | 설명
------- | ---
@NonNull |  Null값이 될 수 없다는 명시 
@Cleanup | 자동으로 close() 메소드 호출
@Getter/Setter | 컴파일 시점에 setter/getter 새성
@ToString | toString() 메소드 생성
@EqualsAndHashCode | 객체의 equals와 hashCode 생성
@NoArgsConstructor| 파라미터 없는 생성자를 만듬
@RequireArgsContstructor | 지정된 속성에 대해서만 생성자를 만듬
@AllArgsConstructor | 모든 속성에 대하여 생성자를 만듬 
@Data | Bean 클래스 등록
@Value | 불변 클래스를 생성할 때 사용
@Log | 자동으로 생기는 log라는 변수를 이용해서 로그사용
@Builder |  빌더 패턴을 사용할 수 있도록 코드 생성 
@SneakyThrows | 예외 발생 시 Throwable 타입으로 변환

> Note @Data 어노테이션은 정말 편리하지만 [ORM]에서 주의를 해야한다. 
부모 객체와 자식객체가 toString으로 서로를 호출하면 무한 루프에 빠진다. 
번거롭더라도 @Setter @Getter 필요한 어노테이션을 직접 사용하는게 안전하다. 


[ORM]:객체와 객체가 관계를 가지는 조합의 형태,테이블 간의 연관관계 
