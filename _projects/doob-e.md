---
title: Doob-E
title_kr: 공구정리 로봇
one_liner: Voice-commanded tool-sorting robot (Doosan M0609)
badge: Doosan Bootcamp
featured: true
order: 1
thumbnail: /assets/p02-doob-e/두비_실제동작화면.png
github: https://github.com/yevettee/Doob-E
stack: [ROS2, Gazebo, M0609, D435i, Web UI, STT/LLM]
media:
  - { type: image, src: /assets/p02-doob-e/두비_실제동작화면.png, caption: 실제 로봇 동작 화면 }
  - { type: image, src: /assets/p02-doob-e/실제관제.png, caption: 실제 관제 화면 }
  - { type: image, src: /assets/p02-doob-e/gazebo관제.png, caption: Gazebo virtual mode 관제 화면 }
role:
  - STT/LLM parser tuning. 공구명과 오인식 단어 보정
  - Gazebo virtual mode. M0609, RG2, D435i, object spawn 구성
  - Web UI state sync. E-stop, wake word pause, object count, bounding box 처리
  - stale YOLO 좌표 방지. 매 pick 전 re-detect loop 추가
challenge: >-
  clean-all 중 이전 YOLO 좌표가 계속 사용되는 문제가 있었습니다.
  매 grasp 전에 home 복귀, 재탐지, pick loop를 추가했습니다.
---

STT/LLM command, YOLO detection result, Gazebo virtual mode, Web UI 제어를
연결한 M0609 공구 정리 시스템입니다.
