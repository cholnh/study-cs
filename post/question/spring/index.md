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

## 의존성 주입 (Dependency Injection)

IoC 컨테이너가 BeanDefinition(xml, annotation 으로 명시된)정보를 바탕으로 클래스간 **'의존관계를 자동으로 연결(=주입)'** 하는 것.  
- 객체 레퍼런스를 IoC 컨테이너로 부터 주입 받아서, 실행 시에 **'동적으로 의존관계'** 가 생성.
- 코드가 단순해지고, 컴포넌트간 결합도가 낮아짐.  

<br/>

**주입 유형**
1. 메서드를 통한 주입
    + 의존성을 입력 받는 일반 메서드를 통해 의존성을 주입 받음.
2. setter를 통한 주입
    + 의존성을 입력 받는 `setter` 메서드를 통해 의존성을 주입 받음.
3. 생성자를 통한 주입
    + 의존성을 포함하는 클래스 생성자를 통해 의존성을 주입 받음.
    
<br/>

**Bean Factory**  
Spring DI 컨테이너가 관리하는 객체를 빈(Bean)이라 하며, 이 빈을 관리한다는 의미로 해당 컨테이너를 빈 팩토리(Bean Factory)라 부른다.
- 객체의 생성, 객체 사이의 런타임 관계를 DI 관점에서 볼 때는 컨테이너를 `Bean Factory`라 한다.
- `Bean Factory`에 여러 컨테이너 기능을 추가하여 `ApplicationContext` 라고 부른다.
    + Bean Factory
        + 빈 등록, 생성, 조회, 반환을 관리
        + `getBean()` 메서드 정의되어 있음
        + 보통 확장된 `ApplicationContext`으로 사용
    + ApplicationContext
        + 빈 팩토리 기능을 이어받아 사용
        + 스프링이 제공하는 `ApplicationContext` 구현 클래스가 여러가지 있음
        + StaticApplicationContext, GenericXmlApplicationContext, WebApplicationContext 등...

> 애플리케이션 컨텍스트는 BeanDefinition으로 만들어진 메타정보를 담은 오브젝트를 사용해 IoC와 DI 작업을 수행한다.
        
|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/di1.png" width="500"/>|
|-|
|그림 1|

<br/>

**BeanDefinition 인터페이스 정의**  
IoC 컨테이너가 사용하는 빈 메타정보는 대략 다음과 같다.

- **빈아이디, 이름, 별칭** : 빈오브젝트를 구분 할 수 있는 식별자
- **클래스 또는 클래스 이름** : 빈으로 만들 POJO 클래스 또는 서비스 클래스 정보
- **스코프** : 싱글톤, 프로토타입과 같은 빈의 생성 방식과 존재 범위
- **프로퍼티 값 또는 참조** : DI에 사용할 프로퍼티 이름과 값 또는 참조하는 빈의 이름
- **생성자 파라미터 값 또는 참조** : DI에 사용할 생성자 파라미터 이름과 값 또는 참조할 빈의 이름
- **지연된 로딩 여부, 우선 빈 여부, 자동와이어링 여부, 부모 빈 정보, 빈팩토리 이름** 등

> 빈은 오브젝트 단위로 등록되고 만들어지기 때문에 같은 클래스 타입이더라도 하나 이상의 빈으로 등록할 수 있다.

<br/>

[ [← back](https://github.com/cholnh/study-cs#-스프링-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/spring/index.md#스프링) ]

<br/>

## 제어 반전 (Inversion of control)

스프링 프레임워크를 실행하면 IoC 컨테이너에서 DI(BeanDefinition에 사전 정의된 Bean 의존성 주입)가 수행 된다.  
이렇게 IoC 컨테이너에서 하위 모듈을 관리하고 주입시켜주면 상위 모듈은 제어권이 없어지게 된다.  
기존 상위 모듈에서 하위 모듈 방향으로 이어지던 제어권이, IoC 컨테이너를 통해 역전 되었다고 하여 Inversion of control 이라 한다.  

**강 결합 방식 설계**

**문제점**

**Inversion of control 으로 해결**


[ [← back](https://github.com/cholnh/study-cs#-스프링-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/spring/index.md#스프링) ]

<br/>

## 의존 관계 역전 원칙 (from SOLID)

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/dip1.jpg"/>|
|-|
|그림 1|

**문제**
- 이렇게 고수준 모듈이 저수준 모듈을 의존하고, 저수준 모듈이 다시 고수준 모듈을 의존하는 것을 **의존성 부패(Dependency Rot)** 라고 한다.  
- 또한 지나친 의존관계는 많은 변경 포인를 유발한다.

<br/>

**지나친 의존 관계**
|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/dip2.png"/>|
|-|
|그림 2|

<br/>

**확장에 유연하지 못함**
```java
@RequestMapping(value = "/payments", method = RequestMethod.POST)
public void pay(PaymentRequest req){
    if (req.getType() == CardType.SHINHAN) {
        shinhanCardPaymentService.pay(req);
    } 
    else if (req.getType() == CardType.WOORI) {
        wooriCardPaymentService.pay(req);
    }
    ...
    // 이런 반복적인 if 구조는 리팩터링 대상일 확률이 높다..
}
```

**해결**
- 의존 관계 역전 원칙 : DIP (Dependency Inversion Principle)

> " 고차원 모듈은 저차원 모듈에 의존하면 안된다. 이 모듈 모두 다른 추상화된 것에 의존해야 한다.  
    추상화 된 것은 구체적인 것에 의존하면 안 된다. 구체적인 것이 추상화된 것에 의존해야 한다. "
    
1. 고차원 모듈에 존재하는 저차원 모듈 의존을 끊는다.
    <img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/dip3.png"/>
    
2. 모듈 모두 다른 추상화된 것에 의존해야 한다. 추상화 된 것은 구체적인 것에 의존하면 안 된다.
    <img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/dip4.png"/>
    
3. 구체적인 것이 추상화된 것에 의존해야 한다.
    <img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/dip5.png"/>
    
<br/>

- 의존성 부패가 발생한 코드는 class들이 전부 엉켜있어 재사용이 불가능하다. (가독성, 유지보수성 모두 떨어짐)
- 목 객체로 대체될 수도 없으며, 단위 테스트도 불가능한 경우가 대부분이다.

<br/>

**의존성이 역전된 코드**

```java
class PaymentController {
    @RequestMapping(value = "/payments", method = RequestMethod.POST)
    public void pay(PaymentRequest req) {
        final PaymentService paymentService = paymentFactory.getType(req.getType());
        paymentService.pay(req);
    }
}

public interface PaymentService {
    void pay(PaymentRequest req);
}

public class ShinhanPaymentService implements PaymentService {
    @Override
    public void pay(PaymentRequest req) {
        shinhanApi.pay(req);
    }
}
```

> " 또한 확장에는 열려있고 변경에는 닫혀있는 **'OCP'** 를 준수하게 된다. "

[ [← back](https://github.com/cholnh/study-cs#-스프링-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/spring/index.md#스프링) ]

<br/>

### AOP

[ [← back](https://github.com/cholnh/study-cs#-스프링-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/spring/index.md#스프링) ]