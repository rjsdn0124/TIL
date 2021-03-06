# Logistic Regression

## 이진 분류(Binary Classification)
- 일상 속 두 개의 선택지 중 하나를 고르는 문제를 이진 분류라 한다.
- 이 이진 분류를 풀기 위한 대표적인 알고리즘으로 로지스틱 회귀가 있따. (이름은 회귀지만 분류 작업에 사용가능.)
- 해당 문제를 표현한 데이터들로 그려진 그래프는 S자 형태로 표현된다. 따라서 선형 획귀의 Wx+b와 같은 직선 함수로 표현할 수 없음. 그래서 시그모이드 함수라는 함수를 사용.

### 시그모이드 함수
- S자로 그래프를 그려주는 함수. 보통 sigmoid(Wx+b)로 사용. sigmoid함수 내에 linear함수가 들어있는 꼴이라 둘을 합쳐서 거쳐가는 방향으로 사용한다. 가중치 W는 커질수록 그래프의 경사를 가파르게 하는 경사도에 관여하고, 편향 b는 커질수록 그래프가 왼쪽으로 이동시도록 관여한다. 
- 해당 함수는 입력 값이 한없이 커지면 1에 수렴하고 작아지면 0에 수렴한다. 따라서 0과 1로 구분하기는 어렵고, 보통 임계값을 정하여 해당 값보다 크면 1, 작으면 0으로 진행한다. 이를 확률로 생각하면 해당 레이블에 속할 확률로도 생각할 수 잇따.

### 비용 함수(오차, = loss function)
- 로지스틱 회귀의 가설은 시그모이드 함수로 표현이 가능하다. 따라서 이 함수를 통해 가중치 W와 편향 b를 찾아야 하는데, 선형 회귀에서의 평균 제곱 오차의 수식을 사용하여 해당 식을 미분하면 선형 회귀와 달리 기울기가 0인 점이 하나가 아닌 여러 점이 나와 심한 비볼록(non-convex) 형태의 그래프가 나온다.
<br/> 해당 그래프를 통해 오차의 최솟값을 찾고자 그냥 경사 하강법을 사용하게 된다면, 오차가 최소값이 되는 구간에 도착했따고 판단을 내려도 해당 지점이 실제 최소값이 아닐 가능성이 있다. 이를 전체의 최솟값인 글로벌 미니멈이 아닌 특정 구역에서의 최솟값인 로컬 미니멈에 도달했따고 한다.
<br/> 따라서 이진 분류의 특성상 0또는 1로의 값으로 이루어져 있고, 시그모이드 함수의 출력값은 0또는 1로 이루어져있어 1일 때 예측 값이 0이면 오차가 커지는 이런 형태이다. 이는 로그함수의 형태와 같다. 이 함수를 이용해서 시그모이드 함수에서의 비용함수를 구해야 한다.