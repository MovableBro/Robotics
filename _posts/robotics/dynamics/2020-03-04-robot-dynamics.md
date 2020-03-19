---
title: "Robot Dynamics"
categories: 
  - robotics
  - dynamics
tags:
  - inverse dynamics
  - forward dynamics
---
**Changes in Service:** We just updated our [privacy policy](#) here to better service our customers. We recommend reviewing the changes.
{: .notice}

**Primary Notice:** Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer nec odio. [Praesent libero](#). Sed cursus ante dapibus diam. Sed nisi. Nulla quis sem at nibh elementum imperdiet.
{: .notice--primary}

**Info Notice:** Lorem ipsum dolor sit amet, [consectetur adipiscing elit](#). Integer nec odio. Praesent libero. Sed cursus ante dapibus diam. Sed nisi. Nulla quis sem at nibh elementum imperdiet.
{: .notice--info}  

# 로봇동역학

## 개요
**로봇의 특성 :** 로봇 동역학에 대해 이해하기에 앞서, 로봇의 특성에 대한 이해가 필요하다. 로봇은 각 조인트가 서로 연결되어 움직임이 서로 영향을 준다. 즉, 2번 관절의 움직임이 1번관절과 3번관절의 움직임에 영향을 준다. 인접한 관절에 영향을 주면, 궁극적으로는 한 관절의 움직임이 다른 모든 관절의 움직임에 영향을 준다는 결론이 나온다. 로봇은 비선형이다.
{: .notice}

**로봇 동적 모델의 특성 :** 일반적인 n 축 로봇의 동역학 모델은 널리 알려져 있다. 로봇 동역학 모델을 분석하기 전에 그 특성을 알 필요가 있다. 첫번 째 특성은 관성행렬 M(q) 가 대칭(symmetrical)이고 양의 한정 행렬(positive definite)이라는 것이다. 그 두번째 특징은 관성행렬과 코리올리스 원심력 행렬과 다음의 관계가 성립한다는 것이다. 이를 skew symmetry 하다고 한다.
{: .notice--abc}

## 로봇 동역학 모델
**알아두기 :** 로봇 동역학모델을 만들기 위해서 정의해야 할 변수들이 있다. 그 변수들의 물리적인 의미를 이해하고 나면 기계적으로 순서와 공식에 따라 대입해주기만 하면 로봇 모델이 튀어나올 것이다. 여기서 로봇 모델이란 로봇의 움직임과 관련된 관성행렬 M 과 코리올리와 원심력항 C 그리고 중력항 G 과 로봇의 관절에 작용하는 토크 사이의 상관관계를 표현한 식을 말한다. 로봇 동역학 식은 아래와 같다.
{: .notice--알아두기}

## 정동역학과 역동역학
영어로는 foward dynamics와 inverse dynamics 이다.  
정동역학은 시뮬레이션에 필요하고, 실제 로봇을 움직이기 위해서는 역동역학이 필요하다.

### 정동역학
정동역학은 로봇에 외력을 인가하면 얼마나 움직이더라를 살펴보는것이 목표이다.  
즉, 조인트에 인가되는 토크의 값을 알고 있을 때, 관절이 움직이는 각도, 각속도, 각가속도를 알아내는 것이 목표이다.

### 역동역학
역동역학은 정동역학의 반대이다.  
로봇이 움직이는데 필요한 토크가 얼마인지를 계산해 내는데 관심이 있다.  
실제 로봇을 우리가 원하는 위치로 움직이려면 로봇 관절에 박혀있는 모터에서 얼마만큼의 토크 출력이 나와줘야 하는지를 아는 것이다.
