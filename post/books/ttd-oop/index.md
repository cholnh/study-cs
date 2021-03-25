## 테스트 주도 개발로 배우는 객체지향 설계와 실천

<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/cs/tn-ttd-oop.png" width="250" />

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) ]

<br/>

<br/>

## Index
- [들어가면서](#들어가면서)
- 1부 [서론](#1부-서론)
    + 1장 [테스트 주도 개발의 핵심은 무엇인가?](#1장-테스트-주도-개발의-핵심은-무엇인가?)
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
- **불확실한 변화를 예측하려면 경험이 늘어남에 따라 불확실성을 해결하는 데 도움이 될 프로세스가 필요하다.**  

<br/>

### 피드백은 가장 기본적인 도구다

- 경험에 의거한 피드백
    + 팀에는 반복적인 확동 주기가 필요하다. 
    + 각 주기마다 양과 질에 관한 피드백을 받는다.
- 배포는 현실에서 자신이 내린 가정을 검사할 기회이며, 배포하지 않고는 피드백이 완전해지지 않는다.
- **중첩된 고리형 시스템**으로 피드백 주기를 적용하라
    + 짝 프로그래밍, 단위 테스트, 인수 테스트, 일별 회의, 반복 주기, 출시 등...
    + 중첩된 각 고리마다 팀의 산출물이 경험에 의거한 피드백으로 드러나 팀에서는 오류나 오해를 발견하고 수정함.
    + 고리는 서로를 강화함 (안쪽에서 뭔가 모순되는 것이 바깥쪽에서 포착됨)
    + 안쪽 고리는 **기술적 세부 사항**에 집중 (단위 코드의 역할, 시스템 나머지 부분과의 통합 여부)
    + 바깥쪽 고리는 **조직과 팀**에 집중
- 피드백을 일찍 받을수록 좋다
- 점진적이고 반복적인 개발
    + 점진적인 개발에서는 모든 계층과 구성 요소를 구축한 다음 그것들을 마지막에 통합하는 대신 시스템을 **기능별**로 구축.
    + 각 기능은 시스템 전 구간에 이르는 '**조각**'으로 구현됨.
    + 시스템은 언제나 통합된 상태이며 배포할 준비가 되어 있음.
    + 반복적인 개발은 계속해서 충분한 상태에 이를 때까지 **피드백에 응답**해 **기능 구현**을 다듬는다.
    
<br/>

### 변화를 돕는 실천법



[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 2장 객체를 활용한 테스트 주도 개발

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

## 3장 도구 소개

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
