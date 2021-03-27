## 스프링
- [의존 관계 (Dependency)](#의존-관계-dependency)
- [제어 반전 (Inversion of control)](#제어-반전-inversion-of-control)
- [의존 관계 역전 원칙 (from SOLID)](#의존-관계-역전-원칙-from-solid)
- [의존성 주입 (Dependency Injection)](#의존성-주입-dependency-injection)

[ [← back](https://github.com/cholnh/study-cs#-스프링-) ]

## 의존 관계 (Dependency)

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/dependency1.jpg"/>|
|-|
|그림 1|

위 그림에서 **'`A Class`는 `B Service`를 의존'** 한다.  
(`A Class` 내부에서 `B Service`를 생성하거나, 멤버/로컬 변수로 사용하거나, B의 메서드를 호출하는 것들을 의미)  

```java
class A_Class {
    
    B_Service b_service;
    
    function() {
        ...
        b_service = new B_Service();
        b_service.doIt(3L);
        ...
    }
}

class B_Service {
    function(Long arg) {
        ...
    } 
}
```

<br/>

만약 `B Service`가 변경되면 `A Class` 내부에서 사용되는 로직중 `B Service`와 관련된 로직은 전부 변경되어야 함을 의미한다.  
즉 `A Class`는 **재사용하기 어렵다**. (= Component/Service가 될 수 없다)

> Component 란, 소스 코드의 아무런 수정 없이 **'재사용이 가능한'** 수준의 모듈  

[ [← back](https://github.com/cholnh/study-cs#-스프링-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/spring/index.md#스프링) ]

<br/>

## 제어 반전 (Inversion of control)


[ [← back](https://github.com/cholnh/study-cs#-스프링-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/spring/index.md#스프링) ]

<br/>

## 의존 관계 역전 원칙 (from SOLID)

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/dip1.jpg"/>|
|-|
|그림 1|

**문제**
- 이렇게 고수준 모듈이 저수준 모듈을 의존하고, 저수준 모듈이 다시 고수준 모듈을 의존하는 것을 **의존성 부패(Dependency Rot)** 라고 한다.  

**해결**
- 의존 관계 역전 원칙 : DIP (Dependency Inversion Principle)

> " 고차원 모듈은 저차원 모듈에 의존하면 안된다. 이 모듈 모두 다른 추상화된 것에 의존해야 한다.  
    추상화 된 것은 구체적인 것에 의존하면 안 된다. 구체적인 것이 추상화된 것에 의존해야 한다. "
    
1. 고차원 모듈은 저차원 모듈에 의존하면 안된다.
    + <img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/dip2.jpg"/>
2. 모듈 모두 다른 추상화된 것에 의존해야 한다. 
3. 추상화 된 것은 구체적인 것에 의존하면 안 된다.
4. 구체적인 것이 추상화된 것에 의존해야 한다.


[ [← back](https://github.com/cholnh/study-cs#-스프링-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/spring/index.md#스프링) ]

<br/>

## 의존성 주입 (Dependency Injection)

[ [← back](https://github.com/cholnh/study-cs#-스프링-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/spring/index.md#스프링) ]

<br/>

### AOP

[ [← back](https://github.com/cholnh/study-cs#-스프링-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/spring/index.md#스프링) ]