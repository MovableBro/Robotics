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
