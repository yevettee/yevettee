# Yoon Jeong Ok
**Robot Simulation · Validation · Test Engineer**  
ROS2 · Gazebo · YOLO · Sensor Fusion

---

## About Me
전자공학 전공 기반으로 로봇 제어, 시뮬레이션, 인식 연동 프로젝트를 수행했습니다.  
현재는 **HIL 엔지니어 / 로봇 테스트 엔지니어 / 로봇 시뮬레이션·검증 직무**를 중심으로 준비하고 있습니다.

**관심 분야**
- Robot Simulation / Validation
- HIL / SIL 기반 테스트 환경 구축
- ROS2 기반 로봇 시스템 개발 및 검증
- Perception 연동 테스트 (YOLO, Sensor Fusion)

---

## Tech Stack

### Robotics / Simulation
- ROS2 (Humble)
- Gazebo
- NVIDIA Isaac Sim
- Linux / Ubuntu

### Programming
- Python
- C++

### Perception / Vision
- OpenCV
- YOLO (Object Detection / OBB)
- Sensor Fusion

### Tools & Platforms
- Git / GitHub
- Docker
- Notion
- Firebase (Realtime Database)

---

## Featured Projects

### 1. mother_bird 🍧 — 컵빙수 자동 제조 및 서빙 로봇 시스템

**Overview**
- 두산 로보틱스 M0609 협동로봇을 기반으로 한 컵빙수 자동 제조·서빙 시스템
- 고객 키오스크 웹에서 주문하면 Firebase Realtime Database를 통해 ROS 2 기반 컨트롤러가 24단계 시퀀스를 실행하여 제빙·토핑·드로잉·서빙을 수행
- 관리자 GUI(Pyside6)와 고객용 키오스크 웹을 통한 실시간 진행률 동기화 및 안전 감시

**What I Did**
- ROS2 노드 아키텍처 설계 및 bingsu_sequence(24개 단계) 시퀀스 구현
- Firebase RTDB 연동(order_listener)으로 웹 ↔ ROS2 브리지 구성
- 외력 감지·비상정지(Abort) 처리, 체크포인트 기반 Pause/Resume 설계
- 관리자 GUI 및 키오스크 웹 구성, 동시 검증·재현 가이드 작성

**Tech**
- ROS2 Humble · Python · Doosan M0609 SDK · Firebase RTDB · PySide6 · OpenCV

**Repository**
- https://github.com/yevettee/mother_bird

---

### 2. Doob-E — AI-Powered Service Robot Web System

> 정비소 도우미 로봇 웹 시스템 | 음성 명령 기반 물체 인식 및 pick 작업

**Overview**
- 두산로보틱스 M0609 협작로봇과 RealSense depth camera를 활용한 AI 기반 정비소 도우미 로봇 웹 시스템
- Wake word("두비야") 인식 후 음성 명령으로 로봇이 특정 물체를 인식하고 집거나 정리하는 통합 시스템
- 웹 UI에서 실시간 YOLO 감지 결과, 로봇 상태, 카메라 영상 모니터링

**What I Did**
- ROS2 통합 아키텍처 설계: 음성 인식(STT/LLM), 비전 처리(YOLO), 로봇 제어 연결
- robot_action_node.py / robot_sort_node.py 구현 — 카메라→로봇 좌표 변환, approach/pick/ 정렬 시퀀스
- 음성-비전 명령 매칭 로직 및 안전성 검증(DRY_RUN, pick 높이 보정)
- 웹 대시보드(RealSense, YOLO overlay, 상태 표시) 연동

**Tech**
- ROS2 (Humble) · Python · OpenCV · YOLO · RealSense SDK · STT/LLM (OpenAI) · Flask · Firebase

**Repository**
- https://github.com/yevettee/Doob-E

---

### 3. AquaSweep 🐟 — 양식장 청소 로봇 멀티 시뮬레이터

**Overview**
- NVIDIA Isaac Sim 위에 7개 수조가 있는 양식장 환경을 재현하고, 바닥 청소 로봇(Hippo), 벽 청소 협동로봇(M1013), 갠트리 로봇을 협업 제어하는 멀티 로봇 시뮬레이션
- YOLO OBB + OpenCV 기반 인지로 물고기·이물질을 탐지하고, 수조별 계획(Planner) → 컨트롤러(Controller) → Isaac Sim 실행의 워크플로우로 청소 작업을 자동화
- PyQt5 대시보드로 실시간 영상·진행률 시각화

**What I Did**
- Isaac Sim 익스텐션 및 시뮬레이션 씬 설계(부력·물리·카메라), ROS2 ↔ Isaac 통신 설정
- 다중 런타임(Isaac 3.11 / ROS2 3.10)에서 공통 메시지(aqua_interfaces)를 사용하도록 빌드·설정 스크립트 제작
- Planner/Controller 아키텍처 및 대시보드 구현

**Tech**
- NVIDIA Isaac Sim 5.1 · ROS2 Humble · Python 3.10/3.11 · YOLO OBB · PyQt5

**Repository**
- https://github.com/yevettee/AquaSweep

---

### 4. MediCart 🤖🏥 — 병원 순회 도우미 로봇 시스템

**Overview**
- TurtleBot4 + OAK-D 카메라 + RPLIDAR 기반의 병동 순찰 및 간호사 보조 로봇
- 모드 A: 자율 순찰(병실별 환자 유무 확인, QR 코드 신원 확인)
- 모드 B: 간호사 추적(간호사 따라다니기) + 약품 라벨 OCR 검증(GCP Vision)
- 웹 대시보드(Next.js + Flask)에서 실시간 제어·모니터링

**What I Did**
- Nav2 기반 자율주행 및 미션 매니저 설계
- YOLO/QR 기반 환자 인식 파이프라인 및 OCR(약품 라벨) 통합
- Flask 백엔드와 Next.js 프론트엔드로 구성된 웹 대시보드 및 Firebase 연동
- 시뮬레이션(Gazebo) 환경과 실제 하드웨어 모드 모두 지원하는 빌드·실행 가이드 작성

**Tech**
- ROS2 Humble · Nav2 · TurtleBot4 · OAK-D / RealSense · YOLO · Firebase · Flask · Next.js · GCP Vision API

**Repository**
- https://github.com/yevettee/MediCart

---

## Contact & Links
- GitHub: https://github.com/yevettee
- LinkedIn: https://www.linkedin.com/in/윤정-옥-850b68291?utm_source=share_via&utm_content=profile&utm_medium=member_android
- Portfolio / Notion: [링크 추가 예정]
