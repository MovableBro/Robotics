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
- d1*I <= M(q) <= d2*I
- Mdot - 2*Cm = 0



## 로봇 동역학 모델
**알아두기 :** 로봇 동역학모델을 만들기 위해서 정의해야 할 변수들이 있다. 그 변수들의 물리적인 의미를 이해하고 나면 기계적으로 순서와 공식에 따라 대입해주기만 하면 로봇 모델이 튀어나올 것이다. 여기서 로봇 모델이란 로봇의 움직임과 관련된 관성행렬 M 과 코리올리와 원심력항 C 그리고 중력항 G 과 로봇의 관절에 작용하는 토크 사이의 상관관계를 표현한 식을 말한다. 로봇 동역학 식은 아래와 같다.
{: .notice--알아두기}

**방법론 :** 로봇 동역학 모델을 만드는 방법론은 크게 Newton Euler 와 Lagrangian Euler 방식으로 나뉠 수 있는데, 계산량이 적은 Newton Euler 방식이 실시간 제어를 가능하게 하여 많이 사용된다. 이 Newton Euler의 방법 중 Recursive Newton Euler 방식이 있는데, 이 것 방법론을 이용하여 로봇 동역학 모델을 구해보는 연습을 해 볼 것을 추천한다.
{: .notics--methods}

### Newton Euler 방정식
#### 변수들에 대한 설명
**당부 :** 변수들에 대한 물리적인 이해를 먼저 하는 것이 좋다. 나중에 알고리즘을 개발 할 때는 동역학 관련된 변수들을 가져다가 쓰는 경우가 생기기 때문이다. 관성행렬의 값을 구성하는 것들은 아래 변수들의 조합이다. 관성행렬은 토크 모멘텀을 구하는데 사용되기도 한다. 토크 모멘텀을 관측하면 외력을 추정할 수 있다. 종합해서 말 하면 모든 로보틱스 알고리즘은 아래의 변수들을 재료로 해서 만들어진다는 것이다.
{: .notice--}

1. 무게 관련 변수들
  - $$m_i$$ : 링크 i 전체 질량
  - $$ I_i $$ : 원점 좌표에 관한 링크 i 의 무게 중심에서의 관성
2. 길이 관련 변수들
  - ri bar : 원점에서 링크 i의 무게중심 까지의 거리
  - si bar : i 좌표의 원점에서부터 링크 i 의 무게 중심점까지의 거리
  - p(i-1) to (i) : i-1 좌표에서 i 좌표의 원점까지의 거리
3. 속도 관련 변수들
  - vi bar : 링크 i 의 무게중심에서의 선속도
4. 힘 관련 변수들
  - Fi : 링크 i 의 무게 중심점에 작용되는 전체 외부 힘
  - Ni : 링크 i 의 무게중심점에 적용되는 전체 외부 모멘트
  - fi : 링크 i-1이 링크 i에 적용하는 힘
  - ni : 링크 i-1이 링크 i에 적용하는 모멘트  
  

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
