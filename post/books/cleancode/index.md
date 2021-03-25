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



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/cleancode/index.md#clean-code) ]

<br/>

## 2장 의미 있는 이름



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
