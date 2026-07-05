---
title: AquaSweep
title_kr: 양식장 청소 로봇
one_liner: Multi-robot aquafarm cleaning simulator (Isaac Sim + ROS 2)
badge: Doosan Bootcamp
featured: true
order: 2
thumbnail: /assets/p03-aquasweep/빠끔이청소단_환경.png
github: https://github.com/yevettee/AquaSweep
stack: [Isaac Sim, ROS2, USD, URDF/Xacro, Bringup, PyQt5]
media:
  - { type: image, src: /assets/p03-aquasweep/빠끔이청소단_환경.png, caption: 양식장 시뮬레이션 환경 }
  - { type: image, src: /assets/p03-aquasweep/빠끔이청소단_dashboard.png, caption: 관제 dashboard }
  - { type: image, src: /assets/p03-aquasweep/hippo.gif, caption: Hippo 바닥 청소 로봇 }
  - { type: video, src: /assets/p03-aquasweep/aquasweep_demo.mp4, caption: 시뮬레이션 데모 }
role:
  - Isaac Sim scene cleanup. 양식장 asset과 pool/building 좌표 정리
  - Dashboard pool selector와 topic filtering 적용
  - Simulation bring-up tuning. camera view, debris/shark range, latency 조정
challenge: >-
  15대 로봇을 동시에 돌릴 때 dashboard가 모든 pool topic을 계속 받으면
  부하가 커졌습니다. 그래서 선택한 pool만 topic을 받고, 보고 있지 않은
  pool 데이터는 수신하지 않도록 조절했습니다.
---

Isaac Sim과 ROS 2 기반 양식장 멀티 로봇 시뮬레이터입니다. 팀에서 정의한
ROS 2 인터페이스를 기반으로 detection, planning, controller, Isaac Sim
service 호출 흐름을 연결했습니다.
