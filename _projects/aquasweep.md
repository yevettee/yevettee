---
title: AquaSweep
title_kr: 양식장 청소 멀티 로봇
one_liner: Isaac Sim에서 로봇 15대를 운용하는 양식장 청소 시뮬레이터
card_summary: >-
  Isaac Sim 기반 15대 멀티 로봇 양식장 청소 시뮬레이션입니다. Dashboard에서 작업을 지시하면 YOLO 기반으로 작업 가능한 Pool을 선택해 청소를 수행합니다.
card_roles:
  - Isaac Sim Scene & Bring-up 구성
  - Dashboard Topic Filtering 적용
  - Simulation Runtime Tuning
tier: main
card_stack: [Isaac Sim, ROS 2, Multi-Robot, Bring-up, Topic Filtering]
badge: Doosan Bootcamp
featured: true
order: 1
thumbnail: /assets/p03-aquasweep/빠끔이청소단_환경.png
github: https://github.com/yevettee/AquaSweep
stack: [Isaac Sim, ROS2, USD, URDF/Xacro, Bringup, PyQt5]
facts:
  - { label: Robot, value: 멀티 로봇 15대 (Isaac Sim) }
  - { label: Team, value: 5명 · 팀장 }
  - { label: Duration, value: 2026.05.14 – 05.28 (2주) }
media:
  - { type: video, src: /assets/p03-aquasweep/aquasweep_demo.mp4, caption: 시뮬레이션 데모 }
  - { type: image, src: /assets/p03-aquasweep/빠끔이청소단_환경.png, caption: 양식장 시뮬레이션 환경 }
  - { type: image, src: /assets/p03-aquasweep/빠끔이청소단_dashboard.png, caption: 관제 dashboard }
  - { type: image, src: /assets/p03-aquasweep/hippo.gif, caption: Hippo 바닥 청소 로봇 }
role:
  - Isaac Sim scene organization 및 asset 좌표 정리
  - Dashboard pool selector와 topic filtering 구조 개선
  - Extension bring-up과 simulation startup sequence 통합
  - Camera view, object spawn, latency 기반 simulation tuning
challenge_issue: >-
  15대 로봇 동시 실행 중 dashboard가 전체 pool topic을 동시에 subscribe하면서 CPU 사용량과, message latency가 증가했습니다
challenge_fix: >-
  모든 pool topic을 subscribe하지 않고, dashboard에서 선택된 pool의 topic만
  subscribe하도록 topic filtering구조를 적용했습니다
implementation:
  - "<strong>Scene Organization</strong><br>Blender에서 전달받은 Asset을 Scene, Robot, Pool 단위로 재구성하고 Prim Path와 좌표를 정리하여 Isaac Sim에서 관리하기 쉬운 구조로 개선"
  - "<strong>Robot Customization</strong><br>Dingo 모델을 기반으로 Hippo 청소 로봇을 구성하고 Camera Pose와 URDF/Xacro를 수정하여 시나리오에 맞는 시야를 확보"
  - "<strong>Extension Bring-up</strong><br>기능별 Extension을 분리한 뒤 Startup Order를 고려한 하나의 Launch Sequence로 통합하여 안정적인 초기화를 구성"
  - "<strong>Simulation Tuning</strong><br>Camera View, Shark/Debris Spawn, Latency를 조정하여 실제 시나리오에 맞는 Simulation 환경을 구성"
---

## Overview

Isaac Sim과 ROS2 기반의 15대 Multi-Robot 양식장 청소 시뮬레이션입니다.

Dashboard에서 자동 청소를 시작하면 Top-view Camera와 YOLO를 통해 각 Pool 상태를 확인하고, 작업 가능한 Pool에 청소 작업을 할당합니다. 폐사체가 탐지되면 Gantry Robot이 해당 위치로 이동해 수거 작업을 수행합니다.

관리자는 Dashboard를 통해 Pool 상태를 모니터링하고, 특정 Pool에 수동 청소 명령을 보낼 수 있습니다.
