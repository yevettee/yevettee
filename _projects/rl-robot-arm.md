---
title: RL Robot Arm
title_kr: 강화학습 로봇팔
one_liner: DQN pick-and-place agent in PyBullet (DRL study)
badge: School Project
featured: false
order: 6
thumbnail: /assets/p05-rl-robot/강화학습.png
github: https://github.com/yevettee/RL_robot
stack: [PyBullet, DQN, Python, OpenCV]
media:
  - { type: image, src: /assets/p05-rl-robot/강화학습.png, caption: PyBullet 학습 환경 }
role:
  - Reference code architecture 분석
  - Camera-to-world 좌표 변환 구현
  - Depth normalization 구현
implementation_title: Study Note
implementation:
  - "Code analysis: reference DQN code의 perception, action selection 흐름을 분석."
  - "Camera geometry: camera-to-world transform과 depth normalization 흐름을 구현."
  - "PyBullet replay: RGB-D input 기반 DQN pick-and-place structure를 PyBullet에서 재현."
---

## Project Topic

PyBullet 기반 RGB-D pick-and-place DRL study project입니다. RGB-D observation을 입력으로 받아 물체를 집고 목표 위치에 놓는 pick-and-place 시나리오를 재현합니다.

Reference DQN code를 기준으로 perception preprocessing, coordinate transform, action selection 흐름을 분석합니다.
