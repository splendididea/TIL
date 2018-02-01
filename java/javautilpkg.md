# Java Util 

## Date 
기존에 Java가 제공하는 Date, Time은 여러가지 문제점이 있었다. JDK Java SE 8 부터 변경된 Api를 제공한다. 
- 오브젝트 factory 메서드를 사용한다. 
- 오브젝트 자기 자신의 특정 요소를 가지고 오브젝트를 생성할 경우 of메서드를 호출하면 되고, 다른 타입으로 변경할 경우 from 메서드를 호출 한다. 
```java
LocalDateTime time = LocalDateTime.now();

LocalDate localDate = LocalDate.of(2018,Month.DECEMBER,12);
LocalTime localTime = LocalTime.of(17,18);
```


