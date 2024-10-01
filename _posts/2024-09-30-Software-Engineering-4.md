---
title: 소프트웨어공학 5주차 - (1)
date: 2024-09-24 16:31:10 +09:00
categories: [3학년 2학기, 소프트웨어공학]
tags: [단기 계획, 3학년 2학기, 소프트웨어공학]
mermaid: true
---

## **[질문 사항] Release VS. Deploy**

- Release: 특정 레포지토리에 특정 환경에서 작동할 수 있는 소프트웨어를 버전을 명시하여 게시하는 것
- Delpoy: 설치가 기반되어야 함. 특정 기기에 Deploy한다는 의미는 의존성까지 전부 고려하여 특정 환경을 구성한다는 의미.

## **프로젝트 계획과 관리**

### **WBS: Work Breakdown Structure**

![Desktop View](/assets/img/software-engineering/wbs.jpg){: width="500" height="500" }

- **MM (Man-Month): 특정 기간 동안 n명의 사람이 일에 투자한 시간 비용 (p.102)**

### 직능별 조직 (p.116 ~ 117)

각 직능 별로 팀을 구성하다 보니 자칫 잘못하면 Waterfall 형식의 개발이 되어버려서 진행 속도가 매우 느려짐

### 프로젝트별 조직 (p.117 ~ 118)

서로 다른 역할을 담당하는 직능별 개발자들이 프로젝트에 배정되어 프로젝트 별로 부서를 조직하는 방법
![Desktop View](/assets/img/software-engineering/role-project-organization.jpg){: width="500" height="500" }

### 매트릭스 조직 (p.118 ~ 119)

각 프로젝트의 특정 직능을 맡고 있는 사람들이 또 다른 프로젝트의 같은 직능을 일부 혹은 모두 맡고 있는 구조
![Desktop View](/assets/img/software-engineering/matrix-organization.jpg){: width="500" height="500" }

### 리스크 관리 (p. 124)

위험 요인 파악 후 평가 및 관리하는 기수, 노하우, 프로세스
![Desktop View](/assets/img/software-engineering/risk-management.jpg){: width="500" height="500" }

## Chapter. 4 요구 분석 → 여기서부터 진짜 시험 범위

### **P.137**

CI/CD에서의 'Plan'은 Modeling을 의미하고 Modeling은 'Analysis(분석) + Design(설계)'

- 요구 추출(Elicitation) → 요구 분석 → 요구 확인
  - 이 과정을 거쳐야 동상이몽으로 발생하는 문제를 해결할 수 있는 'Agile Development'가능
    ![Desktop View](/assets/img/software-engineering/elicitation.jpg){: width="500" height="500" }

### **P.147**

- **레거시 시스템 (Legacy System)**: 현재 존재하는 시스템 → 새로운 릴리즈로 인해 더이상 패치가 진행되지 않는 시스템들 또한 레거시

### **시나리오 기반 분석 (P.159~)**

**5W1H 방식**: When, Where, Who, What, Why, How
→ 이중 **'Who, What, Why'는 무조건 기술**되어야 함

**유스 케이스 (쓰임새, Use Case)**
사용자 시나리오라고도 부르며, 도메인 분석의 결과를 액터, 유스 케이스, 관계들로 구성된 시스템 명세로 매핑하는 작업
→ 실질적인 개발 시 Why가 포함되면 복잡해지기에, Who, What만을 이용하여 표현함

- Who: 액터 → 소프트웨어를 사용하는 모든 대상
- What: 사용 사례 → 소프트웨어가 하는 일

![Desktop View](/assets/img/software-engineering/domain-analysis.jpg){: width="500" height="500" }

![Desktop View](/assets/img/software-engineering/use-case.jpg){: width="500" height="500" }
