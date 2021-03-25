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

> " 코드가 왜 그렇게 되었을까? 좋은 코그다 어째서 순식간에 나쁜 코드로 전락할까? 우리는 온갖 이유를 들이댄다. 원래 설계를 뒤집는 방향으로 요구사항이 변했다고 불편한다. 일정이 촉박해 제대로 할 시간이 없었다고 한탄한다. 멍청한 관리자와 조급한 고객과 쓸모없는 마케팅 부서와 전화기 살균제 탓이라 떠벌인다. 하지만 잘못은 전적으로 우리 프로그래머에게 있답니다. 우리가 전문가답지 못했기 때문입니다. "

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

### 검색하기 쉬운 이름을 사용하라

### 인코딩을 피하라

> " 문제 해결에 집중하는 개발자에게 인코딩은 불필요한 정신적 부담이다. "

<br/>

### 자신의 기억력을 자랑하지 마라

> " 코드를 읽으면서 변수 이름을 자신이 아는 이름으로 변환해야 한다면 그 변수 이름은 바람직하지 못하다. (변수 i, j, k는 괜찮다) "

<br/>

> " 전문가 프로그래머는 명료함이 최고라는 사실을 이해한다. "

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

### 한 개념에 한 단어를 사용하라

> " 추상적인 개념 하나에 단어 하나를 선택해 이를 고수한다. "

똑같은 메서드를 클래스 마다 `fetch`, `retrieve`, `get` 으로 제각각 부르면 혼란스럽다.

<br/>

### 말장난을 하지 마라

집합에 값 하나를 추가하는 `add`메서드 vs 기존 값 두 개를 더하거나 이어서 새로운 값을 만드는 `add`메서드  
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

> " 클래스, 함수, 이름 공간에 의미를 넣어 맥락을 부여한다. "

<br/>

> " 모든 방법이 실패하면 마지막 수단으로 접두어를 붙인다. "

<br/>

### 불필요한 맥락을 없애라

<br/>

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 3장 함수



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 4장 주석



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
