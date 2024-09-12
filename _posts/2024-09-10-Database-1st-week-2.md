---
title: 데이터베이스 1주차 - (2)
date: 2024-09-10 18:52:45 +09:00
categories: [3학년 2학기, 데이터베이스]
tags: [단기 계획, 3학년 2학기, 데이터베이스]
mermaid: true
---

이번 글에선 데이터베이스 1주차 내용 중 **'온라인 처리 시스템부터 제어 기능'**까지 설명해드리려고 합니다.

1주차 강의에 생각보다 많은 내용이 담겨 읽기에 불편하실 것 같아 1주차 - (1)과 (2)로 나누려고 합니다! 😅

혹시 이전 글을 안읽어보신 분은 **'데이터베이스 1주차 - (1)'**을 먼저 읽어보시면 좋을 것 같아요!

## **데이터 처리 시스템**

### **일괄 처리 시스템 (Batch Processing System)**

1. **사전 준비 작업 필요**

- 원시 데이터(raw data)의 수집
- 분류 정리하여 파일(file)에 수록

2. **시스템 중심 처리 방법**

- 높은 시스템 성능 : 모든 파일에 대해 작업을 진행하기 때문에 CPU 사용률이 증가
  → 사용자 입장에서 오래 걸리는 작업임을 인지하고 있으므로 비교적 성능이 낮은 하드웨어(Hardware, 이하 HW)를 사용해도 상관없다.

3. **순차 접근 방법 이용 업무에 유리** (ex. OMR 답안지 일괄 처리)

![Desktop View](/assets/img/database/batch-processing-system.jpg){: width="500" height="500" }

### **온라인 처리 시스템 (Online Processing System)**

1. **실시간 처리** : 어떤 대상에게 있어 최종 목적을 달성하기 위해 소비해야 하는 시간 내에 연산을 완료하는 것
   (ex) 인간이 영상을 이산적인 정지 화면이 아닌 연속적인 영상으로 한 장면을 인지하기 위해 1초에 16개의 정지 화면 필요
   → **1/16초 이내**에 다음 화면이 보이면 실시간 스트리밍 영상이라 할 수 있다.
2. **사용자 중심 처리방법**
   - **낮은 시스템 성능** : 요청이 집중적으로 들어올 떄의 빠른 처리를 위해 비싼 컴퓨터를 샀지만, 이후로는 유휴 시간이 대부분이므로 구축 비용 대비 사용률이 떨어지므로 시스템 성능이 낮다.
   - **높은 처리 비용** : 앞서 언급한 비싼 컴퓨터 구매 시 발생하는 비용
3. **통신 제어기 (Communication Controller)** 필요
4. **보수, 유지, 회복의 오버헤드**

![Desktop View](/assets/img/database/online-processing-system.jpg){: width="500" height="500" }

### **분산 처리 시스템** (Kubernetes에서의 단일 / 다중 클러스터)

데이터가 여러 노드 혹은 클러스터에 분산되어 있지만, 사용자는 마치 하나의 PC 스토리지를 쓰는 듯한 UX를 제공하는 시스템

### 예시

- 분산 처리기(Dispersed processor) : 컴퓨터 시스템
- 분산 데이터베이스 (Distributed Database)
- 통신 네트워크 (Communication Network)
  → 클라이언트 / 서버 시스템 운영 형태

## 데이터베이스 (Database)

한 조직(Enterprise)의 여러 응용 시스템들이 공용(Shared)하기 위해 통합(Integration), 저장한 운영(Operation) 데이터의 집합

- **공용 데이터 (Shared Data)** : 한 조직의 여러 응용 시스템들이 공동으로 소유, 유지, 이용하는 데이터
- **통합 데이터 (Integrated Data)**
  - 최소의 중복 (Minimal Redundancy)
  - 통제된 중복 (Controlled Redundancy)
- **저장 데이터 (Stored Data)**
  - 컴퓨터가 접근 가능한 저장 매체에 저장
  - 디스크, 테이프 등 → 백업용
- **운영 데이터 (Operational Data)** → 일종의 **'메타 데이터(Metadata)'**
  → 한 조직의 고유 기능을 수행하기 위해 필요한 데이터

### **데이터베이스의 특성**

1. **실시간 접근성** (Real-Time Accessibilities)
   → 시스템이 최종 목적을 달성하기 위해 소비하는 제한 시간 내에 연산을 완료하는 것
2. **계속적인 변화** (Continuous Evolution) → 동적 특성

- 갱신 (Update)
- 삽입 (Insert)
- 삭제 (Delete)

3. **동시 공용** (Concurrent Sharing)
   → 여러 사용자가 동시에 사용
4. **내용에 의한 참조** (Content Reference)
   → 데이터의 위치나 주소가 아닌 내용에 따라 참조

### **개체와 관계**

**논리적 구성요소 (Logical Components)** : '데이터베이스 = {개체(Entities), 관계(Relationships)}'

![Desktop View](/assets/img/database/database-property.jpg){: width="500" height="500" }

**개체 (Entities)**

- 표현하려는 유무형 정보의 객체(Object)
- 정보의 단위(Unit)
- 하나 이상의 속성(Attribute)으로 구성 → 데이터의 가장 작은 논리적 단위
- 개체 집합 (Entity Set)
- 일반 레코드와 대응

![Desktop View](/assets/img/database/entity.jpg){: width="500" height="500" }

**관계 (Relationship)**

- **속성 관계(Attribute Relationship)** : 개체 내 관계(Infra-Entity) → 특성(properties)
- **개체 관계(Entity Relationship)** : 개체 간 관계(Inter-Entity)

![Desktop View](/assets/img/database/relationship.jpg){: width="500" height="500" }

### **논리적 구조 & 물리적 구조**

**논리적 구조 (Logical Organization)**

- 사용자의 관점에서 본 데이터의 개념적 구조(Conceptual Structure)
- 데이터의 논리적 배치(Logical Structure)
- 논리적 레코드(Logical Record)

**물리적 구조 (Physical Organization)**

- 저장 관점에서 본 데이터의 물리적 배치(Physical Allocation)
- 저장장치에 저장된 데이터의 실제 구조(Actual Structure)
- 추가 정보를 포함 → **'인덱스, 포인터 체인, 오버플로 구역'** 등
- 저장 레코드(Stored Record)

![Desktop View](/assets/img/database/logical-physical-organization.jpg){: width="500" height="500" }

오늘 글은 여기까지입니다. 이번 글도 설명이 조금 부족한 것 같아서 조금 더 다듬어서 추석 지나기 전 업데이트하도록 하겠습니다. 읽어주셔서 감사합니다!
