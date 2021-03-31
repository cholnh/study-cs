## 스프링
- [의존 관계 (Dependency)](#의존-관계-dependency)
- [의존성 주입 (Dependency Injection)](#의존성-주입-dependency-injection)
- [제어 반전 (Inversion of control)](#제어-반전-inversion-of-control)
- [의존 관계 역전 원칙 (from SOLID)](#의존-관계-역전-원칙-from-solid)
- [AOP](#aop)

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

**강 결합 방식 설계 (좋지 않은 설계 방식)**
|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/ioc1.jpg"/>|
|-|
|그림 1|

- 상위 모듈에서 하위 모듈을 관리한다. (제어권이 상위 모듈에 있음)

<br/>

**문제점**

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/ioc2.jpg"/>|
|-|
|그림 2|

- 상위 모듈에서 하위 모듈을 관리하면 Coupling(결합도)가 증가하여 모듈화가 어려워진다.

<br/>

**Inversion of control 으로 해결**

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/ioc3.jpg"/>|
|-|
|그림 3|

- IoC 컨테이너에 의해 객체가 생성되고 관리, 주입된다.

<br/>

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/ioc4.jpg"/>|
|-|
|그림 4|

- 의존 관계(=제어권, control)가 역전(Inversion)되어, 상위 모듈은 하위 모듈로 부터 자유로워진다. (결합력이 감소되었으므로)  

<br/>

[ [← back](https://github.com/cholnh/study-cs#-스프링-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/spring/index.md#스프링) ]

<br/>

## 의존 관계 역전 원칙 (from SOLID)

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/dip1.jpg" width="700"/>|
|-|
|그림 1|

**문제**
- 이렇게 고수준 모듈이 저수준 모듈을 의존하고, 저수준 모듈이 다시 고수준 모듈을 의존하는 것을 **의존성 부패(Dependency Rot)** 라고 한다.  
- 또한 지나친 의존관계는 많은 변경 포인를 유발한다.

<br/>

**지나친 의존 관계**
|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/dip2.png" width="700"/>|
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
    |<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/dip3.png" width="700"/>|
    |-|
    |그림 3|
    
    
2. 모듈 모두 다른 추상화된 것에 의존해야 한다. 추상화 된 것은 구체적인 것에 의존하면 안 된다.
    |<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/dip4.png" width="700"/>|
    |-|
    |그림 4|
    
3. 구체적인 것이 추상화된 것에 의존해야 한다.
    |<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/dip5.png" width="700"/>|
    |-|
    |그림 5|
    
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

관점 지향 프로그래밍 방법론으로, 관심사를 나눠(SoC) 모듈성을 증가시키는 것이 목적인 프로그래밍 패러다임이다.

**관심사를 왜 나눌까?**  
- 인간의 인지능력은 한계가 있다. (한 번에 생각할 수 있는 양에 한계가 있음)
- 모든 소프트웨어 개발의 핵심은 복잡성을 극복하는 것이다.
- 즉, 한 번에 여러가지를 동시에 신경 쓰면 복잡하니깐, 각각을 따로 분리해서 생각하자는 이야기.
 
<br/>

**관점에 따라 나눠보기**
- Primary(core) Concern
    + 주 업무 관심 (비지니스 로직)
- Cross-cutting Concern
    + 횡단 관심
    + 로깅, 보안처리, 트랜잭션처리 등..

여기서 `Concern` 은 관심사를 의미한다.  
대략적인 도식화는 다음과 같다.

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/aop1.jpg" width="700"/>|
|-|
|그림 1|

<br/>

스프링을 `Proxy` 기반의 AOP를 제공한다.  
조금 더 자세한 함수 호출 방식은 다음과 같다.

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/aop2.jpg" width="700"/>|
|-|
|그림 2|

<br/>

**스프링 프록시 자세하게 알아보기**
- 스프링은 프록시 기반의 AOP를 제공하며, 이를 구현하기 위해 `Java Dynamic Proxy` 또는 `Cglib` 사용.
- `AopProxy` 라는 `Delegator` 인터페이스로 표현.
    + Dynamic proxy 기반은 `JdkDynamicAopProxy` 클래스
    + Cglib 기반은 `CglibAopProxy` 클래스
    + cf) `DefaultAopProxyFactory` 를 이용해 즉시 사용 가능한 구현체 생성 가능.  
        `createAopProxy()` 메서드를 통해 AopProxy 실 구현체 생성.
        + AOP 적용 대상이 인터페이스 or 인터페이스를 구현 -> `JdkDynamicAopProxy` 생성됨.
        + else -> `ObjenesisCglibAopProxy` 기반 실 객체가 생성됨.
        + cf) `Objenesis` 는 과거 Cglib 단점을 해결해 주는 라이브러리이다.
-  Dynamic proxy 기반과 Cglib 기반은 **프록시 객체 생성 방식** 에 차이가 있다.
    + Dynamic proxy 기반은 프록시 객체 생성을 위해 인터페이스 **필수** 구현.
    + Cglib 기반은 인터페이스를 **구현하지 않은 일반 클래스** 에 런타임 시 **코드 조작으로 프록시 객체를 생성**.
- 스프링 AOP 가 제공하는 프록시 기반 방식은 **런타임 위빙(RTW)** 방식이다.
    + 프로그램 구동 중에 위빙(코드 삽입)이 일어남.
    + 반면, AspectJ 는 컴파일 위빙(CTW) or 로드 타임 위빙(LTW) 이용. (런타임 위빙보다 성능이 우세)
    + AspectJ는 기본 스프링 AOP 보다 다양한 포인트컷 지원.
- Transaction 대상의 경우 기본적으로 Cglib 으로 생성 됨.
    + 성능상 Cglib 우세, 예외발생 확률도 적음.
    + Cglib 기존 문제점(생성자 중복 호출, default 생성자 필요 문제 등)을 `Objenesis` 라이브러리가 해결.
- AspectJ 를 사용하기 위해서는 AJC 등 별도의 컴파일러 설정 필요하나 스프링 AOP는 그렇지 않음. (성능도 크게 체감하기 힘들다고 함)


**Bean을 Proxy로**
스프링에서 Bean 으로 등록된(=BeanDefinition에 사전 정의된) 객체는 IoC 컨테이너에서 관리된다.  
Bean 객체에 대해 스프링 AOP는 어떻게 Proxy를 생성하고 관리할까? 

|<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/question/spring/aop3.jpg" width="700"/>|
|-|
|그림 3|

<br/>

**Bean 후처리기**
- 스프링은 자동 Proxy 생성을 위해 `DefaultAdvisorAutoProxyCreator` 클래스를 Bean 후처리기에 등록하여 사용한다.
    + Advisor 를 이용한 자동 프록시 생성기이다.
    + Bean 객체 일부를 `Proxy` 로 포장하고, `Proxy` 를 Bean 대신 IoC 컨테이너에 등록한다.  
1. 스프링은 Bean 생성 마다 후처리기에 전달.
2. 후처리기는 Bean 으로 등록된 모든 Advisor 내 PointCut 을 이용하여 전달받은 Bean이 프록시 적용 대상인지 확인.
3. 내장된 Proxy 생성기를 통해 Bean 에 대한 `Proxy` 생성, Advisor 연결.
4. 전달 받은 Bean 대신 `Proxy` 를 Ioc 컨테이너에 등록 시킴.
5. 컨테이너는 Bean 후처리기가 돌려준 `Proxy` 를 Bean 으로 등록.

<br/>

[ [← back](https://github.com/cholnh/study-cs#-스프링-) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/question/spring/index.md#스프링) ]