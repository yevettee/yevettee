---
title: Vision-based Drone Landing
title_kr: 비전 기반 드론 착륙
one_liner: Camera-only autonomous drone landing (graduation capstone)
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
  - YOLO/ArUco landing marker detection
  - Real-time position update landing flow
  - AirSim marker, drone, camera setup
  - DJI Tello validation과 camera calibration
implementation_title: Validation Note
implementation:
  - "AirSim validation: marker, drone, camera 환경을 구성해 landing flow를 먼저 검증."
  - "Camera calibration: DJI Tello test 과정에서 marker size, camera calibration, distance estimation 값을 재조정."
  - "Landing error 보정: simulation setup과 실제 드론 테스트 사이의 위치 오차를 보정."
---

## Project Topic

Camera-only autonomous drone landing capstone입니다. 드론이 착륙 마커를 인식하고, marker position update를 기반으로 목표 위치를 보정하며 착륙하는 시나리오를 구현한 프로젝트입니다.

AirSim simulation과 DJI Tello test를 통해 vision-based landing flow를 검증하였습니다.
