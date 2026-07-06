---
title: MediCart
title_kr: 간호사 보조 로봇
one_liner: 병동 순회 간호사 보조 로봇
card_stack: [TurtleBot4, Nav2, ROS 2]
badge: Doosan Bootcamp
featured: true
order: 4
thumbnail: /assets/p04-medicart/간호사 팔로잉.png
github: https://github.com/yevettee/MediCart
stack: [TurtleBot4, Nav2, ROS2, State Machine, Firebase]
media:
  - { type: image, src: /assets/p04-medicart/간호사 팔로잉.png, caption: 간호사 팔로잉 모드 }
  - { type: video, src: /assets/p04-medicart/간호보조카트.mp4, caption: 최종 시연 영상 }
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
