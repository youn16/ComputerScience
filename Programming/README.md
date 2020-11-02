# PROGRAMMING

## 재귀호출-재귀함수

### 장점
1. 알고리즘 자체가 재귀적으로 표현하기 자연스러울 때. (가독성 이야기)
2. 변수 사용을 줄여 준다.

### 단점
1. 메모리를 많이 차지하며 성능이 반복문에 비해 느리다.
함수 호출시 함수의 매개변수, 지역변수, 리턴 값, 그리고 함수 종료 후 돌아가는 위치가 **스택 메모리**에 저장된다.
재귀함수를 쓰게되면, 함수를 반복적으로 호출하므로, 스택 메모리가 커지고, 호출하는 횟수가 많아지면 **스택오버플로우**가 발생할 수 있다.
또한 스택 프레임을 구성하고 해제하는 과정에서 반복문보다 오버헤드가 들어 성능도 느려진다.