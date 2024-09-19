---
title: 소프트웨어공학 1주차 - (2)
date: 2024-09-20 15:29:10 +09:00
categories: [3학년 2학기, 소프트웨어공학]
tags: [단기 계획, 3학년 2학기, 소프트웨어공학]
mermaid: true
---

이번 글에선 소프트웨어공학 1주차 내용 중 2회차 내용에 대해 설명해드리려고 합니다.

소프트웨어 구조는 초기에 펌웨어의 형태로 모놀리틱(Monolithic, 저의 글 중 마이크로서비스 관련 설명에 있습니다!)한 소프트웨어와 하드웨어로만 구성되어 있었습니다. 그러나, 하나로 묶여있던 요소들이 애플리케이션, 미들웨어, 운영체제(Operating System, 이하 OS)로 점점 분리되다가, 이제는 클라우드 네이티브 컴퓨팅이 도입되면서 애플리케이션은 SaaS, 미들웨어와 OS는 PaaS, 하드웨어는 IaaS 형태로 제공되기 시작했습니다.

- **SaaS(Software as a Service) : 사용자가 별도의 설치 없이 인터넷을 통해 애플리케이션을 제공하는 서비스**
- **PaaS(Platform as a Service) : 애플리케이션을 개발, 실행, 관리할 수 있는 플랫폼을 클라우드 환경에서 제공하는 서비스**
- **IaaS(Infrastructure as a Service) : 가상화된 컴퓨팅 리소스를 클라우드를 통해 제공하는 서비스**

## **모델 기반의 소프트웨어 개발 (Model-Based SW Development, MBSD)**

- 모델링이 선행되고, 구현이 진행됩니다.
- **모델링 (Modeling)**
  - 모델을 구성하는 것
  - **모델(Model) : 특정 목적을 가진 물리적 시스템을 추상화한 것**

### **통상적인 소프트웨어 개발 프로세스**

- 모델링 : **분석(Analysis) + 설계(Design)**
- **구현(Implementation)**
  - 하위 시스템 분해
    - 컴포넌트 식별 (Component Identification)
    - 노드 할당 (Node Allocation)
  - 작업 구조화 (Task Structuring)
  - 번역 (Translation)
  - 통합 (Integration)

### **Analysis Vs. Design**

- **분석 (Analysis)**
  - 문제 영역의 모델을 공식화하는 것 → **'무엇을 할 것인가?'에 포커싱**
- **설계 (Design)**
  - 분석 모델을 어떻게 구현할 것인지 결정하는 것 → **'어떻게 할 것인가?'에 포커싱**

개발자들은 항상 분석과 설계를 명확히 구분하는데에 있어서 어려움을 겪습니다. 분명 목적을 정해두었지만 어느 순간 바쁘게 일하다 보면 목적과 설계가 뒤바뀌어있는 경우가 많기 때문인데요, 따라서 다음과 같은 관념을 항상 머릿속에 되새기면서 작업에 임해야합니다.

#### **분석 & 설계에서 유의할 점**

**분석**
절대 바뀌지 않는 요소, 즉 **'목표'**가 분석을 통해 결정

- 시스템 사용자의 관점에서 시스템 요구 사항을 수집 → **「요구사항 : 기능성, 성능, 인터페이스 등」**
- 분석을 멈출 수 있을 때는 언제인가? → **우리가 테스트해볼 수 있는 문서를 얻을 때까지**
- 대규모 시스템 구축을 위해선 **전체 개발 시간의 30 ~ 40%**는 분석에 할애
- 만약 대안이 존재하지 않는다면? → **'어떻게'가 곧 '무엇을'**

**설계**
전략적 / 분석적인 결정들은 시스템에 요구되는 기능적 / 질적 요구사항들을 충족시키기 위해 만들어집니다.

!!! 실제로 큰 기업들은 어떤 시스템에 대한 **'설계도'**를 가지고 있고, 이 설계도는 곧 **'무엇을 만들고 싶은지'**를 의미하는 결정체가 됩니다. 그리고 이를 만들기 위한 방법을 모색하는 일을 계약된 하청업체들이 진행하는데, 이들은 **'어떻게 하면 해당 제품 또는 구성품을 만들지'** 를 담당합니다. 쉽게 회사 간 갑을 관계가 형성된다고 생각하시면 되겠습니다.

![Desktop View](/assets/img/software-engineering/company-analysis-design.jpg){: width="500" height="500" }

### **UML (Unified Modeling Language)**

- 객체 지향 설계를 위한 그래픽 언어 → 기업 표준, OMG(Object Management Group)이 개발

### **<https://noru0817.github.io/posts/Docker/>**

모델링에 대한 접근법은 다음과 같은 모습으로 발전해왔습니다.
![Desktop View](/assets/img/software-engineering/modeling-flow.jpg){: width="500" height="500" }

### **기능적 모델링 (Functional Modeling == Static Modeling)**

- 시스템의 기능성에 포커싱 → **'이 시스템에는 이러한 기능이 있다'**
- 근간은 C와 같은 '구조적 프로그래밍 언어'
- 모델 구성
  - Data Flow(Control Flow) + Data Transformations
- DFD(Data Flow Diagram)으로 표현 → (EX) **DART (Design Approaches for Real-Time Systems)**
- 요구사항 분석에 용이

![Desktop View](/assets/img/software-engineering/functional-modeling.jpg){: width="500" height="500" }

### **동적 모델링 (Dynamic Modeling)**
