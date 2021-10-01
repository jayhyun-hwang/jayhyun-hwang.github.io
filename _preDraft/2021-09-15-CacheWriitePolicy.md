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

캐시와 여러가지 캐시 쓰기 정책(Cache Write Policy)에 대해서 알아보자.

### 2. 캐시란

일반적으로, 캐시는 저장소에 더 편리하고 빠르게 접근하기 위한 **파사드 컴포넌트**(facade component)이다. 캐시 저장소는 더 빠르지만, 비용이 크다. 때문에 **적게 효율적으로 써야한다**. (캐시 저장소를 시스템 디자인 차원에서 구성하기도 한다.)

**캐시의 목적은 레이턴시와 처리량을 개선하는 것이다.** 하드웨어와 소프트웨어 모두 캐시를 가질 수 있다. 예를 들면, 하드웨어에는 CPU cache가 있으며, 소프트웨어 차원에는 휘발성 메모리(RAM)을 사용해 비휘발성 메모리(Secondary storage, 예를 들면 SSD)에서 데이터를 캐시하는 page cache가 있다.

`파사드(facade): 클라이언트가 복잡한 시스템에 단순하게 접근하게 하는 레이어를 두는 패턴, 사용하기 쉬운 중앙 집중된 ingerface를 제공한다.(facade는 새로운 동작을 추가하지 않고 단지 interface에 있는 메소드를 호출한다.)  `



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