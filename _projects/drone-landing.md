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
---

카메라 비전만으로 landing marker를 인식해 드론을 자율 착륙시키는
졸업작품입니다. YOLO와 ArUco로 marker를 탐지하고, 실시간으로 목표 위치를
갱신하며, AirSim 세팅부터 DJI Tello validation까지 진행했습니다.
