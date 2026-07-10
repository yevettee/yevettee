---
title: Doob-E
title_kr: 음성 명령 기반 공구정리 로봇
one_liner: 음성 명령을 해석해 공구를 집고 제자리에 정리하는 협동로봇 시스템
card_summary: >-
  음성 명령을 STT/LLM으로 해석해 Doosan M0609가 공구를 정리하는 시스템입니다. Gazebo에서 동일한 Workflow를 검증한 뒤 실로봇에서 실행했습니다.
card_roles:
  - STT/LLM Command Parser 보정
  - Gazebo Virtual Mode 구축
  - Re-detect Loop 기반 Pick & Sort 안정화
tier: main
card_stack: [ROS 2, Gazebo, M0609, STT/LLM, YOLO]
badge: Doosan Bootcamp
featured: true
order: 2
thumbnail: /assets/p02-doob-e/두비_실제동작화면.png
github: https://github.com/yevettee/Doob-E
stack: [ROS2, Gazebo, M0609, D435i, Web UI, STT/LLM]
facts:
  - { label: Robot, value: Doosan M0609 }
  - { label: Team, value: 6명 }
  - { label: Duration, value: 2026.04.27 – 05.13 (약 2주) }
media:
  - { type: video, src: /assets/p02-doob-e/doob-e.mp4, caption: 최종 시연 영상 }
  - { type: image, src: /assets/p02-doob-e/두비_실제동작화면.png, caption: 실제 로봇 동작 화면 }
  - { type: image, src: /assets/p02-doob-e/실제관제.png, caption: 실제 관제 화면 }
  - { type: image, src: /assets/p02-doob-e/gazebo관제.png, caption: Gazebo virtual mode 관제 화면 }
role:
  - STT/LLM Command Parser를 프로젝트 공구명과 음성 오인식 패턴에 맞게 보정
  - M0609, RG2 Gripper, D435i를 포함한 Gazebo Virtual Mode 구축
  - Web UI와 Robot State를 동기화하여 실행 상태와 오류 처리 개선
  - Re-detect Execution Loop를 적용해 매 Pick마다 최신 YOLO 좌표 사용
challenge_issue: >-
  "모두 정리해줘" 명령에서는 첫 YOLO Detection 결과를 계속 재사용해, Pick 이후 물체 위치가 바뀌어도 이전 좌표를 사용했습니다.
challenge_fix: >-
  매 Pick 전에 Home → Re-detect → Pick 순서로 Execution Loop를 재구성하여 항상 최신 YOLO Detection 결과를 사용하도록 수정했습니다.
implementation:
  - "<strong>Virtual Mode Architecture</strong><br>sim_mode와 real_mode를 분리하고 Gazebo Backend를 독립 구성하여 실로봇 코드 수정 없이 동일한 Workflow를 검증"
  - "<strong>Robot Simulation Setup</strong><br>M0609, RG2 Gripper, D435i Camera와 Bolt/Nut SDF 모델을 Gazebo 환경에 구성하고, Camera Pose와 Object Spawn을 실제 환경에 맞게 조정"
  - "<strong>Web State Synchronization</strong><br>Robot State, Wake Word, Object Count, Bounding Box를 ROS2 Topic과 동기화하여 실행 상태를 실시간으로 반영"
---

## Overview

Doosan M0609 기반의 음성 명령 공구 정리 로봇입니다.

Wake Word, STT, LLM Command Parsing을 통해 음성 명령을 작업 계획으로 변환하고, YOLO Detection과 Planner를 연계하여 Pick & Sort를 수행합니다.

동일한 ROS2 Workflow를 Gazebo Virtual Mode에서 먼저 검증한 뒤, 실로봇에서 동일한 시나리오를 실행하도록 구성했습니다.