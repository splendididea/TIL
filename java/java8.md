# Modern Java

[Kevin](https://github.com/Kevin-Lee)님의 [모던 자바 못다한 이야기](https://github.com/Kevin-Lee/modern-java-untold) 강좌를 보고 정리

## 함수형 인터페티스(Functional Interface)
- `Abstract Method`가 하나인 인터페이스 
- 람다식 사용 가능 
- 람다의 타입도 `Functional Interface`다. 
- `@Functional Interface`어노테이션으로 특정한다. abstract method는 하나여야 한다. 

람다의 타입에 해당하는 `Functional Interface` 결국 해당 오브젝트가 생성되어야 하는데 메소드를 남겨놓고는 오브젝트 생성을 못 시키기 때문에 람다를 쓰려면 꼭 `Single Abstract Method(SAM)`이어야 한다. 

## 대표적인 함수형 인터페이스 
### Function 
R apply(T t) 하나의 타입을 다른 타입으로 바꾼다.
```java
Function<String, Integer> toInt = new Function<String, Integer>() {
        @Override
        public Integer apply(String value) {
            return Integer.parseInt(value);
        }
};
```

```java
Function<String, Integer> toInt = value -> Integer.parseInt(value);
```

### Consumer

```java
final Consumer<String> print = new Consumer<String>() {
        @Override
        public void accept(String value) {
            System.out.println(value);
        }
};
```

```java
final Consumer<String> print = (value) -> System.out.println(value);
```

### Predicate
```java
Predicate<Integer> isPositive = i -> i > 0;
```
abstract 메소드가 test 있다. 결과값은 항상 boolean Function<T, R>
```java
isPositive.test(num)
```

### Supplier 
인자는 받지 않고 리턴 타입만 존재하는 메서드를 갖고 있다. 
```java
Supplier<String> s = () -> "hello World";
```