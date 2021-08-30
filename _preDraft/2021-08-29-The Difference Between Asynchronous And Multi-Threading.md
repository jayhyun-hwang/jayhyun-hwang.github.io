---
layout: post
title: "비동기 처리와 멀티 스레딩의 차이"
subtitle: "The Difference Between Asynchronous And Multi-Threading"
author: "jay"
header-style: text
comments: true
tags:
  - OS
  - Computer Science
---

### 1. 소개

비동기 프로그래밍과 멀티 스레딩 프로그래밍에 대해 알아보고, 차이점을 비교해보자.

### 2. 비동기 프로그래밍이란

비동기적 모델에서는 **여러 일이 동시에 발생할 수 있다.** 프로그램은 실행시간이 긴 함수를 실행할 때, **그 함수의 실행 흐름을 막지(block) 않고**, 프로그램을 계속 실행한다. 그리고 그 함수가 끝났을 때, 프로그램은 실행결과에 접근한다. 

예를 들면, 네트워크를 통해 2개의 파일을 가져와 결합하는 프로그램이 있다고 했을 때

![sync-1024x658](\img\in-post\sync-1024x658.png)

비동기 시스템에서는, 





> Baeldung의 동의하에 글을 번역하고 정리하였습니다.
>
> 참고 글: <https://www.baeldung.com/cs/async-vs-multi-threading>{:target="_blank"}