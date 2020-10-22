# 딥러닝(Deep Learning)

- 용어 정리
  - feed forward : 트레이닝 데이터가 신경망으로 들어가서 최종적으로 손실함수를 구할 때까지의 과정
  - epochs : 손실 함수가 최소가 될 때까지를 반복하는 과정
  - 손실 함수(loss function) : training data와 정답(t)과 입력(x)에 대한 계산 값 y의 차이를 모두 더해 수식으로 나타낸 것

### 신경망(Neural Network)
개념 : 인간의 신경세포 뉴런으로 연결된 신경망 동작원리와 유사하게 돌아가는 딥러닝을 말한다.

- 활성화 함수 : 입력 신호를 받아 특정 값의 임계점을 넘어서는 경우에, 출력을 생성해주는 함수
  ```
  [예시]
  Logistic Regression 시스템의 sigmoid 함수가 대표적인 활성화 함수
  sigmoid에서의 임계점은 0.5, 0.5보다 크다면 1을 출력, 작다면 출력을 내보내지 않는다.
  ```

### Multi-Variable Logistic Regression
- 신경 세포인 뉴런 동작원리를 머신러닝에 적용하기 위해서는 아래를 반복

  1. 입력 신호와 가중치(W)를 곱하고 적당한 바이어스(b)를 더한 후(*Linear Regression*) 
  
  2. 그 값을 활성화 함수(sigmoid) 입력으로 전달(*Classification*)해서 sigmoid 함수 임계점 0.5를 넘으면 1, 그렇지 않으면 0
  
### 딥러닝(Deep Learning)
- 구성 : 입력층(Input Layer), 1개 이상의 은닉층(Hidden Layer), 출력층(Output Layer)
- 개념
  ```
  노드가 서로 연결되어 있는 신경망 구조를 바탕으로 입력층, 1개 이상의 은닉층, 출력층을 구축하고, 
  출력층에서의 오차를 기반으로 각 노드(뉴런)의 가중치(Weight)를 학습하는 머신러닝 한 분야
  ```
