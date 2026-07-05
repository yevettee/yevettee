---
title: MediCart
title_kr: 간호사 보조 로봇
one_liner: Hospital ward patrol assistant robot (TurtleBot4)
badge: Doosan Bootcamp
featured: true
order: 4
thumbnail: /assets/p04-medicart/간호사 팔로잉.png
github: https://github.com/yevettee/MediCart
stack: [TurtleBot4, Nav2, ROS2, State Machine, Firebase]
media:
  - { type: image, src: /assets/p04-medicart/간호사 팔로잉.png, caption: 간호사 팔로잉 모드 }
  - { type: image, src: /assets/p04-medicart/순회문진_map.png, caption: 순회 문진 지도, fit: contain }
role:
  - Mode A 문진 patrol state machine 구현
  - Nav2 waypoint flow와 QR 결과 처리
  - 환자 부재 timeout과 문진 완료 상태 전환 처리
  - Firebase 상태 기록과 launch bring-up 정리
challenge: >-
  버튼 하나로 undock, waypoint 순회, QR 결과 처리, 문진 대기, 환자 부재
  timeout, dock까지 이어져야 했습니다. 상태 전환과 fallback 처리를 묶어서
  터미널 개입 없이 문진 순회가 이어지도록 만들었습니다.
---

TurtleBot4 병원 보조 로봇입니다. Mode A 문진 patrol flow에서 Nav2
waypoint, QR 확인 결과, Firebase 상태 기록, 웹 문진 상태 전환을
연결했습니다.
