---
title: Bingsu Cobot
title_kr: 빙수 제조 협동로봇
one_liner: 빙수 제조 협동로봇 (Doosan M0609)
badge: Doosan Bootcamp
featured: true
order: 3
thumbnail: /assets/p01-shaved-ice/제조환경세팅.jpg
github: https://github.com/yevettee/mother_bird
stack: [M0609, ROS2, Firebase, PySide, Python]
media:
  - { type: image, src: /assets/p01-shaved-ice/제조환경세팅.jpg, caption: 제조 환경 세팅 }
  - { type: image, src: /assets/p01-shaved-ice/글씨쓰는 로봇.png, caption: 닉네임 쓰는 로봇 }
  - { type: image, src: /assets/p01-shaved-ice/펜_최종.jpg, caption: 최종 펜 홀더구조 }
role:
  - 주문부터 픽업까지 로봇 task sequence 통합
  - Firebase order/state와 robot controller 연동
  - 닉네임 작성 기능 구현
challenge_issue: >-
  손글씨 작성 과정에서 펜 파지 불안정, 접촉 압력 편차로 인해 글씨가 밀리거나 품질이 일정하지 않는 문제가 발생
challenge_fix: >-
  다양한 Pen Holder Prototype을 제작·비교하여 적절한 접촉 압력을 확보하고,
스프링 구조의 Chalk Holder를 적용해 필기 품질과 안정성을 개선
implementation_title: Implementation Details
implementation:
  - "Task sequence: Firebase order/state를 robot controller와 연결하고 제조 단계별 실행 흐름을 통합."
  - "Handwriting Path: HersheyFonts Stroke Path에 Scale Normalization, Coordinate Transform, Interpolation을 적용하여 Robot Motion Path를 생성."
  - "Hardware debugging: 펜 파지, 접촉 압력, 글씨 밀림 사이의 trade-off를 holder prototype 테스트로 확인하고 스프링 구조의 분필 홀더로 개선."
  - "Integration lesson: 이후 프로젝트부터 ROS 2 interface와 mock data를 먼저 고정한 뒤 module integration을 진행하는 방식으로 전환."
---

## Project Topic

Doosan M0609로 컵빙수 제조 과정을 자동화한 cobot project입니다.

고객이 Web에서 주문과 닉네임을 입력하면, 제빙부터 토핑, 닉네임 작성, 픽업 안내까지 전 과정을 자동으로 수행합니다.

관리자 Web에서는 24개의 Task 진행 상태를 실시간으로 모니터링하고, 특정 Task 이동, 비상 정지, 작업 재시작을 제어할 수 있습니다. 또한 외력 감지 시 로봇을 즉시 정지하고, 해제 후 중단된 Task부터 작업을 재개할 수 있습니다.