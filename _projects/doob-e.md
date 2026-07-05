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
  - Gazebo virtual mode. M0609, RG2, D435i, 카메라 위치와 공구 배치 구성
  - Web UI state sync. E-stop, wake-word pause, object count, bounding box 처리
  - stale YOLO 좌표 방지. 매 pick 전 re-detect loop 추가
challenge_issue: >-
  Clean-all 실행 중 stale YOLO coordinates 재사용. 실제 공구 위치와 pick target
  불일치 발생.
challenge_fix: >-
  각 grasp 전 home 복귀 -> re-detect -> pick 순서의 execution loop 추가.
implementation_title: Implementation Details
implementation:
  - "Backend 분리: real robot code와 충돌하지 않도록 simulation backend / hardware backend를 분리."
  - "Gazebo validation: M0609, RG2 gripper, D435i camera, 카메라 위치와 공구 배치를 맞춰 voice command -> pick/sort flow를 검증."
  - "UI state sync: E-stop, wake-word pause, object count, bounding box update를 robot state와 동기화."
  - "Re-detect loop: clean-all 중 stale detection result를 피하기 위해 home 복귀 -> re-detect -> pick 순서로 execution loop를 수정."
---

## Project Topic

Doosan M0609 기반 정비소 공구 정리 시스템입니다.

사용자가 음성으로 공구 정리 명령을 내리면 STT, LLM, command parser를 거쳐 planner가 실행 명령을 생성하고, YOLO detection 결과와 매칭해 공구를 pick/sort하는 시나리오를 다룹니다.

Gazebo virtual mode와 실제 로봇 관제 UI를 함께 사용해 명령 입력부터 로봇 동작까지의 흐름을 검증합니다.
