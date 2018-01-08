# JPA Join 

순수 SQL을 이용하면 처리 가능한 INNER JOIN이나 OUTER JOIN, 서브쿼리 등을 쉽게 처리할 수 있으나 JPA를 이용하면 많은 제약이 따른다. 

해결책으로는 @Query를 이용해서 Native SQL을 그대로 이용하는것이 가능하지만 
이 경우에는 데이터 베이스에 종속되어 버린다. 

JPA에는 Fetch Join이라는 기법을 통해서 SQL에 조인을 처리하는 것과 유사한 작업을 처리할 수 있다. SQL대신 JPQL을 이용해서 처리한다고 생각하면 된다. 

``` java
public interface UserRepository extends CrudRepository<User, String> {
    @Query("SELECT u.userid, count(c) FROM User u 
    OUTER JOIN Class c ON u.userid = c.user 
    WHERE u.userid = ?1 GROUP BY u ")
    List<Object[]> getUserWithClassCount(String userid);
}
```
@Query 안의 JPQL의 경우 SQL과 유사하지만 테이블 대신 엔티티 클래스를 이용한다. 

메소드 리턴타입은 List<Object[]>로 처리된다. JPQL에서는 엔티티 타입뿐 아니라 다른 자료형도 반환할수 있기 때문이다.

> Note : Spring boot 1.5.4 버전은 hibernate-core-5.0.12 버전을 사용한다. 5.2 부터 @Query에 on 조건이 사용가능해졌으므로 에러가 난다. 
