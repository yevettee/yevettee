---
title: MediCart
title_kr: 간호사 보조 로봇
one_liner: 병동 순회 문진과 복귀를 수행하는 간호사 보조 로봇
card_summary: >-
  TurtleBot4 기반 병원 간호사 보조 로봇입니다. 환자 문진 순회와 약품 전달 두 가지 운영 시나리오를 구현했습니다.
card_roles:
  - Patient Rounding State Machine 구현
  - Nav2·QR·Web을 연결한 Patrol Workflow 통합
  - Firebase 기반 Robot State 동기화
tier: main
card_stack: [TurtleBot4, Nav2, ROS 2, State Machine, Firebase]
badge: Doosan Bootcamp
featured: true
order: 3
thumbnail: /assets/p04-medicart/간호사 팔로잉.png
github: https://github.com/yevettee/MediCart
stack: [TurtleBot4, Nav2, ROS2, State Machine, Firebase]
facts:
  - { label: Robot, value: TurtleBot4 }
  - { label: Team, value: 9명 · 2개 팀 통합 }
  - { label: Duration, value: 2026.05.29 – 06.12 (2주) }
media:
  - { type: video, src: /assets/p04-medicart/간호보조카트.mp4, caption: 최종 시연 영상 }
  - { type: image, src: /assets/p04-medicart/간호사 팔로잉.png, caption: 간호사 팔로잉 모드 (Mode B · 팀 시나리오) }
  - { type: image, src: /assets/p04-medicart/순회문진_map.png, caption: 순회 문진 지도, fit: contain }
role:
  - 버튼 한 번으로 undock → patient rounding → docking까지 이어지는 Patient Rounding State Machine 구현
  - Nav2 waypoint, Web 문진, QR 인식 결과를 하나의 Workflow로 통합
  - QR 불일치, 환자 부재(30s timeout), 문진 완료에 따른 fallback transition 설계
  - Robot state와 문진 상태를 Firebase에 동기화하고 Launch Bring-up 구성
challenge_issue: >-
  QR 인식, Web 문진, Nav2 waypoint는 각각 동작했지만, 버튼 한 번으로 끝까지 이어지는 Patient Rounding Workflow가 없어 시나리오 진행 중 상태 전환이 끊겼습니다.
challenge_fix: >-
  QR 결과와 Web 문진 상태를 State Machine으로 통합하고, timeout과 fallback transition을 추가하여 터미널 개입 없는 End-to-End Patient Rounding Workflow를 구현했습니다.
implementation:
  - "<strong>Patrol State Machine</strong><br>QR 불일치, 환자 부재, 문진 완료 상태에 따라 다음 waypoint 또는 복귀 경로로 전환되는 fallback transition 설계"
  - "<strong>Localization Guard</strong><br>Mission 시작 전 Nav2 Initial Pose 설정 여부를 확인하여 초기 Localization 실패 방지"
  - "<strong>Launch Bring-up</strong><br>Patrol 실행에 필요한 노드를 하나의 Launch Sequence로 통합하여 터미널 개입 없이 전체 시나리오 실행"
---

## Overview

TurtleBot4 기반 병원 간호사 보조 로봇으로, 환자 문진 순회(Patient Rounding)와 간호사 약품 전달(Nurse Assistance) 두 가지 운영 시나리오를 구현했습니다.

**Patient Rounding - 환자 문진 순회**  
간호사가 문진을 시작하면 로봇이 병실 waypoint를 순회하며 환자를 방문합니다. QR로 환자를 확인한 뒤 iPad에서 문진을 진행하며, QR 결과와 문진 상태에 따라 다음 환자 또는 복귀 경로로 전환됩니다. 모든 순회가 끝나면 docking station으로 복귀합니다.

**Nurse Assistance - 간호사 보조**  
Web에서 처방 환자를 선택하면 OCR로 약품 정보를 확인한 뒤 로봇이 간호사를 따라 이동합니다. 환자 구역 도착 후 대기하며, 처방 완료 시 docking station으로 복귀합니다.
