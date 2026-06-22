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
- Linux / Ubuntu

### Programming
- Python
- C++

### Perception / Vision
- OpenCV
- YOLO (Object Detection)
- Sensor Fusion

### Tools & Platforms
- Git / GitHub
- Docker
- Notion
- Firebase (Database)

---

## Featured Projects

### 1. Doob-E: AI-Powered Service Robot Web System
> 정비소 도우미 로봇 웹 시스템 | 음성 명령 기반 물체 인식 및 pick 작업

**Overview**
- 두산로보틱스 M0609 협작로봇과 RealSense depth camera를 활용한 AI 기반 정비소 도우미 로봇 웹 시스템
- Wake word("두비야") 인식 후 음성 명령으로 로봇이 특정 물체를 인식하고 집거나 정리하는 통합 시스템
- 웹 UI에서 실시간 YOLO 감지 결과, 로봇 상태, 카메라 영상 모니터링

**What I Did**
- **ROS2 통합 아키텍처 설계**: 음성 인식(STT/LLM), 비전 처리(YOLO), 로봇 제어를 연결하는 ROS2 노드 설계
- **로봇 액션 노드 구현** (`robot_action_node.py`): 카메라 좌표 → 로봇 베이스 좌표 변환, approach & pick 동작 구현
- **정렬/배치 노드 구현** (`robot_sort_node.py`): 여러 물체를 firebase 슬롯 정보를 기반으로 자동 정렬
- **음성-비전 명령 매칭**: STT/LLM으로 생성된 command JSON과 YOLO 감지 결과를 매칭하여 정확한 타겟 선택
- **실시간 모니터링 웹 UI**: RealSense 카메라 영상, YOLO 감지, 로봇 상태를 웹 대시보드에서 실시간 표시
- **안전성 검증**: Dry-run, approach-only 모드로 단계별 테스트 및 pick 높이 보정 자동화

**Tech**
- ROS2 (Humble) · Python · OpenCV · YOLO v8 · RealSense SDK
- STT/LLM (OpenAI API) · TTS · Firebase · Web UI (Flask)

**Repository**
- [Doob-E GitHub](https://github.com/yevettee/Doob-E)

---

### 2. mother_bird
> 프로젝트 한 줄 요약 필요

**Overview**
- [프로젝트 목적 작성]
- [해결하려던 문제 작성]

**What I Did**
- [본인이 맡은 역할]
- [구현/검증한 핵심 기능]
- [사용 기술]

**Tech**
- ROS2 / Python / C++ / Gazebo / YOLO / etc.

**Repository**
- [mother_bird 링크]

---

### 3. AquaSweep
> 프로젝트 한 줄 요약 필요

**Overview**
- [프로젝트 목적 작성]
- [해결하려던 문제 작성]

**What I Did**
- [본인이 맡은 역할]
- [구현/검증한 핵심 기능]
- [사용 기술]

**Tech**
- [기술 스택]

**Repository**
- [AquaSweep 링크]

---

### 4. MediCart
> 프로젝트 한 줄 요약 필요

**Overview**
- [프로젝트 목적 작성]
- [해결하려던 문제 작성]

**What I Did**
- [본인이 맡은 역할]
- [구현/검증한 핵심 기능]
- [사용 기술]

**Tech**
- [기술 스택]

**Repository**
- [MediCart 링크]

---

## Contact & Links
- **GitHub**: [github.com/yevettee](https://github.com/yevettee)
- **LinkedIn**: [링크 추가]
- **Portfolio / Notion**: [링크 추가]
