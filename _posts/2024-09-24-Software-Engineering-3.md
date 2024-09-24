---
title: 소프트웨어공학 2 ~ 3주차 - (1)
date: 2024-09-24 16:31:10 +09:00
categories: [3학년 2학기, 소프트웨어공학]
tags: [단기 계획, 3학년 2학기, 소프트웨어공학]
mermaid: true
---

이번 글에선 소프트웨어공학 2 ~ 3주차 내용 중 1회차 내용에 대해 설명해드리려고 합니다.

지난 글에선 IaaS, PaaS, SaaS까지 설명드렸습니다. 내용이 기억나시지 않는다면, 하단의 링크를 통해 복기하시고 오면 좋을 것 같아요!

#### **<https://noru0817.github.io/posts/Software-Engineering-2/>**

### **가상화 (Virtualization)**

추상화 계층으로 OS보단 밑에 있지만, 하드웨어보단 위에 위치

- **Virtual Machine Monitor (VMM == Hypervisor)**
  - 가상화 인터페이스를 구현
  - VM(Virtual Machine, 이하 VM)이 독립되어 실행되도록 함

여기서 VM이란 'Virtual Machine'의 약자로, 특정 OS image 및 각종 SW, 가상 HW를 모두 묶은 머신을 말합니다. 이때 중요한 점은 VM Hardware는 가상으로 정의된 장치일 뿐, 실재하는 Physical Hardware와 동일시 해서는 안됩니다.

![Desktop View](/assets/img/software-engineering/virtual-machine.jpg){: width="500" height="500" }

### **VM의 종류**

VM을 사용하기 위해선 기저에 Hypervisor가 필요합니다. 이때 Hypervisor는 두 가지로 나뉩니다.

- **Type 1 Hypervisor**
  - bare-metal 환경 또는 native 환경의 Hypervisor
  - **(Ex) VMware vSphere with ESX/ESXi, KVM, Microsoft Hyper-V, Oracle VM, Citrix Hypervisor**
- **Type 2 Hypervisor**
  - Hosted Hypervisor, 즉 OS 위에서 사용자에 의해 호출된 Hypervisor
  - **(Ex) Oracle VM VirtualBox, VMware Workstation Pro / VMware Fusion, Windows Virtual PC, Parallels Desktop**

![Desktop View](/assets/img/software-engineering/type1-hypervisor.jpg){: width="500" height="500" }

![Desktop View](/assets/img/software-engineering/type2-hypervisor.jpg){: width="500" height="500" }

### **Type1 VS. Type2**

- **Type1**

  - **장점**

    - **확장성**
      - 하드웨어 결함의 관점에서, 관리 소프트웨어가 이슈가 발생하자마자 VM을 작업 서버로 전환
      - 가용한 리소스들을 특정 VM의 현재 요구 사항에 맞춰 동적으로 할당 가능
      - Host OS의 작업량이 없음 → Type 1의 경우 Hypervisor 위에 VM의 Guest OS가 올라가는 구조
    - **보안**
      - 잠재적 악의를 가진 사람들에 대한 공격 면의 확연한 감소

  - **단점**
    - **제한된 기능성**
      - 상대적으로 단순하며, 적은 기능 제공
    - **복잡한 관리**
      - 가상 인스턴스 생성을 위해 다른 머신에 대한 관리 콘솔 필요
    - **가격**
      - 필요한 기능의 양에 따라 관리 콘솔들을 위한 라이센스 비용이 잠재적으로 증가

- **Type2**

  - **장점**

    - 쉬운 관리
    - 테스트의 편의성 보장
    - 추가적인 생산 도구들의 접근 허용

  - **단점**
    - 자원 관리의 유연성 감소
    - Host OS의 작업량 증가
    - 보안 문제
      - 공격자들이 OS의 잠재적 취약점을 사용해 VM으로의 접근을 얻으려 하기 때문에 잠재적 취약점이 존재

![Desktop View](/assets/img/software-engineering/virtualization-vs-containerization.jpg){: width="500" height="500" }

### **CI/CD (Continuous Integration Continuous Delivery)**

![Desktop View](/assets/img/software-engineering/ci-cd-1.jpg){: width="500" height="500" }

![Desktop View](/assets/img/software-engineering/ci-cd-2.jpg){: width="500" height="500" }

![Desktop View](/assets/img/software-engineering/ci-cd-3.jpg){: width="500" height="500" }

![Desktop View](/assets/img/software-engineering/ci-cd-4.jpg){: width="500" height="500" }

### **Cloud Native Computing**

- **확장 가능한 애플리케이션들을 빌드하고 실행**
  - 현대는 동적 환경 → **Public, Private, Hybrid Cloud 등**
    - Hybrid Cloud: 특정 부분은 On-Premise(On-Site, In-House), 나머지는 타사 클라우드 채택하는 형태
- **느슨하게 연결된 시스템 구성 가능**
  - 빠른 회복성, 관리 가능, 관찰 가능
- **엔지니어가 영향력이 큰 변화를 만들 수 있게 함**

  - 최소한의 수고를 들이면서 빈번하고 예측 가능하도록 함

- **_예시_**
  - **컨테이너 (Container)**
  - **서비스 메쉬 (Service Mesh)**
    - 서비스 간 통신을 추상화하여 안전하고, 빠르고, 신뢰성 있게 만드는 전용 Infrastructure Layer
  - **마이크로서비스 (Microservice)**
  - **불변 인프라 (Immutable Infrasturcture)**
  - **선언형 API들**

### **Virtualization VS. Containerization**

2 ~ 3주차 1회차에 대한 설명은 여기까지입니다. 끝까지 읽어주셔서 감사합니다!!! 😌
