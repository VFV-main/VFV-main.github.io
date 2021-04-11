--- 
layout: post
title: 'Optimization'
use_math: true
categories: [ML,DL]
tags: Optimization
---
최적화 ( Optimization )
![](https://heung-bae-lee.github.io/image/optimization_theory_and_algorithm_learning.png)

$minimize_x f\left(x\right)$  $\;\;\;\;\;\;$$\;\;\;\;\;\;\;\;\;$ : 목적함수
$\;\;\;\;$ $g_i(x)\leq0, \;\;\;(i=1...m)$  : 부등식 제약조건
$\;\;\;\;$ $ h_j(x)=0, \;\;\;(i=1...m)$  : 등식 제약조건
     
     
-      최적해를 찾는 문제에 적용
-      연속 변수와 불연속 변수로 나뉨
-      제약 조건을 지키면서 목적함수가 최소가 되게하는 X를 찾음  


									1. 브루트 포스


![브루트포스.PNG](C:\Users\승현\Pictures\브루트포스.PNG)

	- 가능한 모든 경우를 다 해보는 것
	
    x의 최적의 범위를 알아야함
    x를 찾기위해 모둔지점을 계산해야함
    f(x)의 계산복잡도가 매우 높음
매우 비효율적임 


									2. 경사하강법 (GBM)


![GBM.PNG](C:\Users\승현\Pictures\GBM.PNG)

	각 지점마다 미분을 해가며 기울기를 구하고 최소의 값을 찾을때까지 반복  (f(x) 값이 변하지 않을 때까지 반복)
    
1차원 :$\;\;\;\;\;\;\;\;$ $a$ : 학습률
   $x_n = x_{n-1} - a\frac{df(x_{(n-1)})}{dx}$

n차원 :
	$x_n = x_{n-1}-a\,f(x_{n-1})$

###### ==**적절한 학습률을 선택하는 것이 중요함**==

![](https://heung-bae-lee.github.io/image/selection_of_learning_rate.png)




![](https://heung-bae-lee.github.io/image/analysis_and_numerical_method.png)






![모멘텀.PNG](C:\Users\승현\Pictures\모멘텀.PNG)

- 이동벡터와 이전 기울기로 계산


#### AdaGrad 
    : 변수별 학습률 변경
  $ g_t = g_{t-1} + (f(x_{t-1}))^2 $ <-- 제곱 때문에 $g_t$가 커지면서 점점 학습 불가
  $ x_t = x_{t-1} - \frac{\eta}{\sqrt{g_t+\epsilon}}$
  
  $g_t$ : t 번째 단계까지 기울기의 누적 크기
  $\epsilon$ : 0으로 나누는것을 방지 $\approx 10^{-6}$ 

 : ==기울기가 커져 학습이 많이 된 변수는 학습률 감소==
 

#### RMSProp 
    : 지수평균 이용
   $ g_t = \gamma\,g_{t-1}+(1-\gamma)(f(x_{t-1}))^2$
   $ x_t = x_{t-1}-\frac{\eta}{\sqrt{g_t+\epsilon}}$
   $ \gamma $ : 지수 평균 업데이트 계수
   
	감마를 곱해서 학습율에 큰 지장이 없게 만들어 주었다.
    
### Adam (Adaptive estimation) 
  ##### :  RMSProp + Momentum


![애덤.PNG](C:\Users\승현\Pictures\애덤.PNG)











