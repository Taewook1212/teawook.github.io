---
title: 실행 컨텍스트(Execution Context)란?
date: YYYY-MM-DD HH:MM:SS +09:00
categories: [깃헙 블로그, 도메인]
tags: [태그1, 태그2, 태그3]
toc: true
---

#

## 실행 컨텍스트(Execution Context)란?

코드가 실행되는 곳으로 현재 실행 중인 코드의 환경, 변수, 함수 등의 정보를 담고 있는 객체라고 할 수 있습니다.

javaScript 코드의 실행 과정은 일반적으로 두 단계로 나눌 수 있습니다.

스크립트 준비 단계와 스크립트 실행 단계입니다.

요약하면

- 스크립트 준비 단계에서 코드의 문법적 유효성을 체크하는 파싱을 하고

스코프와 식별자에 대한 정보를 담는 렉시컬 환경을 생성합니다.

그리고 실행 단계에서는 이렇게 생성된 실행 컨텍스트를 스택에 쌓아가며

코드를 실행합니다. 변수와 함수의 호이스팅이 발생합니다.

이후 실행단계를 거칩니다.

## 1. 스크립트 준비 단계

1. 파싱
   1. 인터프리터 엔진이 토근화 하여 토큰 단위로 나눔.
   2. 문법 검사하여 AST 생성
2. 렉시컬 환경 생성(Lexical Environment Creation)
   1. 스코프(블랙,함수)와 식별자(변수,함수,속성,매개변수)에 대한 정보를 담는 환경
   2. 전역 범위와 함수 범위에서 각각 렉시컬 환경 생성
   3. 실행되기 전이라 변수와 함수가 실제로 초기화 되지 않는 상태.
3. 실행 컨텍스트 생성(Execution Context Creation)
   1. 전역 컨텍스트 생성, 함수가 호출될 때마다 해당 함수 컨텍스트 생성.
   2. 변수 객체, 스코프 체인, this 값 등이 설정
   3. 이 시점에서 변수와 함수의 초기화가 이루어지고, 호이스팅(Hoisting)이 발생합니다.

## 2. 스크립트 실행 단계

1. 코드가 실행되고 실행 컨텍스트 스택이 실행되고 변수 할당, 함수 호출 등이 이루어 지며
   마지막으로 실행컨텍스트 스택에서 팝되고, 컨텍스트가 종료가 됩니다.

> 변수와 함수의 호이스팅(Hoisting)
>
> 1. 호이스팅은 변수와 함수 선언문이 실행 컨텍스트의 변수 객체에 끌어 올려지는 현상
> 2. var는 `undefined` 로 초기화 되고, let과 const는 [let 변수이름 = 까지만 올려져서] `is not defined` (죽음의 TDZ Temparal Dead Zone )로 초기화 됩니다. 함수는 전체가 끌어 올려지며 실제 함수의 정의 전에 호출할 수 있게 됩니다.

![1](https://github.com/Taewook1212/js-homework/assets/147236247/7fc1a925-a339-43ef-84a9-7a311db084e1)
![2](https://github.com/Taewook1212/js-homework/assets/147236247/0b19a8d2-cdc5-43bc-a945-b8b6c23fbc9d)
![3](https://github.com/Taewook1212/js-homework/assets/147236247/38434474-ce2b-4dbd-a5e5-db62d15ff90c)
![4](https://github.com/Taewook1212/js-homework/assets/147236247/00b96f62-a56f-4888-afe1-4ae6df77a4a0)

위에서 부터 순서대로 함수가 호출될 때마다 해당 함수 컨텍스트 생성. 전역 컨텍스트 생성,
그 후 스택에 쌓이는 그림.

Call Stack과 Web APIs , Event Loop 의 관계는 다음 정리~!
