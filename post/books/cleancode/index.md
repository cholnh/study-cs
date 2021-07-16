## Clean Code

<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/cs/tn-cleancode.jpg" width="250" />

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) ]

<br/>

<br/>

## Index
- [들어가면서](#들어가면서)
- 1장 [깨끗한 코드](#1장-깨끗한-코드)
- 2장 [의미 있는 이름](#2장-의미-있는-이름)
- 3장 [함수](#3장-함수)
- 4장 [주석](#4장-주석)
- 5장 [형식 맞추기](#5장-형식-맞추기)
- 6장 [객체와 자료 구조](#6장-객체와-자료-구조)
- 7장 [오류 처리](#7장-오류-처리)
- 8장 [경계](#8장-경계)
- 9장 [단위 테스트](#9장-단위-테스트)
- 10장 [클래스](#10장-클래스)
- 11장 [시스템](#11장-시스템)
- 12장 [창발성(創發性)](#12장-창발성創發性)
- 13장 [동시성](#13장-동시성)
- 14장 [점진적인 개선](#14장-점진적인-개선)
- 15장 [JUnit 들여다보기](#15장-JUnit-들여다보기)
- 16장 [SerialDate 리팩터링](#16장-SerialDate-리팩터링)
- 17장 [냄새와 휴리스틱](#17장-냄새와-휴리스틱)

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) ]

<br/>

<br/>

## 들어가면서

<br/>

> " 과거와는 달리 조금 더 나아진 방법으로 코드를 만들기 위해 의식적으로 신경을 쓴다. "

<br/>

> " 우리 개발자들에게는 체크아웃해 코드를 꺼낼 때보다 체크인해서 코드를 넣을 때 더 깨끗한 상태로 만들어야 할 의무가 있다. "

<br/>

> " 신은 세세함에 깃들어 있다. "

<br/>

> " 책임 있는 전문가라면 프로젝트를 시작할 때 생각하고 계획할 시간을 확보해야 한다. "

<br/>

> " 시란 영원히 미완성이라 끝없는 재작업이 필요하며 포기할 때에만 끝난다. "

<br/>

> " 불행히도 우리는 세세함에 집중하는 태도가 프로그래밍 기술에 핵심적인 주춧돌이라 여기지 않곤 한다. 코드에서는 일찌감치 손을 뗀다. 구현을 끝냈기 때문이 아니라 본질보다 모양새를 중시하는 가치체계 때문이다. "

<br/>

> " 흔히 우리는 아키텍처나 프로그래밍 언어나 좀 더 고차원적인 뭔가가 품질을 결정하는 요인이기를 바란다. 소위 전문가는 고상한 설계 방법론과 도구에 통달해야 한다고 생각하는 까닭에, 무식한 기계, 그러니까 아무 생각 없는 공돌이인 코더가 간단한 들여쓰기 스타일로 가치를 더한다는 사실에 모욕감을 느낀다. "

<br/>

> " 품질은 하늘에서 뚝 떨어진 위대한 방법론이 아니라 사심 없이 기울이는 무수한 관심에서 얻어진다. "

<br/>

> " 장인 정신을 익히는 과정은 두 단계로 나뉜다. 바로 이론과 실전이다. 첫째, 장인에게 필요한 원칙, 패턴, 기법, 경험이라는 지식을 습득해야 한다. 둘째, 열심히 일하고 연습해 지식을 몸과 마음으로 체득해야 한다. "

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 1장 깨끗한 코드

<br/>

### 코드가 존재하리라

> " 언젠가 코드가 사라지리라 생각하는 사람들은 언젠가 비정형적인 수학이 나오리라 기대하는 수학자와 비슷하다. 그들은 우리가 시키는 대로가 아니라 원하는 대로 돌아가는 기계가 나오리라 기대한다. 우리가 그런 기계를 만드는 방법을 찾아내리라 믿는다. 요구사항을 모호하게 줘도 우리 의도를 정확히 꿰뚫어 프로그램을 완벽하게 실행하는 그런 기계 말이다. 절대로 불가능한 기대다. "

<br/>

### 나쁜 코드

> " 우리 모두는 대충 짠 프로그램이 돌아간다는 사실에 안도감을 느끼며 그래도 안 돌아가는 프로그램보다 돌아가는 쓰레기가 좋다고 스스로를 위로한 경험이 있다. 나중은 결코 오지 않는다. "

<br/>

### 태도

> " 코드가 왜 그렇게 되었을까? 좋은 코드다 어째서 순식간에 나쁜 코드로 전락할까? 우리는 온갖 이유를 들이댄다. 원래 설계를 뒤집는 방향으로 요구사항이 변했다고 불편한다. 일정이 촉박해 제대로 할 시간이 없었다고 한탄한다. 멍청한 관리자와 조급한 고객과 쓸모없는 마케팅 부서와 전화기 살균제 탓이라 떠벌인다. 하지만 잘못은 전적으로 우리 프로그래머에게 있답니다. 우리가 전문가답지 못했기 때문입니다. "

<br/>

> " 좋은 코드를 사수하는 일은 바로 우리 프로그래머들의 책임이다. "

<br/>

### 깨끗한 코드라는 예술?

> " 깨끗한 코드와 나쁜 코드를 구분할 줄 안다고 깨끗한 코드를 작성할 줄 안다는 뜻은 아니다. "

<br/>

> " '코드 감각'이 있는 프로그래머는 나쁜 모듈을 보면 좋은 모듈로 개선할 방안을 떠올린다. '코드 감각'으로 최고 방안을 선택한 후 여기서 거기까지 이동하는 경로를 계획한다. "

<br/>

### 비야네 스트롭스트룹

> " 우아하지 않은 코드는 바람직하지 않은 결과를 초래한다. 비야네는 '유혹'이라는 단어로 그 결과를 표현한다. 여기에는 심오한 진실이 담겨 있다. 나쁜 코드는 나쁜 코드를 '유혹'한다! 흔히 나쁜 코드를 고치면서 오히려 더 나쁜 코드를 만든다는 뜻이다. "

<br/>

### 그레디 부치

> " 코드는 추측이 아니라 사실에 기반해야 한다. 반드시 필요한 내용만 담아야 한다. 코드를 읽는 사람에게 프로그래머가 단호하다는 인상을 줘야 한다. "

<br/>

### 론 제프리스

> " 메서드가 여러 기능을 수행한다면 메서드 추출 리팩터링 기법을 적용해 기능을 명확히 기술하는 메서드 하나와 기능을 실제로 수행하는 메서드 여러 개로 나눈다. "

<br/>

> " 프로그램을 짜다 보면 어떤 집합에서 특정 항목을 찾아낼 필요가 자주 생긴다. 이런 상황이 발생하면 나는 추상 메서드나 추상 클래스를 만들어 실제 구현을 감싼다. 그러면 여러 가지 장점이 생긴다. '진짜'문제에 신경 쓸 여유가 생긴다. "

<br/>

### 보이스카우트 규칙

> " 캠프장은 처음 왔을 때보다 더 깨끗하게 해놓고 떠나라. "

<br/>

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 2장 의미 있는 이름

<br/>

### 의도를 분명히 밝혀라

> " 좋은 이름을 지으려면 시간이 걸리지만 좋은 이름으로 절약하는 시간이 훨씬 더 많다. "

- 변수(혹은 함수나 클래스)의 존재 이유는 ?
- 수행 기능은 ?
- 사용 방법은 ?
> 따로 주석이 필요하다면 의도를 분명히 드러내지 못했다는 말이다.

<br/>

```java
public List<int[]> getThem() {
    List<int[]> list1 = new ArrayList<int[]>();
    for (int[] x : theList)
        if (x[0] == 4)
            list1.add(x);
    return list1;
}
```

위 코드는 암암리에 다음과 같은 정보를 안다고 **가정**한다.
1. theList에 무엇이 들었는가 ?
2. theList에서 0번째 값이 어째서 중요한가 ?
3. 값 4는 무슨 의미인가 ?
4. 함수가 반환하는 리스트 list1을 어떻게 사용하는가 ?

<br/>

```java
public List<Cell> getFlaggedCells() {
    List<Cell> flaggedCells = new ArrayList<Cell>();
    for (Cell cell : gameBoard)
        if (cell.isFlagged())
            fraggedCells.add(cell);
    return flaggedCells;
}
```

단순히 이름만 고쳤는데도 함수가 하는 일을 이해하기 쉬워졌다. 바로 이것이 좋은 이름이 주는 위력이다.

<br/>

### 의미 있게 구분하라

```java
getActiveAccount();
getActiveAccounts();
getActiveAccountInfo();
```

이 프로젝트에 참여한 프로그래머는 어느 함수를 호출할지 어떻게 알까 ?  
**읽는 사람이 차이를 알도록 이름을 지어라.**

<br/>

### 발음하기 쉬운 이름을 사용하라

<br/>

### 검색하기 쉬운 이름을 사용하라

<br/>

### 인코딩을 피하라

> " 문제 해결에 집중하는 개발자에게 인코딩은 불필요한 정신적 부담이다. "

<br/>

### 자신의 기억력을 자랑하지 마라

<blockquote><p>" 코드를 읽으면서 변수 이름을 자신이 아는 이름으로 변환해야 한다면 그 변수 이름은 바람직하지 못하다. (변수 i, j, k는 괜찮다) "</p></blockquote>

<blockquote><p>" 전문가 프로그래머는 명료함이 최고라는 사실을 이해한다. "</p></blockquote>

<br/>

### 클래스 이름

> " `Manager` `Processor` `Data` `Info` 등과 같은 단어는 피하고, 동사는 사용하지 않는다. "

<br/>

### 메서드 이름

> " 동사나 동사구가 적합 "

<br/>

생성자를 중복정의 할 때는 **정적 팩토리 메서드**를 사용한다.  

`Complex complex = Complex.FromRealNumber(23.0);` ( o )  
`Complex complex = new Complex(23.0);` ( x ) 

<br/>

### 기발한 이름은 피하라

<br/>

### 한 개념에 한 단어를 사용하라

> " 추상적인 개념 하나에 단어 하나를 선택해 이를 고수한다. "

똑같은 메서드를 클래스 마다 `fetch`, `retrieve`, `get` 으로 제각각 부르면 혼란스럽다.

<br/>

### 말장난을 하지 마라

- 집합에 값 하나를 추가하는 `add`메서드 
- 기존 값 두 개를 더하거나 이어서 새로운 값을 만드는 `add`메서드  
두 메서드는 맥락이 다르다. 일관성을 지키기 위해 `add`를 고수할 필요 없다.  
`insert`나 `append`와 같은 이름이 적당함.

<br/>

### 해법 영역에서 가져온 이름을 사용하라

> " 코드를 읽을 사람도 프로그래머라는 사실을 명심한다. 그러므로 전산 용어, 알고리즘 이름, 패턴 이름, 수학 용어 등을 사용해도 괜찮다. "

<br/>

### 문제 영역에서 가져온 이름을 사용하라

> " 적절한 '프로그래머 용어'가 없다면, 문제 영역(도메인 영역?)에서 이름을 가져온다. "

<br/>

### 의미 있는 맥락을 추가하라

<blockquote><p> " 클래스, 함수, 이름 공간에 의미를 넣어 맥락을 부여한다. " </p></blockquote>

<blockquote><p> " 모든 방법이 실패하면 마지막 수단으로 접두어를 붙인다. " </p></blockquote>

<br/>

### 불필요한 맥락을 없애라

<br/>

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 3장 함수

<br/>

> " 의도를 분명히 표현하는 함수를 어떻게 구현할 수 있을까 ? "

<br/>

### 작게 만들어라!

> " 함수를 만드는 첫째 규칙은 '작게', 두 번째 규칙은 '더 작게!' "

- 각 함수가 이야기 하나를 표현한다. (쓰임이 명백해야 한다)
- if 문 / else 문 / while 문 등에 들어가는 블록은 한 줄이어야 한다.
    + 대게 여기서 함수를 호출한다. (바깥을 감싸는 함수가 작아져 가독성이 높아진다) 
    + 즉 중첩 구조가 생길만큼 함수가 커져서는 안 된다.

<br/>

### 한 가지만 해라!

> " 함수는 한 가지를 해야 한다. 그 한 가지를 잘 해야 한다. 그 한 가지만을 해야 한다. "

- 지정된 함수 이름 아래에서 **'추상화 수준이 하나인 단계만 수행'** 한다면 그 함수는 한 가지 작업만 한다.
- 단일 책임 원칙 (SRP) 과 같은 말.

<br/>

### 함수 당 추상화 수준은 하나로!

- 함수 내 모든 문장의 **'추상화 수준이 동일'** 해야 함.
- 한 함수 내에 여러 추상화 수준이 섞여있으면 읽는 사람이 헷갈림.
    + 추상화 수준이 높은 코드
        `getHtml()`
    + 추상화 수준이 낮은 코드
        `.append("\n")`
- 위에서 아래로 **'이야기'** 처럼 읽혀야 좋다.
    + 위에서 아래로 한 번 내려갈 수록, 추상화 수준도 한 단계씩 낮아져야 함.

<br/>

### Switch 문

- 다형성을 이용하여 저차원 클래스에 숨기고 반복을 피해야 한다.

**SRP 를 위반한 Switch 사용 함수 예시**

```java
public Money calculatePay(Employee e) throw InvalidEmployeeType {
    switch (e.type) {
        case COMMISSIOND:
            return calculateCommissionedPay(e);
        case HOURLY:
            return calculateHourlyPay(e);
        case SALARIED:
            return calculateSalariedPay(e);
        default:
            throw new InvalidEmployeeType(e.type);
    }
}
```

**문제점**

- 함수가 길다. (새 직원 유형을 추가하면 더 길어짐)
- 한 가지 작업만 수행하지 않는다.
- SRP를 위반한다. (코드를 변경할 이유가 여럿이기 때문)
- OCP를 위반한다. (새 직원을 추가할 때마다 코드를 변경해야 하기 때문)
- 제일 심각한 문제는 위 함수와 구조가 동일한 함수가 무한정 생성될 수 있다.
    + `isPayDay(Employee e, Date date)`
    + `deliverDay(Employee e, Money pay)`

<br/>

**추상 팩토리 사용하여 해결**

```java
public abstract class Employee {
    public abstract boolean isPayDay();
    public abstract Money calculatePay();
    public abstract void deliverDay(Money pay);
}

---

public interface EmployeeFactory {
    Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType;
}

---

public class EmployeeFactoryImpl implements EmployeeFactory {
    public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType {
        switch (r.type) {
            case COMMISSIOND:
                return new CommissionedEmployee(r);
            case HOURLY:
                return new HourlyEmployee(r);
            case SALARIED:
                return new SalariedEmployee(r);
            default:
                throw new InvalidEmployeeType(r.type);
        }
    }
}
```

- 팩토리는 `switch`문을 사용해 적절한 `Employee` 파생 클래스의 인스턴스를 생성.
- `calculatePay`, `isPayDay`, `deliverDay` 와 같은 함수는 Employee 인스턴스를 거쳐 호출.
- 다형성으로 인해 실제 파생 클래스의 함수가 실행됨.

<br/>

### 서술적인 이름을 사용하라!

- 함수가 하는 일을 잘 표현해야 한다.
- private 함수 또한 서술적인 이름을 지어야 한다.  

> 길고 서술적인 이름이 짧고 어려운 이름보다 좋다.  
> 길고 서술적인 이름이 길고 서술적인 주석보다 좋다.  

- 이름을 붙일 때는 일관성이 있어야 한다.
- 모듈 내에서 함수 이름은 같은 문구, 명사, 동사를 사용한다.
    + `includeSetupAndTeardownPages`, `includeSetupPages`, `includeSuiteSetupPage`, `includeSetupPage` 등이 좋은 예다.
    + > "includeTearDownPages, includeSuiteTeardownPage 도 있나요?" 당연하다. '짐작하는 대로'다.

<br/>

### 함수 인수

> " 함수에서 이상적인 인수 개수는 0개(무항)다. "

- 인수(매개변수)는 개념을 이해하기 어렵게 만든다.
- 함수 이름과 인수 사이에 추상화 수준이 같아야 한다.
- 인수가 3개를 넘어가면 인수마다 유효한 값으로 모든 조합을 구성해 테스트하기가 상당이 부담스러워 짐.

<br/>

> " 출력 인수는 입력 인수보다 이해하기 어렵다. "

- 출력 인수는 매개변수로 받은 출력기능을 하는 객체이다.
    + `appendFooter(StringBuffer report)` 에 `StringBuffer` 와 같은. 
- 인수로 입력을 넘기고 반환값으로 출력을 받는다는 개념이 일반적이다.
- 대개 함수에서 인수로 결과를 받으리라 기대하지 않는다. (코드를 재차 확인하게 만든다) 
- 객체 지향 언어에서는 출력 인수를 사용할 필요가 거의 없다.
    + 출력 인수로 사용하라고 설꼐한 변수가 바로 `this` 이기 때문
    + `public void appendFooter(StringBuffer report)` 보다는 `report.appendFooter()` 더 낫다.
    + 함수에서 상태를 변경해야 한다면 함수가 속한 객체 상태를 변경하는 방식을 택한다.

<br/>

**많이 쓰는 단항 형식**
- 인수에 질문을 던지는 형식
    + `boolean fileExists("myFileName")`
- 인수를 뭔가로 변환해 결과로 반환하는 형식
    + `InputStream fileOpen("myFileName")`
- 이벤트 형식 (입력 인수로 시스템 상태를 변경)
    + `passwordAttemptFailedNtimes(int attempts)`

**주의 해야할 단항 형식**
- 위에서 설명한 경우가 아니라면 단항 함수는 가급적 피한다.
- 변환 함수에서 출력 인수를 사용하면 혼란을 일으킨다.
    + `void includeSetupPageInto(StringBuffer pageText)`
- 입력 인수를 변환하는 함수라면 변환 결과는 반환값으로 돌려준다.
    + `StringBuffer transform(StringBuffer in)`
- 플래그 인수는 추하다.
    + 함수가 한꺼번에 여러 가지를 처리한다고 대놓고 공표하는 셈.
- 인수가 2~3개 필요하다면 독자적인 클래스 변수로 선언할 가능성을 짚어본다.

**동사와 키워드**
- 단항 함수는 함수와 인수가 동사/명사 쌍을 이뤄야 한다.
    + `writeField(name)`
- 함수 이름에 키워드를 추가하는 형식 (인수 순서에 따라)
    + `assertEquals` 보다는 `assertExpectedEqualsActual(expected, actual)` 이 더 좋음.

<br/>

### 부수 효과를 일으키지 마라!
 
> " 함수에서 한 가지를 하겠다고 약속하고선 남몰래 다른 짓을 하지 마라. "

- 부수 효과는 시간적인 결합이나 순서 종속성을 초래한다.
    + 시간과 결합한다는 의미는 동시성을 띄지 못함을 의미(시간에 종속되어).
    + cf) 실용주의 프로그래머

<br/>

### 명령과 조회를 분리하라!

- 함수는 뭔가를 수행하거나 뭔가에 답하거나 둘 중 하나만.
- 객체 상태를 변경하거나 아니면 객체 정보를 반환하거나 (둘 중 하나!)
    + `public boolean set(String attribute, String value)` 이러한 함수는  
        `if (set("username", "unclebob"))` 과 같은 괴상한 코드가 나온다.
        + 코드만 봐서는 의미가 모호함. (set 단어가 명령인지 조회인지...)
        + username 을 unclebob으로 설정(set)하는 것인지, 설정되어 있다면 인지...
    + 해결책은 명령과 조회를 분리해 혼란을 애초에 뿌리뽑는 방법이다.  
        + `if(attributeExists("username"))` 과 `setAttribute("username", "unclebob")` 으로 나눠야함. 

<br/>

### 오류 코드보다 예외를 사용하라!

- 명령 함수에서 오류 코드를 if 표현식으로 중첩하여 반환하지 마라.
    + 호출자는 오류 코드를 곧바로 처리해야 함.
- 오류 코드 대신 예외를 사용하라.
- try / catch 블록은 코드 구조에 혼란을 준다. (별도로 뽑아내는 것이 좋음)
- 오류 처리도 '한 가지' 작업에 속한다. (오류를 처리하는 함수는 오류만 처리해야 마땅하다)

**Error.java 의존성 자석**  
오류 코드를 반환한다는 이야기는, 클래스든 열거형 변수(enum)든, 어디선가 오류 코드를 정의한다는 뜻

```java
public enum Error {
    OK,
    INVALID,
    NO_SUCH,
    LOCKED,
    ...
}
```

위와 같은 코드는 **'의존성 자석'** 이다.  
다른 클래스에서 Error enum을 import해 사용해야 하므로, 이 에러코드를 사용하는 클래스 전부를 다시 컴파일 하고 다시 배치해야 한다.  

<br/>

### 반복하지 마라!

- 중복을 없애면 모듈 가독성이 크게 높아진다.

<br/>

### 구조적 프로그래밍

> " 데이크스트라는 모든 함수와 함수 내 모든 블록에 입구와 출구 하나만 존재해야 한다고 말했다. "

### 함수를 어떻게 짤까?

> " 글짓기와 비슷하다. (생각을 기록한 후 읽기 좋게 다듬는다)  
>   처음에는 길고 복잡하다.  
>   그 서투른 코드를 빠짐없이 테스트하는 단위 테스트 케이스를 만든다.  
>   그런다음 코드를 가다듬고, 함수를 만들고, 이름을 바꾸고, 중복을 제거한다.  
>   메서드를 줄이고 순서를 바꾼다. 때로는 클래스를 쪼개기도 한다.  
>   이 와중에도 코드는 항상 단위 테스트를 통과한다. "

<br/>

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 4장 주석

<br/>

<blockquote><p> " 우리에게 프로그래밍 언어를 치밀하게 사용해 의도를 표현할 능력이 있다면, 주석은 거의 필요하지 않으리라. 아니, 전혀 필요하지 않으리라. " </p></blockquote>

<blockquote><p> " 우리는 코드로 의도를 표현하지 못해, 그러니까 실패를 만회하기 위해 주석을 사용한다. " </p></blockquote>

<blockquote><p> " 주석을 달 때마다 자신에게 표현력이 없다는 사실을 푸념해야 마땅하다. " </p></blockquote>

<blockquote><p> " 주석이 언제나 코드를 따라가지는 않는다. 아니, 따라가지 못한다. " </p></blockquote>

<blockquote><p> " 진실은 한 곳에만 존재한다. 바로 코드다. 코드만이 자기가 하는 일을 진실되게 말한다. " </p></blockquote>

<br/>

### 주석은 나쁜 코드를 보완하지 못한다

코드에 주석을 추가하는 일반적인 이류는 **코드 품질이 나쁘기 때문** 이다.  
표현력이 풍부하고 깔끔하며 주석이 거의 없는 코드가,  
복잡하고 어수선하며 주석이 많이 달린 코드보다 훨씬 좋다.  

> " 자신이 저지른 난장판을 주석으로 설명하려 애쓰는 대신에 그 난장판을 깨끗이 치우는 데 시간을 보내라! "

<br/>


### 코드로 의도를 표현하라!

두 예제가 있다. 어느 쪽이 나은지는 한 눈에 알아볼 수 있다.

```java
// 직원에게 복지 혜택을 받을 자격이 있는지 검사한다.
if ((employee.flags & HOURLY_FLAG) &&
    (employee.age > 65))
```

vs

```java
if (employee.isEligibleForFullBenefits())
```

<br/>

### 좋은 주석

글자 값을 한다고 생각하는 주석:  

- 법적인 주석
    + 저작권 정보와 소유권 정보 등을 소스 파일 첫머리에 주석으로 표시
- 정보를 제공하는 주석
    + 기본적인 정보

```java
// 테스트 중인 Responder 인스턴스를 반환한다.
protected abstract Responder responderInstance(); 
```

또는

```java
// kk:mm:ss EEE, MMM dd, yyyy 형식이다.
Pattern timeMatcher = Pattern.compile(
    "\\d*:\\d*:\\d* \\w*,\\w* \\d*,\\d*");
```

위 주석은 코드에서 사용한 정규표현식이 시각과 날짜를 뜻한다고 설명한다.  

<br/>

- 의도를 설명하는 주석
    + (구현을 이해하게 도와주는 선을 넘어) 결정에 깔린 의도를 설명하는 주석이다.  
        다음 예제는 두 객체를 비교할 때 다른 어떤 객체보다 자기 객체에 높은 순위를 주기로 결정한다.  

```java
public int compareTo(Object o) {
    if (o instanceof WikiPagePath) {
        WikiPagePath p = (WikiPagePath) o;
        String compressedName = StringUtil.join(names, "");
        String compressedArgumentName = StringUtil.join(p.names, "");
        return compressedName.compareTo(compressedArgumentName);
    }
    return 1; // 오른쪽 유형이므로 정렬 순위가 더 높다.
}
```

<br/>

- 의미를 명료하게 밝히는 주석
    + 모호한 인수나 반환값은 그 의미를 읽기 좋게 표현하면 이해하기 쉬워진다.  
    + 일반적으로는 인수나 반환값 자체를 명확하게 만들면 더 좋겠지만, 인수나 반환값이  
        **표준 라이브러리나 변경하지 못하는 코드에 속한다면** 주석이 유용하다.

```java
public void testCompareTo() throw Exception {
    WikiPagePath a = PathParser.parse("PageA");
    WikiPagePath ab = PathParser.parse("PageA.PageB");
    WikiPagePath b = PageParser.parse("PageB");
    ...
    assertTrue(a.compareTo(a) == 0);      // a == a
    assertTrue(a.compareTo(b) != 0);      // a != b
    assertTrue(ab.compareTo(ab) == 0);    // ab == ab
    ...
}
```

그릇된 주석을 달아놓을 위험이 상당히 높다.  
위 주석이 올바른지 검증하기 쉽지 않다. (주석은 코드를 따라가지 않는다!)  
 
<br/>

- 결과를 경고하는 주석
    + 때로는 다른 프로그래머에게 결과를 경고할 목적으로 주석을 사용한다.

```java
// 여유 시간이 충분하지 않다면 실행하지 마십시오.
public void _testWithReallyBigFile() {
    whiteLinesToFile(10000000);
    
    response.setBody(testFile);
    response.setReadyToSend(this);
    String responseString = output.toString();
    assertSubString("Content-Length: 1000000000", responseString);
    assertTrue(bytesSent > 1000000000);
}
```

위 예제는 @Ignore 속성을 이용하여 테스트를 꺼버릴 수 있다..  
`@Ignore("실행이 너무 오래 걸림")`

<br/>

- TODO 추석
    + '앞으로 할 일'을 `// TODO` 주석으로 남겨두면 편하다.  
    + 더 이상 필요 없는 기능을 삭제하라는 알림
    + 누군가에게 문제를 봐달라는 요청
    + 더 좋은 이름을 떠올려 달라는 부탁
    + 앞으로 발생할 이벤트에 맞춰 코드를 고치라는 주의 등

```java
// TODO-MdM 현재 필요하지 않다.
// 체크아웃 모델을 도입하면 함수가 필요 없다.
protected VersionInfo makeVersion() throws Exception {
    return null;
}
```

그래도 TODO 로 떡칠한 코드는 바람직하지 않다.  
그러므로 주기적으로 TODO 주석을 점검해 없애도 괜찮은 주석은 없애라.

<br/>

- 중요성을 강조하는 주석

```java
...
String listItemContent = match.group(3).trim();
// 여기서 trim은 정말 중요하다. trim 함수는 문자열에서 시작 공백을 제거한다.
// 문자열에 시작 공백이 있으면 다른 문자열로 인식되기 때문이다.
new ListItemWidget(this, listItemContent, this.level + 1);
return buildList(text.substring(match.end()));
```

<br/>

- 공개 API
    + 설명이 잘 된 공개 API 는 유용하다.
    + 표준 자바 라이브러리에서 사용한 Javadocs 가 좋은 예다.
    + 여느 주석과 마찬가지로 Javadocs 역시 독자를 오도하거나, 그릇된 정보를 전달할 가능성이 존재한다.
    
<br/>

### 나쁜 주석

- 주절거리는 주석
    + 특별한 이유 없이 주석을 다는 행위
    
```java
public void loadProperties() {
    try {
        String propertiesPath = propertiesLocation + "/" + PROPERTIES_FILE;
        FileInputStream propertiesStream = new FileInputStream(propertiesPath);
        loadedProperties.load(propertiesStream);
    } 
    catch (IOException e) {
        // 속성 파일이 없다면 기본값을 모두 메모리로 읽어 들였다는 의미이다.
    }
}
```

catch 블록에 있는 주석은 무슨 뜻일까? (의미가 전해지지 않는다)  
`IOException` 이 발생하면 속성 파일이 없다는 뜻이란다.  
그러면 누가 모든 기본값을 읽어 들이는가?  
`loadedProperties.load()` 를 호출하기 전에 읽나?  
아니면 `loadedProperties.load()` 가 예외를 잡아 기본값을 읽어 들인 후 예외를 던져주는가?  
저자가 `catch` 블록을 비워놓기 뭐해서 몇 마디 덧 붙였을 뿐인가?  
**답을 알아내려면 다른 코드를 뒤져보는 수밖에 없다.**  
즉 독자와 제대로 소통하지 못하는 주석이다.  

<br/>

- 같은 이야기를 중복하는 주석

```java
// this.closed 가 true 일 때 반환되는 유틸리티 메서드다.
// 타임아웃에 도달하면 예외를 던진다.
public synchronized void waitForClose(final long timeoutMillis) throws Exception {
    if (!closed) {
        wait(timeoutMillis);
        if (!closed)
            throw new Exception("MockResponseSender could not be closed");
    }
}
```

헤더에 달린 주석이 같은 코드 내용을 그대로 **중복** 한다.  
이와 같은 주석은  
- 자칫하면 코드보다 주석을 읽는 시간이 더 오래 걸린다.  
- 주석이 코드보다 더 많은 정보를 제공하지 못한다.
- 실제로 코드보다 부정확해 함수를 대충 이해하고 넘어가게 만든다.

엔진 후드를 열어볼 필요가 없다며 고객에게 아양 떠는 중고차 판매원과 비슷하다.  

<br/>

아래는 쓸모없고 중복된 Javadocs 가 매우 많은 코드이다.  
이러한 같은 이야기를 중복하는 주석은 코드만 지저분하고 정신 없게 만든다.  

```java
public abstract class ContainerBase
    implements Container, Lifecycle, Pipeline,
    MBeanRegistration, Serializable {
    
    /**
     * 이 컴포넌트의 프로세서 지연값
     */
    protected int backgroundProcessorDelay = -1;
    
    /**
     * 이 컴포넌트를 지원하기 위한 생명주기 이벤트
     */
    protected LifecycleSupport lifecycle = new LifecycleSupport(this);
    
    /**
     * 이 컴포넌트를 위한 컨테이너 이벤트 Listener
     */
    protected ArrayList listeners = new ArrayList();
    
    ...
}
```

<br/>

- 오해할 여지가 있는 주석

```java
// this.closed 가 true 일 때 반환되는 유틸리티 메서드다.
// 타임아웃에 도달하면 예외를 던진다.
public synchronized void waitForClose(final long timeoutMillis) throws Exception {
    if (!closed) {
        wait(timeoutMillis);
        if (!closed)
            throw new Exception("MockResponseSender could not be closed");
    }
}
```

위에서 본 주석은 중복이 상당히 많으면서도 오해의 여지 또한 존재한다.  
- `closed` 가 `true` 로 변하는 **순간** 에 메서드는 (바로)반환되지 않는다. 
- `closed` 가 `true` **여야** 메서드는 반환된다. (즉시 반환이 아니라는 뜻)

누군가 **주석만 읽고** `closed` 가 `true` 로 변하는 **순간** (즉시)함수가 반환되리라는 생각으로 경솔하게 함수를 호출할지도 모른다.  

<br/>

- 의무적으로 다는 주석
    + 모든 함수에 Javadocs 를 달거나 모든 변수에 주석을 달아야 한다는 규칙은 어리석다.  

```java
/**
 * @param title CD 제목
 * @param author CD 저자
 * @param track CD 트랙 숫자
 * @param durationInMinutes CD 길이(단위: 분)
 */
public void addCD(String title, String author, int tracks, int durationInMinutes) {
    ...
}
```

<br/>

- 이력을 기록하는 주석
    + 예전에는 모듈 첫머리에 변경 이력을 기록하고 관리하는 관례가 바람직했다.  
        당시에는 소스 코드 관리 시스템이 없었으니까.  
        하지만 이제는 혼란만 가중할 뿐이다. 완전히 제거하는 편이 좋다.

<br/>

- 있으나 마나 한 주석
    + 너무 당연한 사실을 언급하며 새로운 정보를 제공하지 못하는 주석

```java
/**
 * 기본 생성자
 */
protected AnnualDateRule() {}

/** 월 중 일자 */
private int dayOfMonth;

/**
 * 월 중 일자를 반환한다.
 * 
 * @return 월 중 일자
 */
public int getDayOfMonth() {
    return dayOfMonth;
}
```

위와 같은 주석은 지나친 참견이다.  
결국은 코드가 바뀌면서 주석은 거짓말로 변한다.  

<br/>

아래 예시를 보자

```java
private void startSending() {
    try {
        doSending();
    }
    catch (SocketException e) {
        // 정상. 누군가 요청을 멈췄다.
    }
    catch (Exception e) {
        try {
            response.add(ErrorResponder.makeExceptionString(e));
            response.closeAll();
        }
        catch (Exception e1) {
            // 이게 뭐야!
        }
    }
}
```

첫 번째 주석은 적절해 보인다.  
`catch` 블록을 무시해도 괜찮은 이유를 설명하는 주석이다.  
하지만 두 번째 주석은 전혀 쓸모가 없다.  

<br/>

다음과 같이 코드 구조를 개선할 수 있다.

```java
private void startSending() {
    try {
        doSending();
    }
    catch (SocketException e) {
        // 정상. 누군가 요청을 멈췄다.
    }
    catch (Exception e) {
       addExceptionAndCloseResponse(e);
    }
}

private void addExceptionAndCloseResponse(Exception e) {
    try {
        response.add(ErrorResponder.makeExceptionString(e));
        response.closeAll();
    }
    catch (Exception e) {  }
}
```

마지막 `try/catch` 블록을 독자적인 함수로 만드는 데 노력을 쏟았어야 했다.

<br/>

- 무서운 잡음
    + 때로는 Javadocs 도 잡음이다.  
        아래 나오는 (오픈 소스 라이브러리 코드)Javadocs 는 어떤 목적을 수행할까? 닶: 없다.  
        단지 문서를 제공해야 한다는 잘못된 욕심으로 탄생한 잡음일 뿐이다.  

```java
/** The name. */
private String name;

/** The version. */
private String version;

/** The licenceName. */
private String licenceName;

/** The version. */
private String info;
```

아래 version 은 복붙 하다가 생긴 오류인가 보다.  
결국 주석 작성에 주의를 기울이지 않는다면, 읽는 사람은 아무 이익을 얻을 수 없다.  

<br/>

- 함수나 변수로 표현할 수 있다면 주석을 달지 마라

```java
// 전역 목록 <smodule> 에 속하는 모듈이 우리가 속한 하위 시스템에 의존하는가?
if (smodule.getDependSubsystems().contains(subSysMod.getSubSystem()))
```

위 코드에서 주석을 없애고 다시 표현하면 다음과 같다.

```java
ArrayList moduleDependees = smodule.getDependSubsystems();
String ourSubSystem = subSysMod.getSubSystem();
if (moduleDependees.contains(ourSubSystem))
```

위와 같이 주석이 필요하지 않도록 코드를 개선하는 편이 더 좋다.

<br/>

- 위치를 표시하는 주석

```java
// Actions ////////////////////////////////////
```

일반적으로 위와 같은 주석은 가독성만 낮춘다.  
극히 드물게 유용한 경우도 있지만 자주 사용하면 독자가 흔한 잡음으로 여겨 무시한다.  

<br/>

- 닫는 괄호에 다는 주석
    + 중첩이 심하고 장황한 함수라면 의미가 있을지도 모르지만,  
        작고 캡슐화된 함수에는 잡음일 뿐이다.  
        **닫는 괄호에 주석을 달아야겠다고 생각이 든다면 대신에 함수를 줄이려 시도하자.**  

<br/>

- 공로를 돌리거나 저자를 표시하는 주석

```java
/* 길동이 추가함 */
```

소스 코드 관리 시스템을 이용하도록 하자.  
현실적으로 이런 주석은 그냥 오랫동안 코드에 방치되어 점차 부정확하고 쓸모없는 정보로 변하기 쉽다.  

<br/>

- 주석으로 처리한 코드
    + 주석으로 처리된 코드는 다른 사람들이 지우기를 주저한다.  
        이유가 있어 남겨놓았으리라 생각해서 (중요한 코드일까봐)지우면 안 된다고 생각한다.  
        이 역시 코드 관리 시스템이 우리를 대신해 코드를 기억해준다.  
        그냥 코드를 삭제해라. 잃어버릴 염려 없다.  

<br/>

- HTML 주석
    + 소스 코드에서 HTML 주석은 혐오 그 자체다.  
        주석에 HTML 태그를 삽입해야 하는 책임은 프로그래머가 아니라 도구가 져야 한다.  

<br/>

- 전역 정보
    + 근처에 있는 코드만 기술하라.  
        코드 일부에 주석을 달면서 **시스템의 전반적인 정보를 기술하지 마라.**  

```java
/**
 * 적합성 테스트가 동작하는 포트: 기본값은 <b>8082</b>
 * 
 * @param fitnessePort
 */
public void setFitnessePort(int fitnessePort) {
    this.fitnessePort = fitnessePort;
}
```

위 주석은 심하게 중복되었다는 사실 외에도 기본 포트 정보(함수에서 알 필요 없는)를 기술한다.  
하지만 함수 자체는 포트 기본값을 전혀 통제하지 못한다.  
즉 시스템 어딘가에 있는 다른 함수를 설명하고 있다.  
**(어딘가에 있는)포트 기본값 설정하는 코드가 변해도 아래 주석이 변하리라는 보장은 전혀 없다.**  

<br/>

- 너무 많은 정보
    + 주석에다 흥미로운 역사나 관련 없는 정보를 장황하게 늘어놓지 마라.  
        독자에게 불필요하며 불가사의한 정보일 뿐이다.  

<br/>

- 모호한 관계
    + 주석과 주석이 설명하는 코드는 **둘 사이 관계가 명백** 해야 한다.  

```java
/*
 * 모든 픽셀을 담을 만큼 풍부한 배열로 시작한다(여기에 필터 바이트를 더한다).
 * 그리고 헤더 정보를 위해 200바이트를 더한다.
 */
this.pngBytes = new byte[((this.width + 1) * this.height * 3) + 200];
```

여기서 필터 바이트란 무엇일까?  
주석을 다는 목적은 **코드만으로 설명이 부족해서** 다.  
그런데 위에서는 주석 자체가 다시 설명을 요구한다.  

<br/>

- 함수 헤더
    + 짧고 한가지만 수행하며 이름을 잘 붙인 함수가  
        주석으로 헤더를 추가한 함수보다 훨씬 좋다.  

<br/>

- 비공개 코드에서 Javadocs
    + (공개 API 가 아닌)시스템 내부에 속한 클래스에 Javadocs 를 생성할 필요 없다.  

<br/>

### 예제

다음은 에라스토테네스의 체 알고리즘을 구현한 코드를 리팩터링하는 과정을 보여준다.  

<br/>

**변경 전**

```java
/**
 * 이 클래스는 사용자가 지정한 최대 값까지 소수를 생성한다. 사용된 알고리즘은
 * 에라스토테네스의 체다.
 * <p>
 * 에라스토테네스: 기원전 276년에 리비아 키레네에서 출생, 기원전 194년에 사망
 * 지구 둘레를 최초로 계싼한 사람이자 달력에 윤년을 도입한 사람.
 * 알렉산드리아 도서관장을 역임.
 * </p>
 * 알고리즘은 상당히 단순하다. 2에서 시작하는 정수 배열을 대상으로
 * 2의 배수를 모두 제거한다. 다음으로 남은 정수를 찾아 이 정수의 배수를 모두 지운다.
 * 최대 값의 제곱근이 될 때까지 이를 반복한다.
 * 
 * @author 홍길동
 * @version 2021.04.03
 */
import java.util.*;

public class GeneratePrimes {
    /**
     * @param maxValue 는 소수를 찾아낼 최대 값
     */
    public static int[] generatePrimes(int maxValue) {
        if (maxValue >= 2) {    // 유일하게 유효한 경우
            // 선언
            int s = maxValue + 1;   // 배열 크기
            boolean[] f = new boolean[s];
            int i;
            
            // 배열을 참으로 초기화
            for (i = 0; i < s; i++)
                f[i] = true;
            
            
            // 소수가 아닌 알려진 숫자를 제거
            f[0] = f[1] = false;
            
            // 체
            for (i = 2; i < Math.sqrt(s) + 1; i++) {
                if (f[i]) { // i 가 남아 있는 숫자라면 이 숫자의 배수를 구한다.
                    for (j = 2 * i; j < s; j += i) 
                        f[j] = false;   // 배수는 소수가 아니다.
                }
            }
            
            // 소수 개수는?
            int count = 0;
            for (i = 0; i < s; i++) {
                if (f[i])
                    count++;    // 카운트 증가
            }
            
            int[] primes = new int[count];
            
            // 소수를 결과 배열로 이동한다.
            for (i = 0, j = 0; i < s; i++) {
                if (f[i])   // 소수일 경우에
                    primes[j++] = i;
            }
            
            return primes;
        }
        else // maxVlue < 2
            return new int[0];  // 입력이 잘못되면 비어 있는 배열을 반환한다.
    }
}
```

개선될 점을 대략 파악하면 다음과 같다.
- 너무 많은 정보 (헤더에 역사설명 부분)
    + `에라스토테네소: 기원전 276년에 리비아 키레네에서 출생` 등
- 의무적으로 다는 Javadocs 주석
    + `@author 홍길동` 등
- 모호한 class 명
    + `GeneratePrimes` 보다는 `Generator` 가 좀 더 명시적
- 코드가 바뀌면 덩달아 바뀌어야 하는 주석들
    + `@param maxValue 는 소수를 찾아낼 최대 값`
- 모호한 변수 네이밍
    + `int s = ...`
    + `boolean[] f = ...`
    + `int count = ...` 등
- 명시적인 함수로 대체
    + `if (maxValue >= 2) // 유일하게 유효한 경우` 등
    + `generatePrimes()` 메서드 내 대부분은 함수로 쪼개야 한다. (함수가 여러가지 일을 함)
- 증복된 내용
    + `count++; // 카운트 증가` 등

위와 같은 문제점들을 리팩터링 해보자.  

<br/>

**리팩터링 결과**

```java
/**
 * 이 클래스는 사용자가 지정한 최대 값까지 소수를 구한다.
 * 알고르짐은 에라스토테네스의 체다.
 * 2에서 시작하는 정수 배열을 대상으로 작업한다.
 * 처음으로 남아 있는 정수를 찾아 배수를 모두 제거한다.
 * 배열에 더 이상 배수가 없을 때까지 반복한다.
 */

public class PrimeGenerator {
    
    private static boolean[] crossedOut;
    private static int[] result;
    
    public static int[] generatePrimes(int maxValue) {
        if (maxValue < 2)
            return new int[0];
        else {
            uncrossIntegersUpTo(maxValue);
            crossOutMultiples();
            putUncrossedIntegersIntoResult();
            return result;
        }
    }
    
    private static void uncrossIntegersUpTo(int maxValue) {
        crossedOut = new boolean[maxValue + 1];
        for (int i = 2; i < crossedOut.length; i++)
            crossedOut[i] = false;
    }
    
    private static void crossOutMultiples() {
        int limit = determineIterationLimit();
        for (int i = 2; i <= limit; i++) {
            if (notCrossed(i))
                crossOutMultiplesOf(i);
        }
    }
    
    private static int determineIterationLimit() {
        // 배열에 있는 모든 배수는 배열 크기의 제곱근보다 작은 소수의 인수다.
        // 따라서 이 제곱근보다 더 큰 숫자의 배수는 제거할 필요가 없다.
        double iterationLimit = Math.sqrt(crossedOut.length);
        return (int) iterationLimit;
    }
    
    private static boolean notCrossed(int i) {
        return crossedOut[i] == false;
    }
    
    private static void putUncrossedIntegersIntoResult() {
        result = new int[numberOfUncrossedIntegers()];
        for (int j = 0, i = 2; i < crossedOut.length; i++)
            if (notCrossed(i))
                result[j++] = i;
    }
    
    private static int numberOfUncrossedIntegers() {
        int count = 0;
        for (int i = 2; i < crossedOut.length; i++)
            if (notCrossed(i))
                count++;
        
        return count;
    }
}
```

<br/>

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 5장 형식 맞추기

<br/>

> 프로그래머라면 형식을 깔끔하게 맞춰 코드를 짜야 한다.

코드 컨벤션과 같은 코드 스타일 가이드는 코드의 가독성을 증가시키고 일관된 코드 스타일을 유지할 수 있게 도와준다.  

<br/>

### 형식을 맞추는 목적

> 코드 형식은 의사소통의 일환이다.
 
오랜 시간이 지나 원래 코드의 흔적을 더 이상 찾아보기 어려울 정도로 코드가 바뀌어도  
맨 처음 잡아놓은 구현 스타일과 가독성 수준은 **유지보수 용이성**과 **확장성**에 계속 영향을 미치게 된다.  
원할한 소통을 장려하는 코드 형식에 대해 알아보자.

<br/>

### 적절한 행(세로) 길이 유지

자바에서 파일크기는 클래스 크기와 밀접하다.  
일반적으로 큰 파일보다 작은 파일이 이해하기 쉽다.  

<br/>

#### 신문 기사 처럼 작성하라

소스 파일도 신문 기사와 비슷하게 작성한다.  
- 이름은 간단하면서도 설명이 가능하게 짓는다.
- 이름만 보고도 올바른 모듈을 살펴보고 있는지 아닌지를 판단할 정도로 신경 써서 짓는다.
- 소스 파일 첫 부분은 고차원 개념과 알고리즘을 설명한다.
- 아래로 내려갈수록 의도를 세세하게 묘사한다.
- 마지막에는 가장 저차원 함수와 세부 내역이 나온다.

<br/>

#### 개념은 빈 행으로 분리하라

일련의 행 묶음은 완결된 생각 하나를 표현한다.  
생각 사이에는 빈 행을 넣어 분리해야 마땅하다.  
빈 행은 새로운 개념을 시작한다는 시각적 단서이다.

```java
public class Example {
    public void exampleMethod1(Argument argument1, Argument argument2) { 
        doSomething1(argument1); doSomething2(argument2); ...} 
    public void exampleMethod2(Argument argument1, Argument argument2) { 
        doSomething1(argument1); doSomething2(argument2);
        ...}
    public void exampleMethod3(Argument argument1, Argument argument2) { 
        doSomething1(argument1); doSomething2(argument2);
        ...
    }
}
```

위 코드 보다는 아래 코드가 가독성이 좋다.

```java
public class Example {
    
    public void exampleMethod1(Argument argument1, Argument argument2) { 
        doSomething1(argument1); 
        doSomething2(argument2); 
        ...
    } 
    
    public void exampleMethod2(Argument argument1, Argument argument2) { 
        doSomething1(argument1);
        doSomething2(argument2);
        ...
    }
    
    public void exampleMethod3(Argument argument1, Argument argument2) { 
        doSomething1(argument1);
        doSomething2(argument2);
        ...
    }
}
```

<br/>

#### 세로 밀집도

줄바꿈이 개념을 분리한다면 세로 밀집도는 연관성을 의미한다.  
서로 밀접한 코드 행은 세로로 가까이 놓여야 한다는 뜻이다.

```java
public class ReporterConfig {
    /**
     * 리포터 리스너의 클래스 이름
     */
    private String m_className;
    
    /**
     * 리포터 리스너의 속성
     */
    private List<Property> m_properties = new ArrayList<Property>();
    public void addProperty(Property property) {
        m_properties.add(property);
    }
}
```

같은 코드라도 위 코드는 머리와 눈을 더 움직여야 한다.

```java
public class ReporterConfig {
    
    private String m_className;
    private List<Property> m_properties = new ArrayList<Property>();
    
    public void addProperty(Property property) {
        m_properties.add(property);
    }
}
```

<br/>

#### 수직 거리

함수 연관 관계와 동작 방식을 이해하려고 이 함수에서 저 함수로 오가며 소스 파일을 위아래로 뒤지는 뺑뺑이를 돈 경험이 있는가?  
이 조각 저 조각이 어디에 있는지 찾고 기억하느라 시간과 노력을 소모한다.

<br/>

**연관성**이란 한 개념을 이해하는 데 다른 개념이 중요한 정도다.  
연관성이 깊은 두 개념이 멀리 떨어져 있으면 코드를 읽는 사람이 소스 파일과 클래스를 여기저기 뒤지게 된다.  

<br/>

- 변수 선언  
    변수는 사용하는 위치에 최대한 가까이 선언한다.

- 인스턴스 변수  
    인스턴스 변수는 클래스 맨 처음에 선언한다.  
    변수 간에 세로로 거리를 두지 않는다.  
    잘 설계한 클래스는 많은 클래스 메서드가 인스턴스 변수를 사용하기 때문이다.

- 종속 함수  
    한 함수가 다른 함수를 호출한다면 두 함수는 세로로 가까이 배치한다.  
    또한 가능하다면 호출하는 함수를 호출되는 함수보다 **먼저** 배치한다.  
    
- 개념적 유사성  
    어떤 코드는 서로 끌어당긴다. 개념적인 친화도가 높기 때문이다.  
    비슷한 동작을 수행하는 일군의 함수가 좋은 예다.
    
<br/>

#### 세로 순서

호출되는 함수를 회출하는 함수보다 나중에 배치한다.  
그러면 소스 코드 모듈이 고차원에서 저차원으로 자연스럽게 내려간다.  

<br/>

신문 기사와 마찬가지로 가장 중요한 개념을 가장 먼저 표현한다.  
그러면 독자가 소스 파일에서 첫 함수 몇 개만 읽어도 개념을 파악하기 쉬워진다.

<br/>

### 가로 형식 맞추기

#### 가로 공백과 밀집도

가로로는 공백(띄어쓰기)을 사용해 밀접한 개념과 느슨한 개념을 표현한다.  
공백을 넣으면 한 개념이 아니라 별개로 보인다.  
연산자 우선순위를 강조하기 위해서도 공백을 사용한다.

```java
private static double determinant(double a, double b, double c) {
    return b*b - 4*a*c;
}
```

<br/>

#### 들여쓰기

범위로 이뤄진 계층을 표현하기 위해 우리는 코드를 들여쓴다.  
들여쓰는 정도는 계층에서 코드가 자리잡은 수준에 비례한다.  

<br/>

떄로는 `if` 문, 짧은 `while` 문, 짧은 함수에서 들여쓰기 규칙을 무시하고픈 유혹이 생긴다.  
하지만 한 행에 범위를 뭉뚱그린 코드를 피해야 한다.

```java
public class CommentWidget extends TextWidget {
    public CommentWidget(ParentWidget parent, String text) {super(parent,text);}
    public String render() throws Exception {return "";}
}
```

```java
public class CommentWidget extends TextWidget {
    
    public CommentWidget(ParentWidget parent, String text) {
        super(parent, text);
    }
    
    public String render() throws Exception {
        return "";
    }
}
```

<br/>

#### 가짜 범위

세미콜론(;)은 새 행에다 제대로 들려써서 넣어준다.  
그렇게 하지 않으면 눈에 띄지 않는다. 

```java
while(dis.read(buf, 0, readBufferSize) != -1)
;
```

<br/>

### 팀 규칙

팀은 한 가지 규칙에 합의해야 한다. 그리고 모든 팀원은 그 규칙을 따라야 한다.  
그래야 소프트웨어가 일관적인 스타일을 보인다.  

<br/>

좋은 소프트웨어 시스템은 읽기 쉬운 문서로 이뤄진다는 사실을 기억해야 한다.  
스타일은 일관적이고 매끄러워야 한다. 한 소스 파일에서 봤던 형식이 다른 소스 파일에도 쓰이리라는 **신뢰감**을 독자에게 줘야 한다.  

<br/>

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 6장 객체와 자료 구조

<br/>

### 자료 추상화

두 코드는 2차원 점을 표현한다.

- 코드1  
    ```java
    public class Point {
        public double x;
        public double y;
    }
    ```

- 코드2  
    ```java
    public interface Point {
        double getX();
        double getY();
        void setCartesian(double x, double y);
        double getR();
        double getTheta();
        void setPolar(double r, double theta);
    }
    ```

아래 인터페이스로 짜여진 코드2는 직교좌표계를 사용하는지 극좌표계를 사용하는지 알 길이 없다.  
그럼에도 불구하고 자료구조를 명백하게 표현한다.  
클래스 메서드가 접근 정책을 강제하고 좌표를 읽을 때는 각 값을 개별적으로 읽어야 한다.  

<br/>

반면 코드1은 확실히 직교좌표계를 사용한다.  
개별적으로 좌표값을 읽고 설정하게 강제하며 구현을 노출한다.  

> 변수를 private 으로 선언하더라도 각 값마다 조회(getter) 함수와 설정(setter) 함수를 제공한다면 구현을 외부로 노출하는 셈이다.

<br/>

변수 사이에 함수라는 계층을 넣는다고 구현이 저절로 감춰지지는 않는다.  
구현을 감추기 위해선 **추상화**가 필요하다.  
추상 인터페이스를 제공해 사용자가 구현을 모른 채 자료의 핵심을 조작할 수 있어야 진정한 의미의 클래스이다.

<br/>

다른 두 코드를 살펴보자.

- 코드3  
    ```java
    public interface Vehicle {
        double getFuelTankCapacityInGallons();
        double getGallonsOfGasoline();
    }
    ```

- 코드4  
    ```java
    public interface Vehicle {
        double getPercentFuelRemaining();
    }
    ```

코드3 은 자동차 연료 상태를 구체적인 숫자 값으로 알려준다.  
반면 코드4 는 자동차 연료를 백분율이라는 추상적인 개념으로 알려준다.  

<br/>

코드3 은 두 함수가 변수값을 읽어 반환할 뿐이라는 사실이 거의 확실하다.  
반면 코드4 는 정보가 어디서 오는지 전혀 드러나지 않는다.

<br/>

즉, 자료를 세세하게 공개하기보다는 추상적인 개념으로 표현하는 편이 좋다.  
인터페이스나 조회/설정 함수만으로는 추상화가 이뤄지지 않는다!  
개발자는 객체가 포함하는 자료를 표현할 가장 좋은 방법을 심각하게 고민해야 한다.

<br/>

### 자료/객체 비대칭

객체는 추상화 뒤로 자료를 숨긴 채 자료를 다루는 함수만 제공한다.  
반면 자료구조는 자료를 그대로 공개하며 별다는 함수는 제공하지 않는다.  
(두 정의는 본질적으로 상반된다)

<br/>

다음은 절차적인 도형 클래스이다.  
각 도형 클래스는 간단한 자료구조이다.

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

public class Geometry {
    public final double PI = Math.PI;
    
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
        }
        throw new NoSuchShapeException();
      }
}
```

객체 지향적 사고로 위 코드를 바라본다면 어설퍼보인다.  
만약 저 코드에 `perimeter()` 함수를 추가하고 싶으면?  
도형 클래스는 아무도 영향을 받지 않는다. 그저 함수를 추가하고 구현하기만 하면 된다.  

<br/>

하지만 새 자료구조(도형)를 추가하고 싶다면?  
`Geometry` 클래스에 속한 함수를 모두 고쳐야만 한다.  

<br/>

이번에는 객제 지향적인 코드를 살펴보자.  

```java
public class Square implements Shape{

  private Point topLeft;
  private double side;

  @Override
  public double getArea() {
    return side * side;
  }
}

public class Rectangle implements Shape{

  public Point topLeft;
  public double height;
  public double width;

  @Override
  public double getArea() {
    return height * width;
  }
}

public class Circle implements Shape{

  public Point center;
  public double radius;

  @Override
  public double getArea() {
    return radius * radius * Math.PI;
  }
}
``` 

여기에 새 도형을 추가해도 기존 함수에 아무런 영향을 미치지 않는다.  
반면 새 함수를 추가하고 싶다면 도형 클래스 전부를 고쳐야 할 것이다.  

<br/>

복잡한 시스템을 짜다 보면 새로운 함수가 아니라 새로운 자료 타입이 필요한 경우가 생긴다.  
이때는 클래스와 객체 지향 기법이 가장 적합하다.  

<br/>

반면 새로운 자료타입이 아니라 새로운 함수가 필요한 경우도 생긴다.  
이때는 절차적인 코드와 자료 구조가 좀 더 적합하다.  

<br/>

어느 방식이 필요할지는 주어진 상황에 맞게 편견 없이 최적의 해결책을 선택하는것이 현명하다.

<br/>

### 디미터 법칙

디미터 법칙은 잘 알려진 휴리스틱으로, 모듈은 자신이 조작하는 객체의 속사정을 몰라야 한다는 법칙이다.  

> 낯선 사람은 경계하고 친구랑만 놀라는 의미이다.

즉, 객체는 조회 함수로 내부 구조를 공개하면 안된다는 의미다.  
좀 더 정확히 표현하면 "클래스 C 의 메서드 f 는 다음과 같은 객체의 메서드만 호출해야 한다"

- 클래스 C
- f 가 생성한 객체
- f 인수로 넘어온 객체
- C 인스턴스 변수에 저장된 객체

<br/>

#### 기차 충돌 코드

```java
final String outputDir = ctxt.getOptions().getScratchDir().getAbsolutePath();
```

흔히 위와 같은 코드를 기차 충돌 코드라 부른다.  
일반적으로 조잡하다 여겨지는 방식이므로 피하는 편이 좋다.

<br/>

위 코드는 다음과 같이 펼칠 수 있다.

```java
Options opts = ctxt.getOptions();
File scratchDir = opts.getScratchDir();
final String outputDir = scratchDir.getAbsolutePath();
```

그렇다면 위 코드는 디미터 법칙을 잘 지키고 있는 것일까?  
잘 살펴보면 `ctxt` 객체가 `Options` 를 포함하며, `Options` 가 `ScratchDir` 을 포함하고,  
`ScratchDir` 는 `AbsolutePath` 를 포함한다는 사실을 알 수 있다.  

<br/>

위 예제가 디미터 법칙을 위반하는지 여부는 `ctxt`, `Options`, `ScratchDir` 가 객체인지 아니면 자료구조인지에 달려있다.  
객체라면 내부 구조를 숨겨야 하므로 확실히 디미터 법칙을 위반하게 된다.  
자료 구조라면 당연히 내부 구조를 노출하므로 디미터 법칙이 적용되지 않는다.  

<br/>

그런데 위 예제는 조회(get블라블라) 함수를 사용하는 바람에 혼란을 일으킨다.  
자료구조 였더라면 아래와 같이 표현됐을 것이다.

```java
final String outputDir = ctxt.options.scratchDir.absolutePath;
```

<br/>

자료 구조는 무조건 (함수 없이) 공개 변수만 포함하고  
객체는 비공개 변수와 공개 함수를 포함한다면 문제는 훨씬 간단해진다.  
하지만 자료 구조에도 설정 함수를 정의하라 요구하는 프레임워크와 표준(`bean` 과 같은..)이 존재한다.

<br/>

#### 잡종 구조

이런 혼란으로 말미암아 떄때로 절반은 객체, 절반은 자료구조인 잡종 구조가 나온다.  
공개 조회/설정(getter/setter) 함수는 비공개 변수를 그대로 노출한다.  
덕택에 다른 함수가 절차적인 프로그래밍의 자료 구조 접근 방식처럼 비공개 변수를 사용하고픈 유혹(기능 욕심)에 빠지기 십상이다.

<br/>

#### 구조체 감추기

만약 `ctxt`, `Options`, `ScratchDir` 가 객체라면 앞서 코드 예제처럼 줄줄이 사탕으로 엮어서는 안 된다.  
(객체라면 내부 구조를 감춰야 하므로)  

<br/>

`ctxt` 가 객체하면 **'뭔가를 하라고'** 말해야지 속을 드러내라고 (자신의 내부를)말하면 안 된다.  
임시 디렉터리의 절대 경로가 왜 필요할까? 얻어서 어디에 쓸려고?  
다음은 같은 모듈에서 (한참 아래로 내려가서) 가져온 코드이다.  

```java
String outFile = outputDir + "/" + className.replace('.', '/') + ".class";
FileOutputStream fout = new FileOutputStream(outFile);
BufferedOutputStream bos = new BufferedOutputStream(fout);
```

절대 경로를 얻으려는 이유가 임시 파일을 생성하기 위한 목적이라는 사실이 드러났다.  
그렇다면 `ctxt` 객체에 임시 파일을 생성하라고 시키면 어떨까?  

```java
BufferedOutputStream bos = ctxt.createScratchFileStream(classFileName);
```

확실히 객체에게 맡기기 적당한 임무에다 내부 구조 또한 드러내지 않으며,  
모듈에서 해당 함수는 자신이 몰라야 하는 여러 객체를 뒤적뒤적 탐색할 필요가 없어지게 된다.  
따라서 디미터 법칙을 위반하지 않게 된다.

<br/>

### 자료 전달 객체(DTO)

자료 구조체의 전형적인 형태는 공개 변수만 있고 함수가 없는 클래스다.  
이런 자료 구조체를 때로는 자료 전달 객체(DTO; Data Transfer Object)라 한다.

<br/>

주로 데이터베이스와 통신하거나 소켓에서 받은 메시지의 구문을 분석할 때 유용하다.  
좀 더 일반적인 형태는 '빈(bean)' 구조이다. 빈은 비공개 변수를 조회/설정 함수로 조작한다.  
일종의 사이비 캡슐화로, 일부 OO 순수주의자나 만족시킬 뿐 별다른 이익을 제공하지 않는다.

<br/>

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 7장 오류 처리



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 8장 경계



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 9장 단위 테스트



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 10장 클래스



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 11장 시스템



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 12장 창발성(創發性)



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 13장 동시성



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 14장 점진적인 개선



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 15장 JUnit 들여다보기



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 16장 SerialDate 리팩터링



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 17장 냄새와 휴리스틱



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>
