---
layout: post
title: "프로세스 제어 블록"
subtitle: "운영체제 커널의 자료구조"
author: "jay"
header-style: text
comments: true
tags:
  - Computer Science
  - OS
---

> **Baeldung**의 동의하에 글을 번역하고 정리하였습니다.
>
> 참고 글: <https://www.baeldung.com/cs/process-control-block>{:target="_blank"}

### 1. 소개

컴퓨터 시스템은 여러 프로그램들을 동시에 실행한다. 이 병렬실행을 통해, 컴퓨터는 연산을 더 많이 처리하고, 사용자 경험은 좋아진다. 이렇게 여러 프로그램을 실행한다는 개념은 **운영 체제에 의해 구현**된다.

이 글에서는, 프로세스가 작동하는데 필요한 PCB(Process Control Block - 프로세스 제어 블록)의 개념에 대해 설명할 것이다.

### 2. 프로세스의 개념

**프로세스란 실행중인 프로그램이다.** 예를 들어, 우리가 java 어플리케이션을 작성하고 디스크에 저장(write)할 때, 이것을 프로그램이라고 하며, 이것은 수동적 개체이다(passive entity). 하지만, 프로그램을 실행할 때, 운영 체제는 java 프로세스를 생성한다. **프로세스는 실행중일 때 활성화되는  행위 엔티티(active entity)이다.**

![img](https://www.baeldung.com/wp-content/uploads/sites/4/2020/06/ProcessContent-1-189x300-1.png)

위의 이미지는 프로세스와 구성요소를 나타낸다.(왼쪽 부분은 메모리이다.)

Text 부분은 낮은 memory offset에서 시작된다. 프로세스의 힙과 스택은 프로세스의 메모리 요구에 따라 증가할 수 있다.

### 3. Process Control Block(프로세스 제어 블록)

프로세스 제어 블록(PCB)는 운영 체제(OS)의 프로세스를 나타낸다. Task Control Block이라고 부르기도 한다. PCB는 **한 프로세스에 관련된 정보를 저장하는 저장소(repository)이다.**

PCB는 다음과 같은 정보를 담고 있다.

#### 3.1 Process State(프로세스 상태)

프로세스 상태는 운영체제 내 프로세스의 상태를 나타낸다. 프로세스 상태로는 **new, ready, running, waiting 그리고 terminated(종료됨)**상태가 있다.

#### 3.2 Program Counter(프로그램 카운터, PC)

프로세스는 CPU에 의해 선형적으로 실행되는 명령어들을 포함하고 있다. 프로그램 카운터(PC)는 이 프로세스에 대해 **다음에 실행될 명령어의 주소**를 나타낸다.

#### 3.3. CPU Registers(레지스터)

레지스터는 프로세스의 상태정보를 가지는 작은 비트 메모리이다. 레지스터는 컴퓨터 아키텍처에 따라 크기와 유형이 변할 수 있다. 레지스터는 누산기(accumulators), 인덱스 레지스터(index registers), 조건코드(condition-code) 정보, 범용 레지스터(general-purpose registers), 그리고 스택 포인터(stack pointers)를 포함한다. 

**레지스터는 실행중인 프로세스가 중단되었을 때, 프로세스의 상태 정보를 저장한다.** 이를 통해 스케줄러가 프로세스를 예약하여 해당 프로세스를 다시 이어서 실행할 수 있다.

#### 3.4. 추가 통계

- CPU-scheduling Information(CPU 스케줄링 정보): 