# Stream
Lazy Iterator

## Intermediate Operation Method
Stream을 리턴하므로 계속 Method Chainig을 통해서 무엇을 해야할지 스트림에게 지시할 수 있다. 

## Terminal Operation Method 


```java
IntStream.of(1,2,3,4,5)
                .filter(i-> i>3)
                .map(i -> i * 3)
                .findFirst();
```

## Stream Static Method 

### of 
Array로 부터 Stream을 만드는 메소드
```java
Stream.of(1,2,3,4,5)
```

### filter 
`Functional Interface`인 `Predicate` 를 인자로 받아서 `element`를 제어할 수 있다. 
```java
Stream.of(1,2,3,4,5)
      .filter(i -> i > 3)
```

### map
`Functional Interface`인 `Function` 를 인자로 받아서 `element`를 제어할 수 있다. 
```java
Stream.of(1,2,3,4,5)
      .filter(i -> i > 3)
      .map(i -> i * 3)
```

### collect

collect는 다양한 인자를 받아서 해당 리턴 타입으로 데이터를 담는다. 

대표적 인자 
- toList()
- toSet()
- joining()

```java
Stream.of(1,2,3,4,5)
      .filter( i -> i > 3 )
      .map(i -> i * 3 )
      .collect(toList())
```

toSet()을 사용하면 기존 set처럼 순서를 보장하지 않고 중복값을 허용하지 않는다. toSet을 사용한것 처럼 중복값을 허용하지 않으면서 순서를 보장하고 싶다면
```java
Stream.of(1,2,3,4,5)
      .distinct()
      .collect(toList())
```
먼저 distinct를 호출하고 collect한다. 
