# java.lang 패키지

java lang 패키지는 import를 하지 않고 바로 사용할 수 있다. 최상위 클래스인 Object 역시 java.lang 패키지이다. 
lang 패키지에는 기본형타입을 객체로 변환시킬 때 사용하는 Wrapper클래스가 있다. 

## Wrapper 클래스
- Boolean
- Byte
- Short
- Integer
- Long
- Float
- Double

문자열과 관련된 String, StringBuffer, StringBuilder 와 System,Math,Thread와 관련된 중요 클래스 역시 lang 패키지안에 있다. 

### 오토박싱(Auto Boxing),오토 언박싱(Auto Unboxing)
기본형의 데이터를 객체형 `Wrapper`클래스로 담을 수 있다. 그렇게 담는 경우 `오토박싱`이 되었다고 한다. 반대로 Wrapper 클래스를 기본형에 담는경우 `오토언박싱`이 되었다고 한다. 
```java
Integer i1 = 5; // 오토박싱
int i2 = i1;    // 오토 언박싱 
```







