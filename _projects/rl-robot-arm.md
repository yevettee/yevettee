---
title: RL Robot Arm
title_kr: 강화학습 로봇팔
one_liner: RGB-D Pick-and-Place 강화학습 구조를 분석한 스터디 프로젝트
card_roles:
  - DQN Pick-and-Place Pipeline 분석
  - Camera-to-World 좌표 변환 구현
card_stack: [PyBullet, DQN, RGB-D, Camera Transform]
badge: School Project
featured: false
order: 6
thumbnail: /assets/p05-rl-robot/강화학습.png
github: https://github.com/yevettee/RL_robot
stack: [PyBullet, DQN, Python, OpenCV]
facts:
  - { label: Robot, value: 로봇팔 (PyBullet 시뮬레이션) }
  - { label: Team, value: 4명 }
  - { label: Duration, value: 2024.03.15 – 12.23 (스터디) }
media:
  - { type: image, src: /assets/p05-rl-robot/강화학습.png, caption: PyBullet 학습 환경 }
role:
  - Reference code architecture 분석
  - Camera-to-world 좌표 변환 구현
  - Depth normalization 구현
---

## Overview

PyBullet 기반 RGB-D pick-and-place DRL study project입니다. RGB-D observation을 입력으로 받아 물체를 집고 목표 위치에 놓는 pick-and-place 시나리오를 재현한 프로젝트입니다.

Reference DQN code를 기준으로 perception preprocessing, coordinate transform, action selection 흐름을 분석하였습니다.
