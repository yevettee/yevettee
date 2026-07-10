---
title: Doob-E
title_kr: 음성 명령 기반 공구정리 로봇
one_liner: 음성 명령 기반 공구 정리 로봇
card_summary: >-
  음성 명령을 STT/LLM으로 해석해 Doosan M0609가 공구를 집어 정리하는
  시스템입니다. YOLO detection과 연계한 pick & sort flow를 Gazebo에서
  검증한 뒤 실로봇 실행까지 완료했습니다.
card_roles:
  - 공구명 오인식을 줄이는 STT/LLM command parser 보정
  - 실로봇 없이 전체 flow를 검증하는 Gazebo virtual mode 구축
  - Pick 대상 좌표가 갱신되지 않는 문제를 re-detect loop로 해결
tier: main
card_stack: [Doosan M0609, ROS 2, Gazebo, Web UI, Real Robot Validation]
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
  - 공구명 오인식을 줄이는 STT/LLM command parser 보정
  - M0609, RG2 gripper, D435i 카메라와 공구 배치를 맞춘 Gazebo virtual mode 구축
  - E-stop, wake-word pause, 물체 개수, bounding box를 robot state와 맞추는 Web UI 상태 동기화
  - Pick 대상 좌표가 갱신되지 않는 문제를 매 pick 전 re-detect loop로 해결
challenge_issue: >-
  모든 공구를 한 번에 정리하는 명령을 실행하는 중 이전 YOLO detection
  좌표가 재사용되어, 실제 공구 위치와 pick target이 어긋나는 문제 발생
challenge_fix: >-
  각 grasp 전에 home 복귀 -> re-detect -> pick 순서로 execution loop를
  재구성해, 매 pick마다 최신 좌표를 사용하도록 수정
implementation:
  - "Backend 분리: real robot code와 충돌하지 않도록 simulation backend / hardware backend를 분리"
  - "Gazebo validation: M0609, RG2 gripper, D435i camera, 카메라 위치와 공구 배치를 맞춰 voice command -> pick/sort flow를 검증"
  - "UI state sync: E-stop, wake-word pause, object count, bounding box update를 robot state와 동기화"
  - "Re-detect loop: 전체 정리 실행 중 stale detection result를 피하기 위해 home 복귀 -> re-detect -> pick 순서로 execution loop를 수정"
---

## Overview

Doosan M0609 기반의 자동 공구 정리 시스템입니다.

음성 명령을 STT, LLM, Command Parser를 거쳐 실행 가능한 작업 계획으로 변환하고, Planner와 YOLO Detection을 연계하여 공구 Pick & Sort를 수행합니다.

개별 공구 지시와 모든 공구를 한 번에 정리하는 명령을 지원하며, Gazebo virtual mode에서 검증한 뒤 실로봇에서 동일한 flow를 실행했습니다. 저는 Gazebo 검증 환경 구축과 Web UI 상태 동기화, 음성 명령 인식 보정을 담당했습니다.
