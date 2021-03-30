## 테스트 주도 개발로 배우는 객체지향 설계와 실천

<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/cs/tn-ttd-oop.png" width="250" />

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) ]

<br/>

<br/>

## Index
- [들어가면서](#들어가면서)
- 1부 [서론](#1부-서론)
    + 1장 [테스트 주도 개발의 핵심은 무엇인가?](#1장-테스트-주도-개발의-핵심은-무엇인가)
    + 2장 [객체를 활용한 테스트 주도 개발](#2장-객체를-활용한-테스트-주도-개발)
    + 3장 [도구 소개](#3장-도구-소개)
- 2부 [테스트 주도 개발 과정](#2부-테스트-주도-개발-과정)
    + 4장 [테스트 주도 주기 시작](#4장-테스트-주도-주기-시작)
    + 5장 [테스트 주도 개발 주기의 유지](#5장-테스트-주도-개발-주기의-유지)
    + 6장 [객체 지향 스타일](#6장-객체-지향-스타일)
    + 7장 [객체 지향 설계의 달성](#7장-객체-지향-설계의-달성)
    + 8장 [서드 파티 코드를 기반으로 한 개발](#8장-서드-파티-코드를-기반으로-한-개발)
- 3부 [동작하는 예제](#3부-동작하는-예제)
    + 9장 [경매 스나이퍼 개발 의뢰](#9장-경매-스나이퍼-개발-의뢰)
    + 10장 [동작하는 골격](#10장-동작하는-골격)
    + 11장 [첫 테스트 통과하기](#11장-첫-테스트-통과하기)
    + 12장 [입찰 준비](#12장-입찰-준비)
    + 13장 [스나이퍼가 입찰하다](#13장-스나이퍼가-입찰하다)
    + 14장 [스나이퍼가 경매에서 낙찰하다](#14장-스나이퍼가-경매에서-낙찰하다)
    + 15장 [실제 사용자 인터페이스를 향해](#15장-실제-사용자-인터페이스를-향해)
    + 16장 [여러 품목에 대한 스나이핑](#16장-여러-품목에-대한-스나이핑)
    + 17장 [Main 분석](#17장-Main-분석)
    + 18장 [세부 사항 처리](#18장-세부-사항-처리)
    + 19장 [실패 처리](#19장-실패-처리)
- 4부 [지속 가능한 테스트 주도 개발](#4부-지속-가능한-테스트-주도-개발)
    + 20장 [테스트에 귀 기울이기](#20장-테스트에-귀-기울이기)
    + 21장 [테스트 가독성](#21장-테스트-가독성)
    + 22장 [복잡한 테스트 데이터 만들기](#22장-복잡한-테스트-데이터-만들기)
    + 23장 [테스트 진단](#23장-테스트-진단)
    + 24장 [테스트 유연성](#24장-테스트-유연성)
- 5부 [고급 주제](#5부-고급-주제)
    + 25장 [영속성 테스트](#25장-영속성-테스트)
    + 26장 [단위 테스트와 스레드](#26장-단위-테스트와-스레드)
    + 27장 [비동기 코드 테스트](#27장-비동기-코드-테스트)
    
[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) ]

<br/>

<br/>

## 들어가면서

<br/>

> " 객체 지향 소프트웨어를 작성하는 최고의 방식, 즉 테스트 주도 개발을 다루는 실용적인 지침서. "

<br/>

> " 설계가 너무 경직돼 있거나 산만할 때 '테스트를 먼저 작성한다'는 절차는 이를 파악하는 데 도움된다. "

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

<br/>

## 1부 서론

<br/>

## 1장 테스트 주도 개발의 핵심은 무엇인가?

### 학습 과정으로서의 소프트 개발

- 프로젝트에는 미처 예상하지 못한 요소가 있게 마련이다.
- 갖가지 중요한 구성 요소가 조합된 시스템은 너무나도 복잡해서 개인이 해당 시스템의 모든 가능성을 이해하기는 어렵다.
- **'불확실한 변화를 예측하려면 경험이 늘어남에 따라 불확실성을 해결하는 데 도움이 될 프로세스가 필요하다.'**  

---

<br/>

### 피드백은 가장 기본적인 도구다

- 경험에 의거한 피드백
    + 팀에는 반복적인 확동 주기가 필요하다. 
    + 각 주기마다 양과 질에 관한 피드백을 받는다.
- 배포는 현실에서 자신이 내린 가정을 검사할 기회이며, 배포하지 않고는 피드백이 완전해지지 않는다.
- **'중첩된 고리형 시스템'** 으로 피드백 주기를 적용하라
    + 짝 프로그래밍, 단위 테스트, 인수 테스트, 일별 회의, 반복 주기, 출시 등...
    + 중첩된 각 고리마다 팀의 산출물이 경험에 의거한 피드백으로 드러나 팀에서는 오류나 오해를 발견하고 수정함.
    + 고리는 서로를 강화함 (안쪽에서 뭔가 모순되는 것이 바깥쪽에서 포착됨)
    + 안쪽 고리는 **'기술적 세부 사항'** 에 집중 (단위 코드의 역할, 시스템 나머지 부분과의 통합 여부)
    + 바깥쪽 고리는 **'조직과 팀'** 에 집중
- 피드백을 일찍 받을수록 좋다
- 점진적이고 반복적인 개발
    + 점진적인 개발에서는 모든 계층과 구성 요소를 구축한 다음 그것들을 마지막에 통합하는 대신 시스템을 **'기능별'** 로 구축.
    + 각 기능은 시스템 전 구간에 이르는 **'조각'** 으로 구현됨.
    + 시스템은 언제나 통합된 상태이며 배포할 준비가 되어 있음.
    + 반복적인 개발은 계속해서 충분한 상태에 이를 때까지 **'피드백에 응답'** 해 **'기능 구현'** 을 다듬는다.
    
---

<br/>

### 변화를 돕는 실천법

- 시스템 규모를 점진적으로 키우고, 늘 일어나는 예상치 못한 변화에 대처하기 위해 필요한 두 가지
    + 회귀 오류를 잡아줄 꾸준한 테스트 작성, 테스트 자동화
    + 단순한 코드 유지 (리팩터링)
- 코드를 작성하기 전에 테스트를 작성한다.
    + 테스트를 **'설계 활동'** 으로 바꾼다.
    + 테스트를 사용해 **'코드에서 하고 싶은 바'** 에 관한 생각을 명확하게 한다. ('물리적인 설계', '논리적인 설계'의 분리)
    + 깔끔하고 모듈화된 코드가 생성됨.
    + 빠른 품질 피드백

<br/>

> " 코드 변경에 대한 **'자신감'** 을 주는 자동화된 회귀 테스트라는 안전망을 구축할 수 있다. "

---

<br/>

### 테스트 주도 개발 간단 정리

**TDD 핵심 주기**
1. 테스트 작성
2. 동작하는 코드 작성
3. 리팩터링

<br/>

**TDD 혜택**
- 다음 작업에 대한 인수 조건이 명확해짐. (자신이 테스트 코드를 작성하니까 당연함..)
- 느슨한 구성 요소로 단계별 테스트 가능. (격리된 상태 -> 결합된 상태 -> 좀 더 결합된 상태 -> ... 점점 더 높은 수준으로)
- 실행 가능한 설명.
- 완전한 회귀 스위트가 늘어남

<br/>

> cf) 리펙터링은 작은 규모의 개선 사항을 찾아내는 식으로 진행되는 '미시적 기법'이다.  
> 경험상 리팩터링의 **'여러 작은 단계'** 를 엄격하고 지속적으로 적용해야만 **'커다란 구조적 개선'** 으로 이어질 수 있다.  
> 주의) 리펙터링은 재설계와 같은 활동이 아니다.

---

<br/>

### 좀 더 큰 그림

- 기존 **'레거시'** 에 바로 단위 테스트 작성하여 TDD를 시작하고 싶은 **'유혹'** 에 빠질 수 있다.  
(없는 것 보단 낫다고 함)
- 단위 테스트만 있는 프로젝트는 TDD 프로세스가 주는 혜택을 놓칠 수 있다.
    + 아무 데서도 호출하지 않는다. (테스트 자동화 부재?)
    + 시스템의 나머지 부분과 통합할 수 없다.
- 그렇다면 코드 작성을 어디서 부터 시작할까?

<br/>

| **실패하는 테스트 작성** |
|-|
|![image](https://user-images.githubusercontent.com/23611497/112597490-854ee480-8e50-11eb-8d86-a501f83d67b6.png)|

**실패하는 테스트**
- 어떤 기능을 구현할 때 인수 테스트를 작성하는 것으로 시작.
    + cf) 인수 테스트 : 만들고자 하는 기능을 시험하는 테스트
    + 인수 테스트를 사용해 작성하려는 코드가 실제로 필요한지 가늠한다. (직접 관련된 코드만 작성)
- 인수 테스트 하에서 단위 수준의 테스트, 구현, 리팩터링 주기를 따라 기능을 개발.
- 인수 테스트는 통과 시간이 길다. 아래와 같이 구분한다.
    + **'현재 작업 중인 인수 테스트'**(빌드에 아직 포함 되지 않는)
    + **'작업을 마친 인수 테스트'**(빌드에 포함되며 반드시 통과해야 하는)
- 실패하는 단위 테스트는 소스 저장소에 절대 커밋해서는 안 된다.

---

<br/>

### 전 구간 테스트

- 인수 테스트에서는 시스템 내부 코드를 가능한 한 직접 호출하지 말고 **'시스템 전 구간'** 을 시험해야 한다.
- 외부 유입 시스템 하고만 상호작용 한다.  
(시스템의 전체적인 작동 방식에는 시스템 외부 환경과의 상호 작용을 포함해야 한다)
- 단지 외부에서 유래한 시스템과 상호 작용하는 것이라면 '경계 간'테스트라고 부르는 편이 더 낫다.
- 전 구간 테스트는 시스템과 해당 시스템을 구축하고 배포하는 **'프로세스를 모두 시험'** 하는 방식으로 진행된다.

<br/>

**전 구간 빌드 주기 자동화 (CI,CD)**
- 자동화 주기 
    1. 누군가 소스 저장소에 코드 체크인 (수동)
    2. 최신 버전을 체크아웃해서 코드를 컴파일 (이하 자동)
    3. 단위 테스트 실행
    4. 시스템에 통합, 패키지
    5. 운영 환경 수준으로 배포
    6. 외부 접근 지점을 통한 시스템 시험
- 소프트웨어의 생애 동안 반복적으로 이루어짐.
- 실제보다 좀 더 어려운 출시 주기가 만들어 질수도 있으므로 전체적인 기술과 조직적인 환경을 이해해야 함.

---

<br/>

### 테스트의 수준

- 인수 테스트
    + **'전체 시스템이 동작하는가 ?'**
    + 전 구간의 기능이 제대로 동작함을 보증한다.
    + 관련 기술 또는 조직 문화에 따라 차이가 있음.
- 통합 테스트 
    + **'변경할 수 없는 코드(외부)를 대상으로 코드가 동작하는가 ?'**
    + 서드 파티 코드를 대상으로 만든 추상화가 기대한 대로 동작하는지 확인.
    + 영속화 매퍼같은 공용 프레임워크나 조직 내 다른 팀에서 개발한 라이브러리 등..
    + (큰 프로젝트의 경우) 느린 인수 테스트에 비해 좀 더 빠른 피드백을 얻기 위해 통합 테스트가 필요.
    + (작은 프로젝트의 경우) 인수 테스트가 통합 테스트의 역할을 할 수도 있음.
    + 관련 기술 또는 조직 문화에 따라 차이가 있음.
- 단위 테스트 
    + **'객체가 제대로 동작하는가 ? 객체를 이용하기가 편리한가 ?'**
    + (개인)프로그래밍 스타일에 따라 달라짐.
    + 모든 시스템에 공통으로 적용됨.

---

<br/>

### 외부 품질과 내부 품질

- 외부 품질
    + 시스템이 고객과 사용자의 요구를 얼마나 잘 충족하는가
    + 기능, 신뢰성, 가용성, 응답성 등
- 내부 품질
    + 시스템이 개발자와 관리자의 요구를 얼마나 잘 충족하는가
    + 이해하기 쉬운가, 변경하기 쉬운가 등 (코드 가독성, 느슨한 설계 등)
    + 내부 품질을 유지하기 위해 시스템 동작 방식을 **'안전'** 하고 **'예상 가능한 상태'** 로 **'바꿀 수 있게'** 만들어야 한다.
    + 그렇게 해야만 **'변경'** 으로 인해 **'큰 규모의 재작업을 해야 할 위험'** 을 최소화할 수 있음.

<br/>

- 전 구간 테스트로 시스템 외부 품질을 알 수 있다.
- 전 구간 테스트를 작성하면 팀 전체가 도메인을 얼마나 잘 이해하는지 알 수 있다.
- 단위 테스트로 코드를 얼마나 잘 작성했는지 알 수 있다. (전 구간 테스트로는 알 수 없음)

<br/>

**단위 테스트**

- 철저한 단위 테스트는 내부 품질을 개선하는데 도움이 된다.
- 단위를 테스트하려면 **'테스트 픽스처'** 에서 해당 단위를 시스템 바깥에서 실행할 수 있게 **'구조화'** 해야 하기 때문.
- 객체에 대한 단위 테스트 하려면
    + 객체를 생성하고 해당 객체의 의존성을 제공하며, 객체와 상호 작용하고, 예상대로 동작하는지 검사.
    + 클래스가 대체할 수 있는 명시적인 의존성(=느슨한 결합)과 명확한 책임(=높은 응집력)을 지녀야 한다.
    + 설계를 잘못하면 (클래스가 멀리 떨어져 있는 시스템의 일부와 긴밀하게 결합 | 암시적인 의존성 | 불분명한 책임이 많음 등)  
    **'단위 테스트를 작성하거나 이해하기 어려워짐'**
    + 테스트에 귀 기울이기
        + '테스트 하기 싫다' ↓ 
        + '왜? 하기 싫을까' (작성하기 어려운 이유 조사) ↓ 
        + 도메인 재설계(설계 방식이 틀리진 않았을까) | 코드 구조 개선(리팩터링)

<br/>

**테스트 픽스처 란**
+ cf) 테스트 픽스처란 : SUT(System Under Test)를 실행하기 위해 필요한 모든 것.
+ 픽스처는 테스트에 필요한 자원 생성, 테스트 가능한 상태로 세팅. (픽스처 설치 단계에 해당)
+ 픽스처는 테스트 **'선조건'** 을 의미, 이를 구현한 클래스는 Test Case Class 이다.
    - 1회용 신선한 픽스처
        + 테스트가 실행될 때마다 새로운 픽스처 생성.  
        (다른 테스트와 의존 관계가 없는 완벽한 독립성 보장, 대신 느림)
    - 지속되는 픽스처 
        + 테스트 대상 컴포넌트가 '어떤 상태를 유지 시키는 매커니즘을 가진 것'과 강하게 결합되어 있을 때 지속되는 픽스처가 될 수 있다.
        + 테스트 수행마다 해체 코드를 실행하여 '지속되는 신선한 픽스처'로 변경 가능
        + 픽스처를 지속되게 만드는 요소
            + 데이터 베이스 사용
            + 클래스 변수에 데이터 저장
            + 다른 테스트에서 사용되는 1회용 픽스처를 수행 후에도 Test Case Class 에서 갖고 있는 경우
    - 공유 픽스처
        + 테스트 실행 속도를 향상시키기 위해 사용.  
        많은 테스트가 하나의 픽스처를 공유하여 재사용.
        + 오래된 픽스처는 어질러지는 부수효과 발생, 이로인해 반복 안되는 테스트, 테스트 실행 전쟁 등 문제 발생.
            > 테스트 실행 전쟁 : 각 테스트에서 동시에 같은 픽스처 자원 접근, 테스트가 무작위로 실패하게 되는 문제.

---

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 2장 객체를 활용한 테스트 주도 개발

### 객체망

<blockquote><p> " 객체 지향 설계는 객체 자체보다 **'객체 간의 의사소통'** 에 더 집중한다. " </p></blockquote>

<blockquote><p> " 위대하고 성장 가능한 시스템을 만들 때의 핵심은 모듈 간의 의사소통에 있지, 모듈의 내부 특성이나 작동 방식에 있지 않다. " </p></blockquote>

<br/>

- 객체 지향 시스템은 **'협업하는 객체의 망'** 으로 구성되어 있다.
- 객체의 구성을 변경해 시스템 작동 방식을 바꿀 수 있다.
- 객체망의 행위에 대한 선언적 정의란
    + 객체 구성을 **'관리'** 할 목적으로 작성하는 코드.
    + 객체 구성을 관리한다는 것은 시스템을 관리하는 것.
    + **'목적'** 에 집중하기 쉬워짐.
- 즉, 객체 구성을 관리하기 쉽게 구성하면 **'변경이 쉬운 시스템'** 으로 됨.
    
---

<br/>

### 값과 객체

책에서 쓰이는 용어의 정확한 대상을 정리

- 값
    + 양이 고정된 불변 인스턴스.
    + 개인적인 식별자가 없으므로 두 값 인스턴스의 상태가 같아면 사실상 동일한 셈.

- 객체
    + 상태가 변할지도 모름.
    + 객체는 변경 가능한 상태를 이용해 시간의 추이에 따른 객체의 행위를 나타냄.
    + 두 상태가 정확히 동일하더라도 별개의 식별자를 지님.  
        (향후 어떤 메시지를 전달 받느냐에 따라 상태가 달라질 수 있기 때문)
    
---

<br/>

### 메시지를 따르라

- 객체는 일반적인 의사소통 패턴을 따르고 서로간의 의존성이 명시적.
- 의사소통 패턴
    + 객체들이 다른 객체와 상호 작용하는 방법을 관장하는 각종 규칙으로 구성.
    + 인터페이스 통한 역할 파악, 객체간 전달 가능한 메시지, 언제 전달 가능한지 등
    + 즉 의사소통 패턴은 **'객체 간에 있을 법한 관계에 의미를 부여'** 하는 행위이다.
    + 테스트와 목(mock) 객체는 객체 간의 의사소통을 또렷이 보여준다.

<br/>

**객체**
- 객체를 역할, 책임, 협력자 측면에서 생각하라.
- 객체는 역할을 하나 이상 구현한 것.
- 역할은 관련된 책임의 집합.
- 책임은 어떤 과업을 수행하거나 정보를 알아야 할 의무.
- 협력은 객체나 역할의 상호 작용에 해당.

---

<br/>

### 묻지 말고 말하라

- 디미터의 법칙
    + 객체들의 **'협력 정도를 제한'** 하면 결합도가 효과적으로 낮아진다.
    + **'한 줄에 점(.)을 하나만 찍는다.'**
    + 객체 구조의 경로를 따라 멀리 떨어져 있는 낯선 객체에 메시지를 보내는 설계는 피하라는 것.

```java
public class Post {
    private final List<Comment> comments;

    public Post(List<Comment> comments) {
        this.comments = comments;
    }

    public List<Comment> getComments() {
        return comments;
    }
}
```

```java
public class Board {
    private final List<Post> posts;

    public Board(List<Post> posts) {
        this.posts = posts;
    }

    public void addComment(int postId, String content) {
        posts.get(postId).getComments().add(new Comment(content));  // 열차 전복 코드
    }
    ...
}
```

<br/>

**문제점**
- 위 `addComment()` 코드처럼 `getter`가 줄줄이 이어지는 코드 형태가 디미터 법칙을 위반한 전형적인 코드 형태.
- `Board`객체는 `Post`객체에도 영향을 받고, `Comment`객체에도 영향을 받음.
- 이러한 설계는 객체 간 결합도를 높이고 객체 구조 변화에 쉽게 무너진다. 

<br/>

**해결**
- 객체는 **'내부적으로 보유하고 있거나 메시지를 통해 확보한 정보만'** 가지고 의사 결정을 내려야 한다.
- 규칙화 (아래 메서드만 호출해야 한다)
    + 객체 자신의 메서드 호출
    + 메서드 파라미터로 넘어온 객체들의 메서드 호출
    + 메서드 내부 생성, 초기화된 객체 메서드
    + 인스턴스 변수로 가지고 있는 객체가 소유한 메서드
    
```java
class Demeter {
    private Member member;

    public myMethod(OtherObject other) {
        // ...
    }

    public okLawOfDemeter(Paramemter param) {
        myMethod();                 // 1. 객체 자신의 메서드
        param.paramMethod();        // 2. 메서드의 파라미터로 넘어온 객체들의 메서드
        Local local = new Local();
        local.localMethod();        // 3. 메서드 내부에서 생성, 초기화된 객체의 메서드
        member.memberMethod();      // 4. 인스턴스 변수로 가지고 있는 객체가 소유한 메서드
    }
}
```
```java
// 1급 컬렉션 객체
public class Comments {
    private final List<Comment> comments;
    
    public void add(String content) {
        Comment newComment = Comment.newInstance(content);
        comments.add(newComment);
    }
}

public class Post {
    private final Comments comments;

    public Post(Comments comments) {
        this.comments = comments;
    }

    public void addComment(String content) {
        comments.add(content);
    }
}

public class Board {
    private final List<Post> posts;

    public Board(List<Post> posts) {
        this.posts = posts;
    }

    public void addComment(int postId, String content) {
        Post post = posts.get(postId);
        post.addComment(content);
    }
}
```

<br/>

**디미터 법칙 주의사항**
- 자료구조라면 디미터 법칙을 거론할 필요가 없다.
    + 자료 
        + 별 다른 동작 없이 자료를 노출
        + 자료구조를 사용하는 절차적 코드는 기존 자료구조를 변경하지 않으면서 새 함수를 추가하기 쉬움  
        + but 새 클래스 추가시 기존 함수 모두 변경해야함
    + 객체
        + 동작을 공개하고 자료를 숨김
        + 객체 지향 코드는 기존 함수를 변경하지 않으면서 새 클래스를 추가하기 쉬움  
        + but 새 함수 추가시 기존 클래스 모두 변경해야함

- 하나의 .을 강제하는 규칙이 아니다.
    + `IntStream.of(1, 15, 3, 20).filter(x -> x > 10).count();`  
        위 코드는 디미터 법칙을 위반한 코드가 아님
    + IntStream의 내부 구조가 노출되지 않았음. (다른 IntStream으로 변환할 뿐, 객체를 둘러싸고 있는 캡슐은 유지)
    + 객체 내부 구현에 대한 어떤 정보도 외부로 노출하지 않는다면 괜찮다!

<br/>

**자료구조**

```java
public class Square {
    public Point topLeft;
    public double side;
}

public class Rectangle {
    public Point topLeft;
    public double height;
    public double width;
}

public class Circle {
    public Point center;
    public double radius;
}

// 새로운 자료구조(Class)가 생긴다면 ? 
// 기존 자료구조를 사용하는 Geometry(공용 코드) 메서드는 전부 수정 되어야 한다... (area 등)

public class Geometry {
    public final double PI = 3.141592653589793;

    public double area(Object shape) throws NoSuchShapeException {
        if (shape instanceof Square) {
            Square s = (Square) shape;
            return s.side * s.side;
        } else if (shape instanceof Rectangle) {
            Rectangle r = (Rectangle) shape;
            return r.height * r.width;
        } else if (shape instanceof Circle) {
            Circle c = (Circle) shape;
            return PI * c.radius * c.radius;
        } else {
            throw new NoSuchShapeException();
        }
    }
    
    // 새로운 함수 추가는 용이함
    // 기존 자료구조 변경할 필요 없이 쭉쭉 추가 가능
}
```

- 따라서 위와 같은 방식(자료구조를 사용하는 절차적 코드)은 자료구조 방식에 유리

<br/>

**객체**

```java
public interface Shape {
    double area();
    
    // 새로운 함수가 추가된다면 ?
    // 인터페이스를 구현한 모든 객체들의 수정이 필요함
}

public class Square implements Shape {
    private Point topLeft;
    private double side;

    public double area() {
        return side * side;
    }
}

public class Rectangle implements Shape {
    private Point topLeft;
    private double height;
    private double width;

    public double area() {
        return height * width;
    }
}

public class Circle implements Shape {
    private Point center;
    private double radius;
    public final double PI = 3.141592653589793;

    public double area() {
        return PI * radius * radius;
    }
}

// 새로운 객체(클래스) 생성에는 용이함
// 기존 구현체들과는 독립적인 객체이기 때문
```

- 따라서 위와 같은 방식(객체 지향 코드)은 객체 방식에 유리
- 객체 지향적 코드는 디미터 규칙을 따라야 좋은 설계방식
    
---
    
<br/>

### 그래도 가끔은 물어라

> " 답을 가늠하는 데 도움이 되는 정보를 묻기보다는 진정 답하고자 하는 질문을 던져야 한다. "

```java
public void reserveSeats(ReservationRequest request) {
    for (Carriage carriage : carriages) {
        if (carriage.getSeats().getPercentReserved() < percentReservedBarrier) {
            request.reserveSeatsIn(carriage);
            return
        }
    }
    request.cannotFindSeats();
}
``` 

위 코드를 질의 메서드 형태도 변경해보면,

<br/>

```java
public void reserveSeats(ReservationRequest request) {
    for (Carriage carriage : carriages) {
        if (carriage.hasSeatsAvailableWithIn(percentReservedBarrier)) { // 질의 메서드
            request.reserveSeatsIn(carriage);
            return
        }
    }
    request.cannotFindSeats();
}
```

- 적절한 객체에 행위가 자리 잡아 행위에 이해하기 쉬운 이름이 생기게 된다. (테스트 하기도 용이)
- 주의할 점은 질의가 정보를 객체 바깥으로 '새어 나가게'하여 시스템을 경직되게 만들 수 있다.
- 단지 구현이 아니라 **'호출하는 객체의 의도'** 를 서술하는 질의를 작성하려고 애써야 한다.

---

<br/>

### 협력 객체의 단위 테스트

> " 초점을 맞추는 객체에 대해 각 객체가 서로 명령을 전달하고 자기 상태를 질의하는 수단을 노출하지 않아야 한다. "

<br/>

단위테스트에서 단정문을 쓸 만한 부분이 하나도 없는 것처럼 보인다.  

<br/>

**목 객체**
- 테스트 대상 객체의 이웃을 다른 대체물, 즉 목 객체(mock object)로 대체하는 것.
- 발생하는 이벤트에 대해 대상 객체가 가짜 이웃과 **'어떻게 상호 작용할지'** 지정할 수 있음.  
    (이 같은 명세를 **'예상 구문'** 이라 함)
- 테스트 동안 목 객체는 자신이 예상대로 호출됐는지 단정함.
- 나머지 테스트가 동작하는 데 필요한 행위(스텁 형태로 동작)를 구현하기도 함.

<br/>

**인터페이스 발견**
- 객체에 필요한 보조 역할을 파악하는 데 도움.
- 이러한 보조 역할은 자바 인터페이스로 정의되어 있고 시스템의 나머지 부분을 개발할 때 실제 구현처럼 동작.

---

<br/>

### 목 객체를 활용한 TDD 지원

|목 객체를 활용한 객체 테스트|
|-|
|![image](https://user-images.githubusercontent.com/23611497/112634234-af6acb80-8e7d-11eb-981b-5c3005c2333b.png)|

<br/>

**테스트 핵심 구조**
- 필요 **'목 객체'** 생성
- 대상 객체를 포함한 **'실제 객체'** 생성
- 대상 객체에서 목 객체가 **'어떻게 호출될지 예상하는 바'** 기술 (예상 구문)
- 대상 객체에서 **'유발(trigger) 메서드(하나 또는 여러 개) 호출'**
- **'결과 값이 유효'** 하고 **'예상되는 메서드 호출이 모두 일어났는지'** 확인

**목 객체를 활용한 객체 테스트** 는 다음과 같이 진행된다.
1. 이웃하는 객체의 **'목 인스턴스를 생성'**
2. 해당 목 인스턴스를 어떻게 호출하고 상태를 검사하는가에 관한 **'예상 구문 정의'**
3. **'스텁'** 형태로 동작할 필요가 있는 행위 구현

<br/>

**모조 객체**
- 테스트의 콘텍스트를 담고 있음
- 목 객체를 생성
- 예상 구문과 스텁 관리

<br/>

> " 이 책 전반에 걸쳐 반복해서 강조하듯이 중요한 것은 모든 테스트 의도를 명확하게 해서 테스트를 거친 기능과 보조 역할을 담당하는 기반 구조, 객체 구조를 서로 구분하는 것이다. "

---

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 3장 도구 소개

<br/>

### JUnit 4 소개

기본적으로 JUnit 은 **'리플렉션'**을 통해 클래스 구조를 파악한 후 해당 클래스 내 테스트를 모두 실행한다.

```java
public class CatalogTest {
    private final Catalog catalog = new Catalog(); // 픽스처
    
    @Test 
    public void containsAnAddedEntry() {    // 테스트 메서드는 값을 반환하거나 매개변수를 받아서는 안 됨.
        Entry entry = new Entry("사과", "바나나");
        catalog.add(entry);
        
        assertTrue(catalog.contains(entry));    // true 이므로 테스트 성공
    }
    
    @Test
    public void indexesEntriesByName() {
        Entry entry = new Entry("사과", "바나나");
        catalog.add(entry);
        
        assertEquals(entry, catalog.entryFor("사과"));    // 두 값이 동일하므로 (true) 이므로 테스트 성공
        assertNull(catalog.entryFor("멜론"));             // catalog 내에 '멜론'이 없으므로 (null) 테스트 성공
    }
}
```

<br/>

**테스트 케이스**
- @Test 애노테이션으로 지정된 메서드
- 값을 반환하거나 매개변수를 받아서는 안된다.
- JUnit 에서는 **'매번'** 테스트 클래스의 **'새 인스턴스를 생성한 후'** 테스트 케이스를 호출한다.
    + 매번 새 객체를 생성하면 각 테스트 간의 **격리성**이 확보됨.
    + 즉 각 테스트 케이스마다 객체 필드 내용을 마음껏 바꿀 수 있다.

<br/>

**Assertion**
- 테스트 내에서 테스트 대상 객체를 호출하고 그 결과를 Assertion(검사, 단정 등으로 불림) 한다.
- JUnit 내 정의돼 있는 Assertion 메서드를 사용한다.
    + `assertNull`, `assertEquals`, `assertThat` 등...

<br/>

**예외 예상하기**
- @Test 애노테이션은 선택적인 매개변수로 `expected`를 지원한다.
- 해당 테스트 케이스에서 던질 예외를 선언한다.
- 테스트에서 예외를 던지지 않거나 다른 예외를 던지면 테스트 실패

```java
@Test(expected=IllegalArgumentException.class)      // IllegalArgumentException 예외를 던지는지 검사
public void cannotAddTwoEntriesWithTheSameName() {  // 두 항목이 같은 이름으로 추가될 경우 예외
    catalog.add(new Entry("사과", "바나나"));
    catalog.add(new Entry("사과", "멜론"));
}
```

<br/>

**테스트 픽스처**
- 테스트가 시작할 때 존재하는 고정된 상태를 의미함.
- 테스트가 반복 가능함을 보장 (매번 동일한 상태로 시작하므로 동일한 결과를 냄)
- 준비(`setup`) 과정과 정리(`teardown`)과정이 있음.
- `@Before` 애노테이션으로 픽스처를 준비하며 `@After` 애노테이션으로 픽스처를 정리.
    + 많은 JUnit 테스트에서 명시적으로 픽스처를 정리하지 않아도 되는데,  
      픽스처를 준비할 때 JVM GC로 생성된 객체를 수거하는 것만으로도 충분하기 때문.
- 공통적인 초기화 작업은 보통 `@Before` 메서드로 옮겨도 된다.

```java
public class CatalogTest {
    final Catalog catalog = new Catalog();
    final Entry entry = new Entry("사과", "바나나");
    
    @Before
    public void fillTheCatalog() {
        catalog.add(entry);
    }
    
    ...
}
```

<br/>

**테스트 러너**
- JUnit 이 리플렉션을 수행해 해당 테스트를 실행하는 방식은 테스트 러너에서 제어한다.
- `@RunWith` 애노테이션으로 설정.

---

<br/>

### 햄크레스트 매처와 assertThat()

**'햄크레스트'** 는 매칭 조건을 선언적으로 작성하는 프레임워크이다.  
- 햄크레스트 자체는 테스트 프레임워크가 아니다.
- 여러 테스트 프레임워크(JUnit, jMock, WindowLicker 등)에서 쓰인다.

<br/>

**햄크레스트 매처**
- 특정 객체가 어떤 조건과 일치하는지 알려준다.
- 일치하지 않는 이유를 기술할 수 있다.

```java
String str = "바나나가 먹고싶어요.";

Matcher<String> containsBananas = new StringContains("바나나");
Matcher<String> containsMangoes = new StringContains("망고");

assertTrue(containsBananas.matched(str));   // str 내 '바나나' 문자열이 있으므로 true, 테스트 성공
assertFalse(containsMangoes.matched(str));  // str 내 '망고' 문자열이 없으므로 false, 테스트 성공
```

<br/>

- 대게 매처는 직접적으로 인스턴스화 하지 않는다.
- 코드 가독성을 높이고자 모든 매처에 대한 정적 팩터리 메서드 제공.

```java
assertTrue(containsString("바나나").matched(str));    // str 내 '바나나' 문자열이 있으므로 true, 테스트 성공
assertFalse(containsString("망고").matched(str));     // str 내 '망고' 문자열이 없으므로 false, 테스트 성공
```
- 코드가 조금 더 깔끔해 졌다.

<br/>

- 실제로는 매처를 JUnit `assertThat` 메서드와 조합해 사용한다.
    + `assertThat` 은 매처의 **'자기서술적(self-describing)'**인 특성을 활용해  
      Assertion 에 실패할 경우 뭐가 잘못됐는지 분명하게 드러낼 수 있다.

```java
assertThat(str, containsString("바나나"));        // str 내 '바나나' 문자열이 있으므로 테스트 성공
assertThat(str, not(containsString("망고")));     // str 내 '망고' 문자열이 없으므로 테스트 성공

assertThat(str, not(containsString("바나나")));    // str 내 '바나나' 문자열이 있으므로 테스트 실패
```

- `not` 메서드는 전달된 매처의 의미와 반대되는 매처를 생성한다.
- 마지막 구문의 실패 보고 내용은 다음과 같다.

```java
java.lang.AssertionError:
Expected: not a string containing "바나나"
     got: "바나나가 먹고싶어요."
```

- `assertThat` 에 매처 표현식을 전달하고 그 일을 알아서 처리하게 할 수 있다.
- 사용자가 햄크레스트를 확장할 수 있다.
    + 매처 인터페이스를 팩터리 메서드로 구현하여 매처를 작성.
    + 결과물은 기존 매처 표현식과 자연스럽게 합쳐진다.

---

<br/>

### jMock2: 목 객체

jMock 은 목 객체를 활용한 테스트 방식을 지원한다.
- 목 객체를 동적으로 생성함.
- 목 구현체를 직접 작성하지 않는다.
- 목 객체를 어떻게 호출하고 목 객체가 거기에 반응해 어떻게 동작할지 지정하는 고수준 API 제공.
- **'jMock 은 예상 구문의 기술을 최대한 명확하게 할 목적으로 고안한 것!!'**

<br/>

**jMock 핵심 개념**
- 모조 객체
    + 테스트 대상 객체의 콘텍스트.
    + 대상을 이웃하는 객체(=그 객체가 사용하는 다른 객체)를 표현한다.
    + 즉 목 객체를 생성하기도 하고, 예상 구문을 정의하기도 하는 컨텍스트 이다.
- 목 객체
    + 테스트 대상 객체의 실제 이웃(=그 객체가 사용하는 다른 객체, 연관 객체...)
    + 가짜 객체(프록시)같은 느낌
- 예상 구문
    + 목 객체가 어떻게 호출(작동)하는지 기술하는 곳
    + 즉 목 객체 내부에 어떤 로직이 (테스트 대상 객체에 호출로 인해)어떻게 작동하는지 기술

<br/>

```java
/*
 * RunWith 애노테이션을 지정하면 
 * 테스트가 끝나는 시점에 모조 객체를 자동으로 호출해
 * 모든 목 객체가 예상대로 호출됐는지 검사함.
 */
@RunWith(JMock.class)
public class AuctionMessageTranslatorTest {
    
    /*
     * 모조 객체
     * 올바른 예외 타입을 던져 테스트 실패를 JUnit 에게 보고함.
     * 관례상 모조 객체를 context 라는 필드에 보관.
     * (테스트 대상 객체의 컨텍스트를 나타내므로)
     */ 
    private final Mockery context = new JUnit4Mockery();
    
    /*
     * 목 객체
     * 모조 객체를 사용해 목 객체를 생성한다.
     * 여기서 생성한 목 객체는 실제 리스너 구현체를 대신할 것이다.
     */
    private final AuctionEventListener listener = context.mock(AuctionEventListener.class);
    
    /*
     * 테스트 대상 객체
     * 목 객체(가짜 객체)를 해당 인스턴스의 생성자에 전달한다.
     * 목 객체의 인터페이스를 통해 상호 작용하며,
     * 해당 인터페이스가 어떻게 구현돼 있는지 신경 쓰지 않는다.
     */
    private final AuctionMessageTranslator translator = new AuctionMessageTranslator(listener);
    
    @Test
    public void notifiesAuctionClosedWhenCloseMessageReceived() {
        /*
         * 테스트에서 사용될 다른 객체
         */
        Message message = new Message();
        message.setBody("SOLVersion: 1.1; Event: CLOSE;");
        
        /*
         * 예상 구문 블록
         * 테스트 과정에서 번역기(translator)가 이웃 객체를 어떻게 호출할지 모조 객체에 알림.
         */
        context.checking(new Expectations() {{
            /*
             * 단일 예상 구문
             * 코드가 작동하는 과정에서 리스너의 auctionClosed() 메서드가
             * 정확히 한 번(oneOf) 호출될 것으로 예상한다는 의미.
             */
            oneOf(listener).auctionClosed();
        }});
        
        /*
         * 테스트 대상 객체 호출
         * 테스트에 따르면 번역기는 리스너를 대상으로 auctionClosed()를 한 번 호출할 것으로 예상함.
         * 모조 객체는 테스트 과정에서 목 객체가 예상대로 호출됐는지 검사하고
         * 예상과 달리 호출되면 즉시 테스트가 실패하게 된다.
         */
        translator.processMessage(UNUSED_CHAT, message);
        
        /* 참고로 Assertion 을 아무것도 하지 않아도 된다. (목 객체 테스트에서 종종 볼 수 있음) */
    }
}
```

<br/>

**예상 구문**
- 예상하는 호출의 최소/최대 횟수
- 호출이 예상되거나(호출되지 않을 경우 테스트 실패) 단순히 호출이 일어나는 것을 허용하는지 여부(호출되지 않으면 테스트 통과)
- 매개변수 값 (상수로 만들어 지정하거나 햄크레스트 매처로 제한할 수 있음)
- 다른 예상 구문을 고려한 제약 조건의 순서 지정
- 반환할 값 지정
- 던질 예외 지정

<br/>

예상 구문 블록은 **'이웃 객체가 어떻게 호출되는지 기술하는 코드'**와  
**'실제도 객체를 호출하고 결과를 검사하는 코드'**를 분명하게 구분하는 데 목적이 있다.  
(선언적인 언어처럼 동작함)  

<br/>

> " 가장 중요한 것은 구현 방법이 아니라 그 이면에 자리한 개념과 동기다. "

---

<br/>
    
[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

<br/>

## 2부 테스트 주도 개발 과정

<br/>

## 4장 테스트 주도 주기 시작

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 5장 테스트 주도 개발 주기의 유지

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 6장 객체 지향 스타일

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 7장 객체 지향 설계의 달성

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 8장 서드 파티 코드를 기반으로 한 개발

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

<br/>

## 3부 동작하는 예제

<br/>

## 9장 경매 스나이퍼 개발 의뢰

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 10장 동작하는 골격

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 11장 첫 테스트 통과하기

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 12장 입찰 준비

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 13장 스나이퍼가 입찰하다

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 14장 스나이퍼가 경매에서 낙찰하다

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 15장 실제 사용자 인터페이스를 향해

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 16장 여러 품목에 대한 스나이핑

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 17장 Main 분석

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 18장 세부 사항 처리

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 19장 실패 처리

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

<br/>

## 4부 지속 가능한 테스트 주도 개발

<br/>

## 20장 테스트에 귀 기울이기

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 21장 테스트 가독성

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 22장 복잡한 테스트 데이터 만들기

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 23장 테스트 진단

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 24장 테스트 유연성

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>
    
<br/>

## 5부 고급 주제

<br/>

## 25장 영속성 테스트

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 26장 단위 테스트와 스레드

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 27장 비동기 코드 테스트

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]
