# CNN

## Feed Forward

### 입력층

### 컨볼루션층

1. padding
    - 컨볼루션 연산을 수행하기 전에 입력 데이터 주변을 특정 값 (예를들면 0)으로 채우는 것을 말하며, 컨볼루션 연산에서 자주 이용되는 방법
  
2. conv(컨볼루션, convolution)
    - 입력데이터와 가중치들의 집합체인 다양한(filter)와의 컨볼루션 연산을 통해 **입력데이터의 특징(feature)**을 추출하는 역할을 수행함

3. Relu
    - 활성화 함수 사용
    - Classification
    - 보통 특정값이상이면 값을 내보내고 아니면 0

4. pooling(폴링)
    - 입력 정보를 최대값 , 최소값 , 평균값등으로 압축하여 **데이터 연산량을 줄여주는 역할** 수행 

### 출력층

## 손실 함수