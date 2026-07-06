---
title: AquaSweep
title_kr: 양식장 청소 로봇
one_liner: 다중 로봇 양식장 청소 시뮬레이터 (Isaac Sim + ROS 2)
badge: Doosan Bootcamp
featured: true
order: 1
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
challenge_issue: >-
  15대 로봇 동시 실행 중 dashboard가 전체 pool topic을 구독해 CPU 부하 증가,
  message update 지연, camera/status 갱신 지연 발생.
challenge_fix: >-
  모든 pool topic을 subscribe하지 않고, dashboard에서 선택한 pool의 topic만
  subscribe하도록 filtering 적용.
implementation_title: Implementation Details
implementation:
  - "Scene cleanup: Blender asset을 scene / robot / pool 단위로 정리하고, pool/building 좌표를 재정렬."
  - "Extension bring-up: 기능별 Isaac Sim extension을 하나의 launch sequence로 묶고 startup order를 조정."
  - "Runtime tuning: camera view, debris/shark spawn range, latency를 simulation scenario 기준으로 조정."
  - "Topic filtering: dashboard가 모든 pool topic을 subscribe하지 않고, 선택한 pool topic만 subscribe하도록 범위를 제한."
---

## Project Topic

Isaac Sim과 ROS 2 기반의 철갑상어 양식장 multi-robot 청소 시스템입니다.

수조 바닥 청소 로봇 Hippo 7대, 벽면 청소 로봇 M1013 7대, 폐사체 수거용 gantry robot 1대로 구성된 총 15대 로봇 시나리오를 다룹니다.

관리자가 dashboard에서 clean 명령을 내리면 camera feed를 기준으로 상어가 없는 pool을 탐지하고, 해당 pool에 청소 작업을 할당합니다.

또한 관리자는 pool별 상태를 확인하고, 선택한 pool에 수동 청소 명령을 보낼 수 있습니다.
