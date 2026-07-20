---
title: Space Debris Capture Testbed
title_kr: 우주 쓰레기 포획 테스트베드
one_liner: 우주 쓰레기 포획용 회전형 위성 Mockup
card_roles:
  - Fusion 360 기반 3층형 Mockup 설계·제작
  - Dynamixel 기반 독립 회전축 구현
card_stack: [xArm Lite 6, Dynamixel, OpenRB-150, XBee]
badge: Research Project
featured: false
order: 5
thumbnail: /assets/p08-embedded/satellite_testbed_전체사진.png
stack: [Python, xArm Python SDK, Dynamixel, OpenRB-150, XBee, RS485, Fusion 360]
facts:
  - { label: Robot, value: xArm Lite 6 · 회전형 폐위성 Mockup }
  - { label: Team, value: 연구실 공동 연구 · Mockup 개인 담당 }
  - { label: Duration, value: 2024.04 – 2024.05 }
media:
  - { type: image, src: /assets/p08-embedded/satellite_testbed_전체사진.png, caption: xArm Lite 6 끝단에 장착한 회전형 폐위성 Mockup, fit: contain }
  - { type: image, src: /assets/p08-embedded/satellite_testbed_fusion360.png, caption: Fusion 360 기구 설계, fit: contain }
  - { type: image, src: /assets/p08-embedded/satellite_testbed_설계도.png, caption: Satellite Mockup 외부 설계, fit: contain }
  - { type: image, src: /assets/p08-embedded/satellite_testbed_내부_설계도.png, caption: 3층형 내부 부품 배치, fit: contain }
  - { type: image, src: /assets/p08-embedded/satellite_testbed_ 내부조립사진.png, caption: OpenRB-150·XBee·전원부 내부 조립 }
role:
  - Fusion 360 기반 폐위성 Mockup 외형 및 3층 탑재 구조 설계·제작
  - UFactory Python SDK 기반 xArm Lite 6 위치·자세 제어
  - XBee·OpenRB-150·RS485·전원부를 연결한 Mockup 회전 구동 시스템 통합
challenge_issue: >-
  자전하는 폐위성 상황을 재현하려면 Mockup이 한 방향으로 계속 회전해야
  했지만, xArm Lite 6의 마지막 관절은 동작 각도가 제한되어 연속 회전이
  불가능했습니다.
challenge_fix: >-
  로봇팔 끝단에 Dynamixel 기반 독립 회전축을 추가하고, Ground Station의
  각속도 명령을 XBee로 전달했습니다. 이를 통해 로봇팔의 위치·자세 제어와
  폐위성 Mockup의 연속 회전을 분리했습니다.
implementation:
  - "<strong>3층형 탑재 구조</strong><br>1층에 OpenRB-150·TTL to RS485 Bridge·24V→12V Converter, 2층에 XBee, 3층에 Dynamixel을 배치하여 제한된 내부 공간에 제어·통신·전원·구동부를 통합"
  - "<strong>탑재 전원·통신 구성</strong><br>로봇 시스템의 24V 전원을 12V로 변환해 탑재부에 공급하고, PC와 직접 연결되지 않은 OpenRB-150이 XBee 명령을 수신해 RS485로 Dynamixel을 구동하도록 구성"
---

## Overview

두 개의 로봇팔을 탑재한 정육면체형 기체로 우주 쓰레기를 포획하는 시스템을 개발하는 연구 프로젝트입니다.

연구실에서 개발하는 포획 기체의 자세 추정과 로봇팔 동작을 검증할 수 있도록, xArm Lite 6 끝단에 날개형 폐위성 Mockup을 장착해 우주 공간에서 폐위성이 자전하는 상황을 재현했습니다. Ground Station에서 회전 명령을 전달하면 Mockup이 일정한 각속도로 회전하는 구조입니다.

저는 회전형 폐위성 Mockup의 기구 설계·제작과 구동·통신·전원 시스템 통합을 담당했습니다.
