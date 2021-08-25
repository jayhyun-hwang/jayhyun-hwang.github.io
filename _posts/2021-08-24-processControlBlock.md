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

#### 3.4. 추가 정보

- CPU 스케줄링 정보(***CPU-scheduling Information***): 스케줄러는 실행할 프로세스들에게 CPU자원을 할당하는 역할을 한다.(Scheduling)  스케줄러는 CPU가 어떤 프로세스를 실행할 지에 대한 우선순위를 정한다. 때문에 프로세스는 스케줄링에 필요한 우선순위(process priority), scheduling queue information, 그 외의 다양한 스케줄링 파라미터들을 가지고 있다.

- 메모리 관리 정보(***Memory-Management information***): 프로세스 실행는 실행할 때 메모리가 필요하고, 메모리 관련 정보(memory-related statistics)를 유지해야 한다. 이 정보에는 **기본 레지스터 및 제한 레지스터에 관한 정보(base and limit register information), 페이지(page) and 세그먼트 테이블(segment tables)**, 등이 포함된다.

- ***Accounting Information***: Accounting Information는 부기 데이터(bookkeeping data)를 측정한다.

  *부기 데이터(bookkeeping data): CPU 사용시간, 제한 시간, 계정 번호, 작업 번호(PID) 등의 데이터*

- I/O 상태 정보(***I/O status information***): 프로세스에 할당 된 I/O 장치, 열린 파일 목록 등

### 4. 문맥 전환에서 PCB의 역할(Role of PCB in Context Switch)

PCB는 프로세스의 문맥 전환(Context Switch)에서 중요한 역할을 한다.

간혹 인터럽트(interrupt signals) 또는 운영체제 호출(operating system calls)등의 프로세스가 다른 프로세스의 실행을 중단시키고 자원을 선점한다. 이때, 운영 체제(OS)는 중단된 프로세스의 실행 정보(통계)를 그 프로세스의 PCB에 저장한다. 그렇게 프로세스가 나중에 이어서 실행될 수 있다.

문맥 전환(Context Switch) 중 어떤 일이 발생하는지 보면,

![img](https://www.baeldung.com/wp-content/uploads/sites/4/2020/06/ProcessContent-Context-Switch-1-300x284-1.png)

1. 처음에는 P0 프로세스가 실행 중이고, 중단이 발생한다.
2. 이에 대한 반응으로, 운영 체제는 P0의 컨텍스트를 저장하고, 실행을 중지한다.
3. 그 다음, 운영 체제는 다른 프로세스 P1의 PCB를 로드하고 실행을 시작한다.
4. 잠시 후, P1도 중단 신호를 받는다.
5. 운영 체제는 P1의 PCB 컨텍스트를 저장하고, 실행을 중지한다.
6. 그 다음, 운영 체제는 P0의 PCB를 로드하고, 이전 상태에서 실행을 재개한다.

### 5. 결론

프로세스 제어블록(PCB)에 대해 알아봤다. PCB의 개념과 운영 체제에서 PCB의 역할, 그리고 PCB의 구성 요소에 대해 알아봤으며, 문맥 전환에서 PCB의 역할에 대해서도 살펴봤다.