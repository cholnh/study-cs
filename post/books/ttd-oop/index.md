## 테스트 주도 개발로 배우는 객체지향 설계와 실천

<img src="https://github.com/cholnh/study-cs/blob/main/assets/images/cs/tn-ttd-oop.jpg" width="250" />

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

[ [← back](https://github.com/cholnh/study-cs/blob/main/post/books/index.md#개발-서적) | [↑ top](https://github.com/cholnh/study-cs/blob/main/post/books/ttd-oop/index.md#테스트-주도-개발로-배우는-객체지향-설계와-실천) ]

<br/>

<br/>

## 1부 서론

<br/>

## 1장 테스트 주도 개발의 핵심은 무엇인가?

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
