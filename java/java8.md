# Modern Java

## Function Interface
- `Abstract Method`가 하나인 인터페이스 
- 람다식 사용 가능 
- 람다의 타입도 `Functional Interface`다. 

## Function 
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

## Consumer

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

## Predicate
```java
Predicate<Integer> isPositive = i -> i > 0;
```
abstract 메소드가 test 있다. 결과값은 항상 boolean Function<T, R>
```java
isPositive.test(num)
```