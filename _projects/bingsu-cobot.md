---
title: Bingsu Cobot
title_kr: 빙수 제조 협동로봇
one_liner: 주문부터 픽업까지 수행하는 컵빙수 제조 협동로봇
card_roles:
  - Robot Task Sequence 통합
  - Firebase–Robot Controller 연동
  - Handwriting Path Generation
card_stack: [Doosan M0609, ROS 2, Firebase, Task Sequence, Motion Path]
badge: Doosan Bootcamp
featured: true
order: 4
thumbnail: /assets/p01-shaved-ice/제조환경세팅.jpg
github: https://github.com/yevettee/mother_bird
stack: [M0609, ROS2, Firebase, PySide, Python]
facts:
  - { label: Robot, value: Doosan M0609 }
  - { label: Team, value: 6명 }
  - { label: Duration, value: 2026.04.14 – 04.27 (2주) }
media:
  - { type: video, src: /assets/p01-shaved-ice/빙수로봇.mp4, caption: 최종 시연 영상 }
  - { type: image, src: /assets/p01-shaved-ice/제조환경세팅.jpg, caption: 제조 환경 세팅 }
  - { type: image, src: /assets/p01-shaved-ice/글씨쓰는 로봇.png, caption: 닉네임 쓰는 로봇 }
  - { type: image, src: /assets/p01-shaved-ice/펜_최종.jpg, caption: 최종 펜 홀더구조 }
role:
  - 주문부터 픽업까지 전체 Robot Task Sequence 통합
  - Firebase Order/State와 Robot Controller 연동
  - HersheyFonts 기반 Nickname Motion Path 생성
challenge_issue: >-
  닉네임 작성 과정에서 펜 파지 불안정과 접촉 압력 편차로 인해 글씨가 밀리거나 필기 품질이 일정하지 않는 문제가 발생했습니다.
challenge_fix: >-
  여러 Holder Prototype을 제작하며 파지 구조와 접촉 압력을 비교했고, 최종적으로 스프링 기반 분필 Holder를 적용하여 일정한 필기 압력을 유지하도록 개선했습니다.
lessons: |-
  부트캠프 첫 프로젝트에서는 기능별 **ROS 2 Interface**가 충분히 정의되지 않은 상태에서 병렬 개발을 진행했습니다. 각 기능은 정상적으로 동작했지만, Interface가 일관되지 않아 최종 Task Sequence를 통합하는 과정에서 일부 로직을 하드코딩으로 연결해야 했습니다.

  이 경험을 통해 **시스템 통합에서는 기능 구현보다 인터페이스를 먼저 정의하고 공유하는 것이 중요하다**는 점을 배웠습니다. 이후 프로젝트에서는 개발 전에 ROS 2 Interface를 먼저 설계하고 팀원들과 공유한 뒤 기능을 구현하는 방식을 적용했고, 병렬 개발과 시스템 통합을 더 안정적으로 진행할 수 있었습니다.
---

## Overview

Doosan M0609 기반 컵빙수 제조 협동로봇입니다.

고객이 Web에서 주문과 닉네임을 입력하면 제빙, 토핑, 닉네임 작성, 픽업 안내까지 전체 제조 과정을 자동으로 수행합니다.

관리자는 Firebase 기반 Dashboard에서 Task 진행 상태를 실시간으로 모니터링하고, 비상 정지와 작업 재개를 제어할 수 있습니다.
