---
title: MediCart
title_kr: 간호사 보조 로봇
one_liner: 병동 순회 문진과 복귀를 수행하는 간호사 보조 로봇
card_summary: >-
  TurtleBot4 기반 병동 순회 간호사 보조 로봇입니다. 지정 병상을 순회하며
  QR로 환자를 확인하고 문진을 안내하며, 환자 부재 처리부터 도킹 복귀까지
  터미널 개입 없이 수행합니다.
card_roles:
  - 버튼 하나로 undock부터 복귀까지 이어지는 문진 patrol state machine 구현
  - Nav2 waypoint 이동과 QR 확인, 환자 부재 timeout 등 fallback 처리 연결
  - Robot state를 Firebase에 기록해 Web UI와 상태 동기화
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
  - 버튼 하나로 undock부터 docking 복귀까지 이어지는 문진 patrol state machine 구현
  - Nav2 waypoint 이동, web 문진표 전환, 팀원이 구현한 QR 판단 결과를 하나의 patrol 시나리오로 연결
  - 환자 부재 30초 timeout, QR 불일치, 문진 완료 등 fallback 상태 전환 처리
  - Robot state와 문진 상태를 Firebase에 기록해 Web UI와 동기화, launch bring-up 정리
challenge_issue: >-
  QR 판단, 문진 웹, waypoint 이동 같은 단위 기능은 모두 있었지만, 버튼
  하나로 undock부터 복귀까지 이어지려면 QR 결과, 문진 상태, 부재 처리
  사이에서 상태 전이가 끊기지 않아야 했음
challenge_fix: >-
  QR 결과와 웹 문진 상태를 state machine에 연결하고, 30초 timeout과
  부재중 fallback을 정리해 터미널 개입 없는 patrol mission flow를 완성
implementation:
  - "Patrol state machine: start button 이후 undock -> waypoint following -> QR 처리 -> 문진 대기 -> docking 흐름을 구성"
  - "Fallback handling: QR 불일치, 환자 부재, 문진 완료 상태에 따라 next waypoint 또는 return flow로 전환"
  - "Nav2 workflow: waypoint 이동과 web questionnaire state를 같은 patrol scenario 안에서 연결"
  - "Localization guard: Nav2 initial pose 설정 전 mission start를 막는 dashboard guard 추가"
  - "State logging: robot state와 questionnaire state를 Firebase에 기록해 Web UI와 TurtleBot4의 기준 상태를 맞춤"
---

## Overview

TurtleBot4 기반 병원 간호사 보조 로봇입니다. 환자 문진 patrol(Mode A)과 간호사 following cart(Mode B) 두 시나리오로 구성되며, 저는 Mode A를 담당했습니다.

Mode A는 간호사가 로봇 위 iPad에서 문진 모드를 시작하면, 로봇이 undock 후 병실 앞 waypoint를 순서대로 방문하는 시나리오입니다. 각 침상에서 QR로 환자를 확인해 문진표를 안내하고, QR 불일치나 무응답 시 30초 대기 후 다음 환자로 넘어가며, 순회가 끝나면 docking station으로 복귀합니다.

Mode B는 약제실에서 약품을 OCR로 확인한 뒤 간호사를 따라 병실까지 이동하는 following cart 시나리오입니다. 간호사가 환자에게 다가가면 following을 해제하고 대기하며, 이 시나리오는 팀원들이 담당했습니다.
