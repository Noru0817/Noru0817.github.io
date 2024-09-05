---
title: Rook-Ceph 구성 요소
date: 2024-09-05 16:09:21 +09:00
categories: [Kubernetes, Rook-Ceph]
tags: [단기 계획]
---

이번 글에서는 저번 글에 이어 Rook-Ceph 구성요소에 대해 간략히 설명 드리겠습니다.

지난 월요일부터 개강했는데, 간단한 프로젝트일 줄 알았던 기초설계 과목이 갑작스럽게 모든 기업체가 LLM 기반 생성형 AI를 토대로 서비스 개발을 뜻하시는 바람에... 지난 학기 이후로 잠시 접어두었던 딥러닝 공부를 다시 시작했습니다 ㅠㅠ

이에 더해 학부 연구생 업무까지 시간이 매우 촉박해져 Rook-Ceph에 대한 자세한 설명은 최소한 2주 뒤부터 시작해야될 것 같습니다 (ㅜ^ㅜ)

당장은 자세히 설명 못드리는 점, 넓은 마음으로 양해 부탁드립니다...

현재 학과 서버 환경에는 다음과 같은 구성 요소들을 통해 PV를 관리 및 제공합니다.

## [Rook Level Component]

1. Operator: 클러스터의 전반적인 관리 및 오케스트레이션을 담당합니다.

   - Ceph 클러스터 생성 및 구성
   - 스토리지 리소스 관리
   - 클러스터 상태 모니터링 및 조정
   - CRDs 처리

2. CRDs (Custom Resource Definitions): 쿠버네티스에 Rook-Ceph 관련 사용자 정의 리소스 타입 정의

   - CephCluster
   - CephBlockPool
   - CephFileSystem
   - CephObjectStore
   - CephClient

3. Toolbox: 디버깅 및 관리 도구 제공
   - Ceph 명령어 실행
   - 클러스터 상태 진단 및 로그 확인

## [Ceph Level Component]

1. Cluster: 분산 스토리지 기능 제공

   - MON (Monitor): 클러스터 맵 관리, 클라이언트 인증
   - MGR (Manager): 추가 모니터링 기능, 대시보드 제공
   - OSD (Object Storage Device): 실제 데이터 저장 객체
   - MDS (Metadata Server): CephFS(Ceph FileSystem) 메타데이터 관리

2. CSI Proviosioner: 동적 볼륨 프로비저너

다음 Rook-Ceph 관련 글에서는 좀 더 자세한 메커니즘 설명으로 돌아오겠습니다.  
오늘도 읽어주셔서 감사합니다!!!
