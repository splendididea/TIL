# JPA 맛보기 
---

## 1. JPA 개요 
기존의 JDBC등을 이용해서 직접 구현했던 데이터페이스 관련 작업을 대신 처리해 주는 추상화된 계층의 구현 스펙 

JPA는 그 자체로는 그냥 스펙에 불과하기 때문에 실제로 구현한 제품이나 프레임워크들의 존재가 필수 

JPA 사용의 장점 
- 데이터베이스 관련 코드에 대해 유연함을 얻을 수 있다. 
- 데이터베이스와 독립적 관계가 된다.

JPA 사용의 단점 
- 학습곡선(learning curve)가 크다. 
- 근본적인 객체지향 설계 사상이 반영되야 한다. 
- 특정 데이터베이스의 강력함을 활용할 수 없다.

## 2. 엔티티(Entity) 와 엔티티 매니저(Entity Manager)
### 2.1 엔티티
엔티니는 데이터 베이스상에서 데이터로 관리되는 대상을 의미, 데이터 베이스는 엔티티를 위해 일반적으로 테이블을 설계하고 데이터를 추가한다. 
이렇게 추가된 데이터는 `인스턴스`혹은 `레코드`라는 용어로 호칭된다. 

***Note** 회원 정보를 기록하는 엔티티를 만든다면 Member는 `엔티티 타입` 
아이디나,이름,연락처 같은 정보들은 `인스턴스`이다.*

하나의 엔티티 타입을 만든다라는 의미는 하나의 클래스를 작성한다는 의미와 같다. 

### 2.2 엔티티매니저
엔티티매니저는 말그대로 엔티티 객체를 관리하는 역할을 한다. 관리는 `life cycle`을 관리한다고 보면된다. 엔티티매니저는 자신이 관리해야 하는 엔티티 객체들을 `영속 컨텍스트(Persistence Context)`라는 곳에 넣어두고, 객체들의 생사를 관리 

### 2.3 영속 컨텍스트(Persistence Context)와 엔티티 객체 
영속 컨텍스트는 JPA가 엔티티 객체들을 모아두는 공간이라고 이해할 수 있다. 컨텍스트라는 용어는 하나의 공간이나 울타리같은 개념으로 이해하면 된다. 

1. **New(비영속)** : Java객체만 존재 데이터베이스와 연동된 적이 없는 상태 엔티티매니저의 관리하에 있는것이 아니라 순수한 Java 객체 
2. **Managed(영속)** : 데이터베이스에도 저장되고 메모리상에도 같은 상태로 존재하는 상태 객체는 영속 컨텍스트 내에 들어가게되고 id(PK) 값을 통해서 엔티티 객체를 꺼내 사용할 수 있다. 
3. **Removed(삭제)** : 데이터베이스상에서 삭제된 상태, 객체는 더 이상 영속 컨텍스트에 존재하지 않는다. 
4. **Detached(준영속)** : 영속 컨텍스트에서 엔티티 객체를 꺼내서 사용하는 상태, 아직 데이터 베이스와 동기화가 이루어 지지 않은 상태 


### 2.4 Spring Data JPA
Spring Data JPA는 동적으로 인터페이스 클래스를 만들어 내는 장식(동적 프록시, Dynamic Proxy)를 이용해서 실제 클래스를 작성하지 않아도 자동으로 만들기 때문에 별도의 코드를 작성할 필요가 없다. 

### 2.5 DataSource 설정 
- application.properties 파일에 필요한 구성을 설정 
- @Bean과 같은 어노테이션을 이용해 Java코드를 통해 구성 
- YAML 파일로 구성  
- XML 파일로 구성

### 2.6 JPA를 위한 어노테이션 추가 

#### 2.6.1 Id 어노테이션
어노테이션 | 설명 
-------- | --------
@Id|각 엔티티를 구별할 수 있도록 식별 ID를 가지게 설계
@Entity | 해당 클래스의 인스턴스들이 엔티티임을 명시 

#### 2.6.2 @Column 어노테이션 
Attribute | Type | 설명 | default
-------- | ------| --- | ---
name |String|컬럼 이름|
unique |boolean|유니크 여부|true,false
nullable|boolean|null 여부|true,false
insertable|boolena|insert여부|true,false
updatable|boolean|수정 가능 여부|true,false
table|String|테이블 이름|
length|int|컬럼 사이즈|255
precision|int|소수 정밀도| 0
scale|int|소수점 이하 자리수 |0

#### 2.6.3 @Table 어노테이션 
Attribute | Type | 설명 | default
-------- | ------| --- | ---
name |String|컬럼 이름|
catalog|String|테이블 카테고리
schema|String|테이블 스키마
uniqueConstraints|UniqueConstraint[]|컬럼값 유니크 제약 조건 
indexes|index[]|인덱스 생성

클래스 선언부에는 반드시 @Entity가 설정 되어야 한다. 
**@Id**는 가장 중요한 어노테이션으로 주로 `@GeneratedValue` 식별키 생성 전략을 지정한다. 
- AUTO 특정 데이터베이스에 맞게 자동으로 생성되는 방식 
- IDENTITY 기본 키 생성 방식 자체를 데이터베이스에 위임하는 방식, 데이터베이스에 의존적인 방식 MySql에 주로 많이 사용
- SEQUENCE 데이터 베이스의 시퀀스를 이용해서 식별키 생성 
- TABLE 별도의 키를 생성해주는 채번 테이블 

### 2.7 종속적인 엔티티의 영속성 전이에 대한 설정 
- **All**    : 모든 변경에 대한 전이 
- **PERSIST** :  저장 시에만 전이
- **MERGE** :  병합시에만 전이
- **REMOVE**  :  삭제 시에만 전이 
- **REFRESH** : 엔티티 매니저의 refresh() 호출 시 전이
- **DETACH**  :  부모 엔티티가 detach되면 자식 엔티티 역시 detach
```java
@OneToMany(cascade = CascadeType.ALL)
@JoinColumn(name="userno")
private List<Class> classes;
```