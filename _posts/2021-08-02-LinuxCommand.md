---
layout: post
title: "Linux Command"
subtitle: '리눅스 명령어 정리'
author: "jay"
header-style: text
comments: true
tags:
  - Linux
  - OS
---
## Linux command

리눅스 커널을 사용할 때 기본적인 조작을 위해 알아야 할 명령어들을 정리했다.

- 찾기

  - find /(전체에서) -name {name}

    ```shell
    find / -name {name}
    ```

  - find ./(현재 경로 하위에서) -name {name} -type f(파일)/d(디렉토리)

    ```shell
    find ./ -name {directory name}} -type d
    find ./ -name {file name} -type f
    ```

- 복사, 이동

  - cp {복사할 file} {복사할 경로 또는 복사하여 생성할 파일 이름}

    ```shell
    cp 폴더2/abc.txt ../../폴더1/
    ```

  - cp -r {복사할 디렉토리( . )} {목적 디렉토리}

    ```shell
    cp -r . ../abc/
    ```

  - mv {이동 시킬 디렉토리} {목적 디렉토리}

    ```shell
    mv * ../abc
    ```

  **현재 디렉토리의 모든 파일을 선택 = * // 하위디렉토리의 모든 파일 선택 = /* **

- 위치 확인(현재 디렉토리)

  ```shell
  pwd
  ```

- 루트 디렉토리(/)로 이동

  ```shell
  cd /
  ```

- 이전 디렉토리로 이동

  ```shell
  cd -
  ```

- 이전 명령어

  ```shell
  !!
  sudo !!
  !! -type d
  !-2 -type f
  ```

- net-tools 설치

  ```shell
  apt-get install net-tools
  ```

- systemctl 명령어

  - 서비스 확인

  ```shell
  # {xxx}문자열이 들어가는 서비스 항목 모두 조회(list)
  systemctl list-units --type=service | grep xxx
  ```

  - 서비스 재시작

  ```shell
  systemctl status firewalld.service
  systemctl stop firewalld
  pkill -f firewalld
  systemctl start firewalld
  ```

  - 방화벽 서비스 등록

  ```shell
  systemctl enable firewalld
  systemctl start firewalld
  
  firewall-cmd --permanent --service={service name} --add-port=9901/tcp
  
  firewall-cmd --reload
  systemctl restart firewalld
  ```

  - 방화벽 포트 등록

  ```shell
  firewall-cmd --add-port=9019/tcp --permanentfirewall-cmd --reloadsystemctl restart firewalld
  ```

- 방화벽 확인

  ```shell
  #90문자열이 들어간 ip테이블 조회(List)iptables -L | grep 90
  ```

- 공통 방화벽 open

  ```shell
  firewall-cmd --zone=public --add-port=400/tcp --permanent
  ```

- firewall-cmd 명령어

  ```shell
  #서비스 방화벽상에 등록하기
  firewall-cmd --new-service={service name}
  firewall-cmd --service={service name} --add-port=9019/tcp --permanent
  firewall-cmd --reload
  systemctl restart firewalld
  ```

- 방화벽 공용포트 삭제하기

  ```shell
  firewall-cmd --zone=public --remove-port=9019/tcp --permanent
  firewall-cmd --reload
  systemctl restart firewalld
  ```

- 재부팅

  ```shell
  shutdown -r now
  ```