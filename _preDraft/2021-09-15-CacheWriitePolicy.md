---
layout: post
title: "캐시와 캐시 쓰기 정책(Cache Write Policy)"
subtitle: ""
author: "jay"
header-style: text
comments: true
tags:
- OS  
- Computer Science
---

### 1. 개요

캐시의 정의와 여러가지 캐시 쓰기 정책(Cache Write Policy)에 대해서 알아보자.

### 2. 캐시란

일반적으로, 캐시는 저장소에 더 편리하고 빠르게 접근하기 위한 **파사드 컴포넌트**(facade component)이다. 캐시 저장소는 데이터 접근속도가 더 빠르지만, 비용이 크다. 이는 마치 CPU가 보조기억장치(예: SSD)와 주기억장치(예: RAM)에 접근하는 속도와 용량에 대한 것과 비슷하다. 주기억장치(RAM)의 데이터에 접근하는 것이 더 빠르지만, 용량은 주로 더 적다. 이와 비슷하게 캐시 데이터도 더 빠른 접근속도에 대한 trade off로 용량에 대한 비용이 크기 때문에 저장소를 더 **적게 효율적으로 써야한다**.(캐시 저장소를 시스템 디자인 차원에서 구성하기도 한다.)

**캐시의 목적은 레이턴시와 처리량을 개선하는 것이다.** 하드웨어와 소프트웨어 모두 캐시를 가질 수 있다. 예를 들면, 하드웨어에는 CPU cache가 있으며, 소프트웨어 차원에는 휘발성 메모리(RAM)을 사용해 보조기억장치(Secondary storage, 예를 들면 SSD)에서 데이터를 캐시하는 page cache가 있다.

작업 시 요청한 데이터가 캐시 저장소에 있을 경우 cache hit가 일어나며,  반대의 경우 cache miss가 일어난다. 

그리고 캐시 저장소에 있는 데이터가 자용되지 않거나, 부피가 너무 커 저장하기 비효울적이라고 판단 될 경우, **캐시 데이터 축출(Eviction)**이 일어난다.(이는 캐시 데이터의 만료(Expiration)와는 무관하다.)

캐시 데이터 축출은 캐시 데이터 무효화(Cache Invalid)와도 구분된다. 캐시 데이터 무효화란, 백업 저장소(원본)에서 데이터를 새로 고칠 수 있는 경우(예를 들면, Cache Flush), 기존의 캐시 데이터가 무효화되어 삭제되는 걸 의미한다. 

`파사드(facade): 클라이언트가 복잡한 시스템에 단순하게 접근하게 하는 레이어를 두는 패턴, 사용하기 쉬운 중앙 집중된 ingerface를 제공한다.(facade는 새로운 동작을 추가하지 않고 단지 interface에 있는 메소드를 호출한다.) `

`Cache Flush: 백업 저장소의 변경 사항을 캐시 저장소에 다시 써주는 걸 말한다.(캐시와 원본을 동기화 시킨다고 볼 수 있다.)`

### 3. 캐시 쓰기 정책

캐시 쓰기 정책은 캐



> Baeldung의 동의하에 글을 번역하고 정리하였습니다.
>
> 참고 글: <https://www.baeldung.com/cs/cache-write-policy>{:target="_blank"}

> 참고 링크:
>
> <https://free-strings.blogspot.com/2016/04/adapter-decorator-facade-proxy.html>{:target="_blank"}
>
> <>{:target="_blank"}
>
> <>{:target="_blank"}
>
> <>{:target="_blank"}