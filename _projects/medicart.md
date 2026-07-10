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
media:
  - { type: video, src: /assets/p04-medicart/간호보조카트.mp4, caption: 최종 시연 영상 }
  - { type: image, src: /assets/p04-medicart/간호사 팔로잉.png, caption: 간호사 팔로잉 모드 }
  - { type: image, src: /assets/p04-medicart/순회문진_map.png, caption: 순회 문진 지도, fit: contain }
role:
  - Mode A 문진 patrol state machine 구현
  - Nav2 waypoint flow와 QR 결과 처리
  - 환자 부재 timeout과 문진 완료 상태 전환 처리
  - Firebase state logging과 launch bring-up 정리
challenge_issue: >-
  One-button patrol flow에서 undock, waypoint following, QR result handling,
  questionnaire wait, absence timeout, docking까지 상태 전이 단절 위험
challenge_fix: >-
  State transition과 fallback handling 통합. 터미널 개입 없는 patrol
  mission flow 구성
implementation_title: Implementation Details
implementation:
  - "Patrol state machine: start button 이후 undock -> waypoint following -> QR 처리 -> 문진 대기 -> docking 흐름을 구성"
  - "Fallback handling: QR 불일치, 환자 부재, 문진 완료 상태에 따라 next waypoint 또는 return flow로 전환"
  - "Nav2 workflow: waypoint 이동과 web questionnaire state를 같은 patrol scenario 안에서 연결"
  - "Localization guard: Nav2 initial pose 설정 전 mission start를 막는 dashboard guard 추가"
  - "State logging: robot state와 questionnaire state를 Firebase에 기록해 Web UI와 TurtleBot4의 기준 상태를 맞춤"
---

## Project Topic

TurtleBot4 기반 hospital assistant robot입니다. 병동 내 지정 병상을 순회하며 QR 확인, 문진 안내, 환자 부재 처리, 복귀까지 수행하는 문진 patrol 시나리오를 다룹니다.
