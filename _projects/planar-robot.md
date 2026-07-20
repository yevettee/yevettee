---
title: 3-Axis Planar Robot Arm
title_kr: 3축 planar 로봇팔
one_liner: 기구학 이론부터 실물 원 그리기까지 구현한 3축 Planar Robot Arm
card_roles:
  - Forward / Inverse Kinematics 구현
  - Dynamixel 기반 3축 Robot Arm 제작
card_stack: [MATLAB, Dynamixel SDK, OpenRB-150, Kinematics]
badge: School Project
featured: false
order: 8
thumbnail: /assets/p06-planar/3축로봇팔_완성품.png
stack: [MATLAB, Arduino, Dynamixel SDK, OpenRB-150, 3D Printing]
facts:
  - { label: Robot, value: 3축 로봇팔 (Dynamixel · 자체 제작) }
  - { label: Team, value: 6명 }
  - { label: Duration, value: 2023.12 – 2024.02 (동계 스터디) }
media:
  - { type: image, src: /assets/p06-planar/3-planar-demo.gif, caption: 원 그리기 동작 }
  - { type: image, src: /assets/p06-planar/3축로봇팔_완성품.png, caption: 3축 planar 로봇팔 완성품 }
  - { type: image, src: /assets/p06-planar/3축로봇팔_원그리기.png, caption: 원 그리기 결과 }
role:
  - Rotation matrix, DH parameter, 순/역기구학 이론 학습
  - MATLAB 2링크·3링크 planar 원 그리기 시뮬레이션. 기하 해법과 수치 해법 비교
  - Dynamixel 3개, OpenRB-150, 3D 프린팅 링크로 실물 제작 및 원 궤적 검증
challenge_issue: >-
  Singularity 영역에서 원 궤적이 레몬 형태로 찌그러지는 문제 발생. 좌표와
  각도를 바꿔가며 특이점 회피를 시도했지만, 모터 성능 한계와 관절 충돌 등
  복합 원인이 존재
challenge_fix: >-
  소프트웨어만으로 해결할 수 없는 기계적 한계를 확인. 이후 알고리즘과
  시스템을 설계할 때 물리적 한계를 전제로 두는 기준을 얻음
---

## Overview

한국항공대학교 RCS 동계 스터디 프로젝트입니다 (2023.12 – 2024.02).

2링크·3링크 planar 로봇팔의 기구학 이론을 학습하고, MATLAB 시뮬레이션으로 원 궤적을 검증한 뒤, Dynamixel 기반 실물 로봇팔로 원을 그리는 단계까지 진행했습니다.
