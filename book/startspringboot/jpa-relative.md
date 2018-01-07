# 다양한 연관관계 처리 
데이터 베이스를 설계하는 것처럼 JPA의 경우도 객체 간의 상호 연관관계 처리가 가장 중요 

## 1.연관관계 처리의 순서와 사전 설계 
1. 필요한 각각의 클래스를 정의 
2. 각 클래스의 연관관계에 대한 설정 추가 
    - 일대다, 다대다 등의 연관관계 설정
    - 단방향, 양방향 설정 
3. 데이터베이스상에 원하는 형태의 테이블이 만들어지는지 확인 
4. 테스트 코드를 통해서 정상 동작하는지 확인 

### 1.1 관계형 데이터베이의 설계와 JPA 
1. 가장 중심이 되는 사람이나 명사를 결정, 이에 대한 구조를 대략적으로 설계
2. 1에서 생성된 데이터들이 상호작용을 하면서 만들어내는 새로운 데이터를 정의 
3. 1, 2를 다시 세분화해서 설계
