---
title: Bingsu Cobot
title_kr: 빙수 제조 협동로봇
one_liner: Shaved-ice making cobot (Doosan M0609)
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
  - HersheyFonts 기반 handwriting path generation
challenge_issue: >-
  손글씨 동작 중 펜 파지 불안정, 접촉 압력 편차, 글씨 밀림 발생.
challenge_fix: >-
  펜이 빠지지 않으면서 종이를 과하게 누르지 않는 압력을 찾기 위해 holder
  prototype을 테스트하고, 스프링 구조의 분필 홀더 적용.
implementation_title: Implementation Details
implementation:
  - "Task sequence: Firebase order/state를 robot controller와 연결하고 제조 단계별 execution flow를 통합."
  - "Handwriting path: HersheyFonts stroke path에 scale normalization, coordinate transform, interpolation을 적용해 robot motion path로 변환."
  - "Hardware debugging: 펜 파지, 접촉 압력, 글씨 밀림 사이의 trade-off를 holder prototype 테스트로 확인하고 스프링 구조의 분필 홀더로 개선."
  - "Integration lesson: 이후 프로젝트부터 ROS 2 interface와 mock data를 먼저 고정한 뒤 module integration을 진행하는 방식으로 전환."
---

## Project Topic

Doosan M0609로 컵빙수 제조 과정을 자동화한 cobot project입니다.

고객이 web에서 주문과 닉네임을 입력하면 제빙기 동작, 재료 토핑, 닉네임 손글씨 작성, 픽업 위치 전달까지 이어지는 제조 시나리오가 진행됩니다.

관리자 web에서는 24개 task 중 현재 진행 상태를 모니터링하고, 원하는 task 이동, 비상정지, 처음부터 다시 진행을 제어할 수 있습니다.

외력 감지 시 로봇이 비상정지하며, 관리자 web에서 해제 후 정지된 task부터 이어서 진행할 수 있습니다.
