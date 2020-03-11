---
title: "Kinematic Model of 6DOF Robot, ABBA"
categories:
  - robot modeling
  - robotics
tags:
  - 7DOF
  - ROBOTIS
  - DH table
---

# 7 자유도 로봇의 기구학 모델링
## 개요
- ROBOTIS Manipulator-H 에 자유도를 추가한 로봇임
- 

## 로봇 모델  
### 기존 6자유도 로봇  
- Roll - Pitch - Pitch - Roll - Pitch - Roll (6DOF) 구조임  
![robotis_manipulator_h](http://emanual.robotis.com/assets/images/platform/manipulator_h/manipulator_product.gif)  
- 평면도  
![robotis_manipulator_h_2d_design_img](http://emanual.robotis.com/assets/images/platform/manipulator_h/manipulator_h_001.jpg)  
- 기존 MDH table

### 1 DOF 추가
- Roll - Pitch - Pitch - Pitch - Roll - Pitch - Roll (7DOF) 구조로 변경

## 결과물
- D-H Table 이 결과물로 산출됨.
- 여기서는 Modified D-H Notation 을 활용함.
  - MDH notation 에서는 base 좌표계가 필요함 (standard DH notation 에서는 EE 좌표계 필요)
  - x0 과 z1 이 수직, 교차 (x(i-1) 과 z(i) 이 교차)

### MDH Table, (length: [mm], Angle: [Deg] )
|i	|a(i-1)	|alpha(i-1)	|d(i)	|offset(i)|
|------|---|---|---|---|
|1	|0	|0	|159 |0|
|2	|0	|-90|	0	 |0|
|3	|0	|-90|-264|0|
|4	|30	|90	|0	 |0|
|5	|-30|	90|	258|0|
|6	|0	|-90|	0	 |0|
|7	|0	|90	|123 |0|

참고) 기존 6 자유도 MDH Table, (length: [mm], Angle: [Deg] )
|i	|a(i-1)	|alpha(i-1)	|d(i)	|offset(i)|
|------|---|---|---|---|
|1	|0	|0	|159 |0|
|2	|0	|-90|0	 |o2|
|3	|a2	|0  |0   |o3|
|4	|-30|90	|258 |0|
|5	|0  |-90|0   |0|
|6	|0	|90 |123 |0|  

a2 = sqrt(264^2 + 30^2)  
o2 = -atan2(264, 30)  
o3 = atan2(264, 30)
