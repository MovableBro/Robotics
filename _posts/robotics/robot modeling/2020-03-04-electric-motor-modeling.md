---
title: "motor dynamic model"
categories:
  - robotics
  - robot-modeling
tags:
  - electric motor
  - modeling
  - dynamics
  - electric circuit
---

# 1축 모터 모델링

## 개요
1축 모터의 모델링은 단순하다.  
그러나 1축 모터의 모델링은 중요하다.  
1축 모터의 모델링이 중요해 지는 순간은 모터의 회전 inertia 가 전체 inertia에 영향을 미칠 만큼 미미하지 않을 때 이다.  
보통은 모터의 회전 inertia를 무시하는데, 감속비가 100대 1인 경우 링크단의 inertia 가 1만분의 1이 되어 적용되기 때문에 
간혹 모터의 회전 inertia의 영향력이 큰 경우들이 있다.

## 모델링 순서
1. 회로도를 그린다.
2. 수식을 적는다.
3. 제어 흐름도를 그린다.

## 예시
![이미지](https://player.slidesplayer.org/60/11177554/slides/slide_7.jpg)
