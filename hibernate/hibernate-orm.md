# 하이버 네이트 

하이버 네이트는 자바에서 쓸수있는 
orm 기술: orm기술은 datamodel을 object 모델로 맵핑하는 기술 

95%에 해당하는 persistence-related 업무를 줄여줄 수 있음 

hibernate 5.2는 최소 jdk 1.8 jdbc 4.2 이상 
hibernate 5.1은 최소 jdk 1.6 jdbc 4.0 이상을 요구 한다.

- SessionFactory 는 hibernate에 있다. 세션을 가져오거나 할 수 있 jpa의 


// Entity
@Entity(name = "Contact")

// value 타입 
@Embeddable
value 타입은 항상 어딘가에 의존한다. 단독으로 query가 될수 없고 독단적인 lifesycle 역시 없다. 
