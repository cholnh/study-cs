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

<blockquote><p> " 우리는 코드로 의도를 표현하지 못해, 그러니까 **실패를 만회하기 위해** 주석을 사용한다. " </p></blockquote>

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

    + 위에 제시간 주석은 코드에서 사용한 정규표현식이 시각과 날짜를 뜻한다고 설명한다.  

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

    + 그릇된 주석을 달아놓을 위험이 상당히 높다.  
    + 위 주석이 올바른지 검증하기 쉽지 않다. (주석은 코드를 따라가지 않는다!)  
 
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

    + 위 예제는 @Ignore 속성을 이용하여 테스트를 꺼버릴 수 있다..  
        `@Ignore("실행이 너무 오래 걸림")`

<br/>

- TODO 추석
    + '앞으로 할 일'을 //TODO 주석으로 남겨두면 편하다.  

```java
// TODO-MdM 현재 필요하지 않다.
// 체크아웃 모델을 도입하면 함수가 필요 없다.
protected VersionInfo makeVersion() throws Exception {
    return null;
}
```

    + 필요하다 여기지만 당장 구현하기 어려운 업무를 기술한다.
        + 더 이상 필요 없는 기능을 삭제하라는 알림
        + 누군가에게 문제를 봐달라는 요청
        + 더 좋은 이름을 떠올려 달라는 부탁
        + 앞으로 발생할 이벤트에 맞춰 코드를 고치라는 주의 
        + 등등... 에 유용하다

    + 그래도 TODO 로 떡칠한 코드는 바람직하지 않다.  
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
    

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 5장 형식 맞추기



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 6장 객체와 자료 구조



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
