---
title: Vision-based Drone Landing
title_kr: 비전 기반 드론 착륙
one_liner: 마커 인식과 위치 추정으로 자율 착륙을 수행하는 드론 비전 시스템
card_roles:
  - YOLO·ArUco 기반 Landing Marker Detection
  - Vision-based Landing Control 구현
card_stack: [YOLO, ArUco, Camera Calibration, AirSim, DJI Tello]
badge: School Project
featured: false
order: 5
thumbnail: /assets/p07-vision/real_drone.png
stack: [YOLO, ArUco, Camera Calibration, AirSim, DJI Tello]
facts:
  - { label: Robot, value: DJI Tello }
  - { label: Team, value: 2명 }
  - { label: Duration, value: 2023.09 – 2024.07 (졸업작품 · 2개 학기) }
media:
  - { type: video, src: /assets/p07-vision/실기체검증.mp4, caption: DJI Tello 실기체 검증 — 최초 detection 좌표 기반 착륙으로 목표 지점 오차 발생 }
  - { type: image, src: /assets/p07-vision/real_drone.png, caption: DJI Tello validation }
  - { type: image, src: /assets/p07-vision/sim_화면.png, caption: AirSim 시뮬레이션 화면 }
  - { type: image, src: /assets/p07-vision/드론_마커.png, caption: 착륙 마커 }
role:
  - YOLO·ArUco 기반 착륙 마커 인식
  - 마커 위치 추정 기반 착륙 제어 구현 및 실기체 검증
  - AirSim 기반 시뮬레이션 환경 구축
  - DJI Tello 실기체 검증 및 Camera Calibration
challenge_issue: >-
  실시간 re-detection 기반 좌표 보정을 목표로 설계했으나, detection 지연(3~8초)과
  Tello 실기체의 필드 제약(통신 불안정, 배터리·발열 한계, 야외 바람)으로
  실험 반복 주기가 병목이 되어 실시간 보정 구현을 완료하지 못함
challenge_fix: >-
  최초 detection 좌표 기반 착륙으로 범위를 조정해 실기체 검증을 완료하고,
  착륙 오차 분석으로 실시간 re-detection 보정 구조의 필요성을 도출
---

## Overview

Camera-only autonomous drone landing 졸업 프로젝트입니다.

YOLO와 ArUco를 이용해 착륙 마커를 인식하고, 추정한 마커 위치를 기반으로 자율 착륙을 수행하는 시스템입니다.

AirSim 시뮬레이션 검증과 DJI Tello 실기체 테스트를 진행했습니다.
