# 스프링 부트 시작하기 


초기 세팅은 *[스프링 설정 사이트](https://start.spring.io)* 에서 프로젝트에 맞게 설정 한다. 

> 스프링 부트의 장점 
- 자동화된 라이브러리 관리 : maven, gradle 사용 
- Spring Boot Auto Configure(자동 설정) 
- 적당한 라이브러리 자동 결정과 XML 없는 환경 구축 
- 테스트 환경과 내장 Tomcat 

> 스프링 부트는 component-scan 설정을 해 줄 필요가 없다. 
@ComponentScan 어노태이션을 사용한다. 

```java
@SpringBootApplication
@ComponentScan(basePackages = {"com.test"})
public class SpringbootApplication {

	public static void main(String[] args) {
		SpringApplication.run(SpringbootApplication.class, args);
	}
}
```

