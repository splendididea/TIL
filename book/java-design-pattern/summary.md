# Chapter1 MVC 패턴

MVC = Model + View + ch01.Controller

객체 지향 언어를 이용한 프로그램 설계에서는 필요한 기능을 열거하고 View, ch01.Controller, Model에 역할을 하는 각각의 클래스로 나눈것이 가장
핵심 개념이다. 각각의 역할을 맡은 클래스들은 독립적으로 동작하는것이 아니라 상호 연관을 맺으면서 프로그램의 목적한 바를 수행 한다. 
이때 서로의 연관 관계를 최소화시키는것이 관건이다. 

따라서 클래스는 Model, ch01.Controller, View는 각각의 역할을 하나만 담당하며 자신을 노출 시킬 수 있는 추상 계층(Abstract Layer)[^1] 를 선언한다.
클래스는 추상 계층을 통해 자신을 노출하고 클래스를 필요홀 하는 곳 또한 추상 계층을 통해 참조하게 되므로, 추상계층의 실제 구현부가 변경, 수정된다 하더라도
이 변경 내용이 서로에게 영향을 주지는 않는다. 즉 추상 계층을 통해 서로의 관계가 **연약(Loose Coupling)** 하게 된다.

## 1. Model
자바에서 모델은 다음과 같이 3가지로 나누어진다.
- Java Bean : GUI Component
- JSP Bean : 이 장에서 우리가 사용 할 것
- Enterprise Java Bean : 분산 환경에 사용하는 자바 컴포넌트 기술

우리가 만들 JSP Bean은 실질적인 비즈니스 로직을 담는 클래스, Model에 해당하며 이 클래스에 비즈니스 프로세스를 처리할 수 있는
역할만 부여하고 View라 할 수 있는 프레젠테이션(Presentation) 영역과 컨트롤러의 역할을 내포시키지 않았다면 Web뿐 아니라
일반 애플리케이션 또는 다른 시스템에서도 사용 할 수 있다.


# Chapter02 Factory Method 패턴
> 객체 생성은 의뢰하자!


## 2.1 객체 생성
자바에서는 객체를 생성하려면 먼저 클래스가 있어야 한다. 클래스는 템플릿이 필요하고 객체가 생성되는 것
> Object is a instance of class(객체는 클래스의 인스턴스이다.)

객체는 템플릿으로서 추상화 작업에 의해 선언된 데이터 타입인 클래스에 구체적인 구현 예가 되는 것으로 다음 처럼
new라는 키워드를 이용해 생성되어야 한다.

```java
Database db = new Database();
```

### 2.1.1 일상적인 객체 생성
자바를 이용한 database프로그램을 수행하려면 절차가 필요하다.
1. 필요한 드라이버 로딩
2. 데이터베이스 서버에 접근
3. 계정 인증을 통한 Connection 객체 생성

JDBC Driver는 사용하고자 하는 데이터베이스 벤더로부터 얻어와 자바 가상 머신이 드라이버를 인지할 수 있도록
Classpath를 잡아주면 된다.

```java

public class Database {

    String server = "127.0.0.1";

    public Database(){
        
    }
}

```

## ch03. 객체지향

### 3.1 추상화란?
객체지향의 3가지 특징
- 상속성(Inheritance)
- 은닉성(Encapsulation)
- 추상화(Abstraction)

#### 3.1.1 메소드 중복 정의(Overloading)
메소드의 이름은 같으나 파라미터의 개수와 타입이 일치하지 않는 것을 의미 메소드의
반환형(Return type)은 관심의 대상이 아니다. 이러한 중복 정의의 대표적인 예가 print()메소드이다.

#### 3.1.2 메소드 재정의(Overriding)
```java
public class Shape{
    public void draw();
}
```
위와 같이 클래스를 생성하면 클래스 구현부(body)가 없다는 에러 메시지를 볼 수 있다. 
```java
public abstract class Shape{
    public abstract void draw();
}
```
추상 클래스를 만들려면 추상화 클래스와 추상화 메서드가 존재해야 한다.
```java
public class ShapeDraw{
    public static void main(String[] args){
      Shape shape = new Shape();
    }
}
``` 
위의 클래스를 컴파일 할 경우 에러가 발생한다. 에러 원인은 Shape 클래스는 추상화 클래스이므로 객체를 생성할 수 없다. 

```java
public class Triangle extends Shape {
    public void methodA(){
        System.out.println("nothing");
    }
}
```
위의 클래스 역시 컴파일 에러가 발생한다. Triangle 클래스 역시 추상 클래스로 선언이 되어야한다. 왜냐하면 상속받은 Shape 클래스에 존재하는 
추상 메서드 draw() 가 있기 때문에 추상클래스로 선언을 해야한다. 

앞서 본바와 같이 추상 클래스는 객체를 생성할 수 없었기에 Triangle 클래스 역시 객체를 생성 할 수 없다. 

정리 
1. 구현부가 없는 메소드는 추상 메소드로 선언해야 한다. 
2. 추상 메서드를 가진 클래스는 추상 클래스로 선언되야 한다. 
3. 추상화된 속성은 상속된다. 
4. 추상 클래스로는 객체를 생성할 수 없다. 

그렇다면 추상 클래스로 객체를 만드려면 어떻게 해야하는가? 

간단하다 추상 클래스를 구현하는 구현 클래스를 만들고 추상 클래스의 추상 메서드를 재정의 해서 해당 클래스를 통해 객체를 생성 하면 된다. 

```java
public class Triagle extends Shape{
    public void draw(){
        System.out.println("triangle drawing");
    }
    public void methodA(){
        System.out.println("nothing");
    }
}
```

이렇게 Traingle 클래스에서 draw()를 재정의 함으로써 객체 생성이 가능한 클래스로서 아무런 하자가 없게 되었다.
1. 재정의(Overriding)의 전제 조건은 상속(Inheritance)이다. 
2. 추상 메서드를 가진 클래스는 추상 클래스로 선언되어야 한다. 
3. 추상 클래스로는 객체를 생성할 수 없다. 
4. 추상 클래스를 상속받은 클래스가 객체 생성이 가능한 클래스가 되려면 추상 메서드를 반드시 재정의 해야 한다. 
5. 추상 클래스의 자식 클래스들이 객체를 생성할 수 있다는 것은 추상 메서드를 재정의 했음을 의미한다. 

```java
public class ShapeDrwa{
    public static void main(String[] args){
      Triagle t = new Triagle();
      Circle c = new Circle();
      Rectangle r = new Rectangle();
      call(t);
      call(c);
      call(r);
    }
    
    public static void call(Shape s){
        s.draw();
    }
}
```
위의 코드의 동작방식
1. 메소드 이름 call을 찾는다. 
2. 메소드가 존재한다면 변수의 개수가 한개인 것을 찾는다. 
3. 변수가 1개인 것중 Triangle 타입인 것을 찾는다. 
4. Triangle 타입이 있다면 해당 메소드가 호출되겟지만 그렇지 않다면 
5. 자동으로 `승급(Promotion)`이 발생하여 Triangle의 부모 클래스 타입(Shape)을 변수로 하는 메서드가 있는지 확인
6. 부모 클래스 타입인 Shape를 변수로 하는 메서드가 없다면 Shape 클래스의 부모 클래스인 java.lang.Object를 변수로 하는 메서드가 있는지 확인
7. 발견한 메서드는 호출되고 찾지 못하면 해당 메서드가 없다는 에러를 발생시킨다. 

**클래스들 사이의 관계에서 앞의 예제 처럼 부모-자식 간의 관계가 성립할 때, 즉 상속 관계로 묶이게 될 때 부모 클래스(상위 클래스) 타입으로
메소드 변수를 전달할 수 있는 이러한 특징을 `다형적 변수(Polymorphic Parameter)`라고 불린다.**

#### Heterogenous
```java
Shape []s = new Shape[3];
s[0] = new Triangle();
s[1] = new Circle();
s[2] = new Rectangle();
```
이처럼 Shape배열에 Shape 타입의 객체를 보관할 수 있는 다형성의 특징을 Heterogeneous Collection이라고 한다. 
Triangle - Rectangle - Circle 간에는 어떠한 관계도 갖지 않는다. 

#### 3.1.3 또 다른 추상화: 인터페이스 
자바는 단일 상속만을 지원한다. 이런 단일 상속 때문에 발생할 수 있는 문제는 인터페이스(Interface)로 해결할 수 있다. 
인터페이스 안에는 오로지 추상메서드만 존재할 수 있다. 일반적으로 추상 클래스를 사용하기 보다는 인터페이스를 사용한다. 

#### extends vs implements 
클래스를 상속받을 때는 extends 키워드를 사용한다. 이렇게 되면 부모클래스와 자식클래스는 is a 또는 is type of 라는 표현으로 이들 관계를 설명한다. 


#### 3.1.4 추상화는 언제 사용하는가? 
인터페이스와 추상 클래스의 공통점은 추상 메서드를 가지고 있다는것과 이들을 상속받은 혹은 구현하는 클래스가 객체 생성이 가능한 형태가 되려면 모두 
이 추상 메서드를 재정의해서 갖고 있어야 한다는 것. 

 
[^1]: 클래스에 대한 명세를 선언한 것으로 실제 구현은 되어있지 않음을 뜻함