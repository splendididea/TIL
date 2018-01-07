# Java Class Design

## 접근 제어자
접근 제어자는 Java Entity(a class, method, or filed) 노출 레벨을 결정한다. 접근 제어자는 효과적인 캡슐화를 가능하게 한다. 
- **Public**
- **Private**
- **Protected**
- **Default** (접근 제어자를 설정하지 않은 경우)

---
## Public 접근 제어자 
Public 접근 제어자는 가장 liberal하다. 같은 패키지 내에서는 어디서나 접근이 가능하다.

## Private 접근 제어자 
다른 클래스에서 접근이 불가하다. 오직 같은 클래스의 멤버만이 접근이 가능하다. 

## Protected and Default 접근 제어자 
두 접근 제어자는 굉장히 유사하다. 같은 패키지 내에서 접근이 가능핟. protected는 자신을 상속받은 클래스에서 접근 가능함 

## 상속(Inheritance) 
![number_classess](../../img/number_classes.jpg)
## 다형성(Polymorphism)