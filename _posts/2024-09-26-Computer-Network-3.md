---
title: 컴퓨터네트워크 4주차 - (수정 및 정리 필요)
date: 2024-10-29 12:20:45 +09:00
categories: [3학년 2학기, 컴퓨터네트워크]
tags: [단기 계획, 3학년 2학기, 컴퓨터네트워크]
mermaid: true
---

이번 글에서는 컴퓨터네트워크 4주차 내용에 대해 정리해보려고 합니다.

## **Chapter.2 - Application Layer**

### **목표**

- 전송층 서비스 모델
- 클라이언트-서버 패러다임
- p2p 패러다임

- HTTP
- SMTP, IMAP
- DNS
- Video Streaming systems, CDNs

- Socket API

### **네트워크 앱 생성**

- 프로그램을 (서로 다른)엔드 시스템들이 네트워크를 통해 통신하도록 작성 → (Ex) 브라우저 SW로 통신하는 웹 서버 SW
- 네트워크-코어 장치를 위한 소프트웨어로의 작성 불필요
  - 네트워크-코어 장치들은 사용자 애플리케이션을 실행하지 않음
  - 엔드 시스템 상의 애플리케이션들이 빠른 앱 개발 및 전파를 가능하게 함

![Desktop View](/assets/img/computer-network/creating-network-app.jpg){: width="500" height="500" }

### **클라이언트-서버 패러다임**

- **서버 (Server)**

  - 항상 켜져있는 호스트
  - 영구 IP 주소 사용 → (Ex) 데이터 센터

- **클라이언트 (Client)**

  - 서버에 접근하고, 통신하는 주체
  - 간헐적으로 연결되어 있음 → 서버에 요청할 것이 있어야만 통신을 시도하기 때문
  - 동적 IP 주소를 가짐
  - 직접적인 연결을 통한 통신을 하지 않음

- 예시
  - HTTP
  - IMAP
  - FTP

### **P2P 아키텍처**

- 항시 작동하는 서버가 아님
- 무작위의 엔드 시스템이 직접 통신하기 위함
- 각 peer가 어떤 peer에게 요청하거나, 자신에게 들어온 요청에 대한 결과를 되돌려줌
  - 자기 확장성(Self Scalability): 새로운 peer들이 새로운 서비스 자체 뿐만 아니라 새로운 서비스 요구를 가져옴
- peer는 간헐적으로 연결되고 IP주소를 바꿈 → 관리가 복잡함
- (Ex) P2P file sharing → BitTorrent

### **프로세스 통신 (Process Communication)**

- 프로세스: 호스트에서 동작하는 프로그램
- 동일 호스트 안에서, 두 개의 프로세스들은 프로세스 간 통신(inter-process communication(OS에 의해 정의됨))을 사용함
- 서로 다른 호스트에 존재하는 프로세스들은 메세지를 주고 받음으로써 통신함
  - client & server
    - client process: 통신을 시작하는 프로세스
    - server process: 연락 받길 기다리는 프로세스
- P2P 아키텍처를 사용하는 애플리케이션은 Client, Server 프로세스를 모두 가지고 있다.
  → 기기간 직접적 연결이 형성되기 때문에 자신이 보내는 주체이자 요청 받는 대상이 될 수 있다.

### **소켓 (Socket)**

- 프로세스는 소켓을 통해(으로부터) 메세지를 송신(수신)
- 소켓은 마치 문과 같다
  - 송신 프로세스는 수신 프로세스 측 소켓으로의 메세지 전달을 위해 반대측 전송 인프라에 의존

### **Addressing Processes**

메세지를 수신하기 위해선 프로세스는 반드시 '식별자(Identifier)'를 가지고 있어야 한다.

- 호스트 장치는 유일한 32비트 IP 주소를 가진다
  - 호스트의 IP주소는 각각의 프로세스를 구별하기에 충분한가?
    → 그렇지 않다. 많은 프로세스들이 같은 호스트 상에서 동작하기 때문이다.
- 식별자는 호스트 상의 프로세스와 연관된 IP 주소와 포트 번호를 포함하고 있다.
- (EX)
  - HTTP Server: 80
  - Mail Server: 25

### **Things that Application-Layer Protocol defines**

- 교환되는 메세지의 종류
-

![Desktop View](/assets/img/computer-network/client-server-paradigm.jpg){: width="500" height="500" }

**static IP address VS. permanent IP address**
IPv4 → 32 bits
IPv6 → 64 bits

현실적으로 모든 유저에게 영구 IP를 제공할 수 없음 → 이로 인해 각자의 로컬 환경의 고유 IP를 만들어주기 위해 내부적으로 localhost라는 개념을 만듦 (127.0.0.1)
→ 따라서, 영구 IP의 경우 서버와 같은 특정 장치에서만 사용되도록 함

p2p: 장치간 통신이 다른 임의의 장치를 거치지 않고 직접 통신하는 형태

intra: 같은 네트워크의 장치 간 통신
inter: 다른 네트워크 장치 간의 통신

p2p 와 server-client는 겉으로 보기엔 같지만, 항상 같은 것은 아니고, 특정 상황이 전제되어야 함

socket이 사용되는 이유: 각 장치마다 고유한 IP가 하나 씩 할당되는데, 이 하나의 IP가지고는 해당 장치에서 실행될 각 프로세스들을 구별할 수 없다. 따라서 각각의 프로세스 별 소켓을 두어 구별한다.

HTTP 서버를 위한 포트번호를 모두가 80으로 사용하지만, 식별자(identifier)와 IP를 가지고 서로 다름을 구별할 수 있다.

소켓이 port번호일 순 있으나, port번호 자체가 소켓이 될 순 없다. → 소켓이 좀 더 광범위한 개념의 식별자

RFC: Request For Comments

why protocol?
→ 서로 다른 환경의 장치들이 통신을 하기 위해선 같은 규칙을 가지고 소통을 해야만 내용에 착오가 생기지 않기 때문
→ 각각의 네트워크가 그들만의 표준(standard)를 가지고 내부에서 소통하기 때문에 수많은 다른 각각의 표준에 대해 상호 통신 가능한 규약이 필요

proprietary protocol: 단일 단체 및 개인만이 가지는 통신 (Ex) 스카이프, 줌, 웹엑스 등

_데이터 통신 교과서 참고_
data integrity (데이터 무결성) → 데이터에 오류가 있으면 안되는 특성

- 특정 애플리케이션들은 100%의 데이터 전송률 보장이 요구됨
- 다른 애플리케이션들은 데이터 전송에 조금 손실이 있어도 수용 가능함

timing

- 특정 애플리케이션들은 '효율적'이기 위해 낮은 지연이 필요

throughput (처리율)

- 특정 애플리케이션들은 '효율적'이기 위해 요구되는 최소한의 처리율이 존재
- 다른 애플리케이션들은 처리율과 무관함

security (보안)

- 암호화, 데이터 무결성 등

UDP: 송수신자간 연결 없이도 통신하는 기술
→ 상대방이 수신 가능한 상태가 아니어도 보내버림
→ 만약 상대방이 수신 불가능할 정도로 바쁘다면, 상대방은 수신된 해당 데이터를 무시함

SIP: Session Initiation Protocol

Vanilla TCP & UDP sockets

- 암호화 과정 X
- 소켓을 통해 cleartext 형태의 PW가 인터넷을 통해 이동함

Transport Layer Security (TLS)

- 암호화된 TCP 연결을 제공
- 데이터 무결성
- 엔드포인트 인증

### **Web & HTTP**

- HTTP는 '스테이트리스(Stateless)'다.
  - 서버는 이전 클라이언트의 요청들에 대한 정보를 가지고 있지 않음
  - ![Desktop View](/assets/img/computer-network/protocol.jpg){: width="500" height="500" }

오늘 설명은 여기까지입니다. 긴 글 읽어주셔서 감사합니다! 😌
