---
title: "External Torque Estimation using Joint Torsion and Motor Current"
categories:
  - robotics
  - dynamics
tags:
  - paper-review
  - MOB
---

# 개요
MOB 정리  
목적 : 로봇에 인가되는 외력을 감지하기 위함  
힘! 이니까 동역학임  
전제조건은 로봇 동역학 모델이 있어야 한다는 것.  
동역학 모델에 따르면 모터가 인가해주는 토크와   
로봇 동역학 식을 보면 로봇 관절에 힘을 가하면 로봇이 어떻게 움직인다는 것을 알 수 있다. (정동역학)  
DOB 와의 비교  
둘 다 비슷한 효과를 낼 수 있음 : 외력을 추정 할 수 있다는 것  
MOB 는 그런데 외력만 추정할 수 있고, DOB는 용도가 더 많다.  
MOB 는 연산량이 적다. (수식으로 예쁘게 풀리는 것 때문에 )   
그러나 DOB 의 경우 M , C, G 행렬을 다 구해야 한다.  
참고 ) 우리 코드에서 M, C, G 행렬 구하는 부분 살펴보면 , q, qdot, q2dot 에 무엇을 구하고 싶은지에 따라 0을 집어 넣고 순서대로 연산하면 성분이 하나씩 나오게 됨.  

# 논문리뷰
- 제목 : Sliding Mode Momentum Observers for Estimation of External Torques and Joint Acceleration  
- 링크 : [논문링크](https://elib.dlr.de/129060/1/root.pdf)
- 저자 : Gianluca Garofalo, Nico Mansfeld, Julius Jankowski and Christian Ott
- 기관 : DLR

## 2장. Robot Dynamics
- rigid joind and rigid link manipulator 를 가정함
- 로봇 동역학 식을 다음과 같이 비선형 미분방정식의 형태로 나타낼 수 있음.
[fig_1. robot dynamics eqn]

## 3장. Momentum Observer
- Collision detection 과 관련된 많은 방법들이 존재함. [15] 참조
- 모멘텀 옵저버가 가장 널리 알려짐
- 외란에 대한 1차 필터의 형태로 사용됨.
- 1차 관측기는 항상 두 가지 가정을 가짐
  - 로봇 동역학 모델은 완벽하게 알려져 있다.
  - 마찰 토크는 무시할만하거나 알고 있다.
- 외력토크는 환경과의 상호작용만을 
  
# MOB 관련 히스토리
## 어려웠던 점
- 처음에 MOB 랑 DOB 랑 차이를 헷갈려했으며, 이 것이 Collision Detection 과 무슨 관계가 있는지 혼란스러웠음.
- Collistion Detection 을 위한 방법론으로서 각 조인트의 Angular Momentum 을 관측하는 기법이 MOB 기법임을 이해함.
- MOB 와 DOB 가 어떤 차이가 있는지는 현재로서 중요하지 않음.
- 다만 Momentum을 관측하는 것이 관절에 인가되는 외력토크를 감지하는 것으로 활용될 수 있도록 하는 과정에 대한 이해가 중요함.

## 해결의 실마리
- MOB를 이해하기 위해서는 1차 필터에 대한 지식이 필요하다.
- 관절에 작용하는 외력 토크가 모멘텀 관측 잔차의 1차 필터와 같다는 것에서 출발한다.

