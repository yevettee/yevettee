---
title: Vision-based Drone Landing
title_kr: 비전 기반 드론 착륙
one_liner: 비전 기반 드론 착륙 시스템
badge: School Project
featured: false
order: 5
thumbnail: /assets/p07-vision/real_drone.png
stack: [YOLO, ArUco, Camera Calibration, AirSim, DJI Tello]
media:
  - { type: image, src: /assets/p07-vision/real_drone.png, caption: DJI Tello validation }
  - { type: image, src: /assets/p07-vision/sim_화면.png, caption: AirSim 시뮬레이션 화면 }
  - { type: image, src: /assets/p07-vision/드론_마커.png, caption: 착륙 마커 }
role:
  - YOLO·ArUco 기반 착륙 마커 인식
  - 실시간 마커 위치 추정을 통한 착륙 제어
  - AirSim 기반 시뮬레이션 환경 구축
  - DJI Tello 실기체 검증 및 Camera Calibration
implementation_title: Implementation Details
implementation:
  - "AirSim validation: marker, drone, camera 환경을 구성해 landing flow를 먼저 검증."
  - "Camera calibration: DJI Tello test 과정에서 marker size, camera calibration, distance estimation 파라미터 조정."
  - "Landing Accuracy: 시뮬레이션과 실제 드론 간 위치 오차를 분석하고 보정."
---

## Project Topic

Camera-only autonomous drone landing 졸업 프로젝트입니다.

YOLO와 ArUco를 이용해 착륙 마커를 인식하고, 실시간으로 추정한 마커 위치를 기반으로 드론의 목표 위치를 보정하여 자율 착륙을 수행하는 시스템입니다.
