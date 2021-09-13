---
layout: post
title: "Python의 List, Tuple 자료형"
subtitle: "List와 Tuple의 차이, 내장 함수들"
author: "jay"
header-style: text
comments: true
tags:
  - Python
---

### 파이썬의 List, Tuple

파이썬의 배열이라고 할 수 있다. `List`는 객체 **변경이 가능**하고, `Tuple`은 정적 선언 후 **수정이 불가**하다.

### List의 pop(), del, 슬라이스

pop(), del == call by reference. 삭제하고, 원객체를 변형

slice[:] == 원본을 유지하고 복사, 반환