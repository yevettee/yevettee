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
  - { type: image, src: /assets/p01-shaved-ice/글씨쓰는 로봇.png, caption: 닉네임 손글씨를 쓰는 로봇 }
  - { type: image, src: /assets/p01-shaved-ice/펜_최종.jpg, caption: 최종 펜 홀더 }
role:
  - 주문부터 픽업까지 로봇 task sequence 통합
  - Firebase 주문/상태 값과 robot controller 연동
  - HersheyFonts 기반 handwriting path generation
challenge: >-
  글씨를 쓸 때 펜 파지와 접촉 압력이 불안정했습니다. 지우개와 펜 뚜껑으로
  holder prototype을 테스트한 뒤, 분필 홀더에 스프링과 스펀지를 넣어 펜이
  빠지지 않으면서 일정한 압력으로 닿도록 조정했습니다.
---

두산 M0609 컵빙수 제조 로봇입니다. Firebase의 주문/상태 값을 robot
controller와 연결하고, 주문부터 픽업까지 로봇 task sequence와 닉네임
손글씨 경로를 구현했습니다.
