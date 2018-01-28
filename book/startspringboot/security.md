# Spring Security

스프링 시큐리티는 기본적으로 필터 기반으로 동작한다. 
## 로그인/로그아웃 처리
```java
@Override
protected void configure(HttpSecure http) throws Exception {
    http.authorizeRequests().antMatchers("/guest/**").permitAll();
    http.authorizeRequests().antMatchers("/manager/**").hasRole("MANAGER");
}
```

`authorizeRequests()`는 시큐리티 처리에서 `HttpServletRequest`를 이용한다는 것을 의미
`antMatchers`는 특정한 경로를 지정한다. 
