
# 캐시메모리의 설계요소

- [캐시메모리의 설계요소](#캐시메모리의-설계요소)
  - [캐시 메모리의 크기는 어떻게 설계해야 할까요?](#캐시-메모리의-크기는-어떻게-설계해야-할까요)
  - [인출 방식은 어떻게 설계해야 할까요?](#인출-방식은-어떻게-설계해야-할까요)
  - [사상함수는 어떻게 설계해야 할까요?](#사상함수는-어떻게-설계해야-할까요)
    - [사상의 방법](#사상의-방법)
      - [직접사상](#직접사상)
      - [완전연관사상](#완전연관사상)
      - [집합 연관사상](#집합-연관사상)
  - [교체 알고리즘은 무엇이 있을까요?](#교체-알고리즘은-무엇이-있을까요)
  - [쓰기 정책은 무엇이 있을까요?](#쓰기-정책은-무엇이-있을까요)
    - [즉시 쓰기 방식](#즉시-쓰기-방식)
    - [나중쓰기 방식](#나중쓰기-방식)


## 캐시 메모리의 크기는 어떻게 설계해야 할까요?

- 캐시메모리를 크게 만들면, 메인메모리에서 가져올 수 있는 블록이 많기 때문에 **적중률이 높아집니다.** 하지만 용량이 크면 주소를 계산하는데 **많은 시간이 소요됩니다.** 
- 즉 용량이 크다고 해서 비례적으로 속도가 높아지진 않습니다. 
- 또한 캐시메모리의 용량이 클수록 비용이 높아집니다. 
- 결과적으로 캐시메모리의 적중률을 높이면서 접근시간이 낮아지는 것을 막하야합니다. 연구 결과에 의하면 1K~128k 워드가 적절하다고 합니다.


## 인출 방식은 어떻게 설계해야 할까요?

**요구 인출방식 VS 선인출 방식**

- 요구 인출 방식 : CPU가 필요한 명령어나 데이터가 있을 때마다 메인메모리에서 가져오는 방식입니다.

- 선인출 방식 : CPU가 현재 필요한 정보뿐만 아니라 앞으로 필요해질 수 있을 것 같은 정보까지 한꺼번에 가져와서 캐시메모리에 저장해두는 방식입니다. 일반적으로 프로그램은 **참조의 지역성**으로 인해 현재 참조하는 데이터와 인접한 데이터를 참조할 가능성이 높기 때문에 이 경우 효과적입니다.
  - 메인메모리에서 가져오는 블록의 크기가 크면 한번에 많은 데이터를 가져올 수 있지만 인출 시간이 길어지고, 캐시 메모리 크기에 비해 블록이 더 커졌기 때문에 블록이 빈번하게 교체됩니다. 블록이 커질수록 멀리 떨어진 워드들도 함께 가져오기 때문에 가까운 미래에 사용될 가능성이 낮아집니다. 일반적으로 블록의 크기는 4~8워드가 적절합니다.

 
## 사상함수는 어떻게 설계해야 할까요?

- 캐시메모리에서 **슬롯**은 한 블록이 저장되는 장소입니다. 그리고 **태그**는 슬롯에 적재된 블록을 구분해주는 정보입니다. 
- 사상 : 메인메모리에서 캐시메모리로 정보를 옮기는 것.

### 사상의 방법
1. [직접사상](#직접사상)
2. [완전연관사상](#완전연관사상)
3. [집합연관사상](#집합-연관사상)

||직접사상|완전연관사상|집합연관사상|
|:--:|:--:|:--:|:--:|
|적중률|3등|1등|2등|
|검사시간|1등|3등|2등|

<br>

#### 직접사상

- 지정된 하나의 캐시 슬롯으로만 적재
  - 메인메모리의 임의의 블록에서 첫번째 워드는 캐시메모리의 첫번째 슬롯에, 또 다른 블록에서 두번째 워드는 캐시메모리의 두번째 슬롯에만 넣을 수 있는 사상방식입니다.
  - 따라서 서로 다른 블록의 첫번째 워드는 동시에 캐시메모리에 존재할 수 없습니다.
    - 적재 위치가 같으면 swap-out 됨
- 이 방식은 CPU에서 캐시메모리를 조사할 때 해당 라인만 검사하면 되기때문에 간단하지만, 일반적으로 **적중률이 낮습니다**.
- 실행 중인 두 프로그램이 같은 슬롯을 공유하는 경우 캐시 슬롯에 대한 적중률이 떨어져 슬롯 교체가 빈번하게 발생 → 캐시 성능 저하

#### 완전연관사상

- 직접사상의 단점을 보완한 방식입니다.
  - 어떤 슬롯으로든 적재 가능
- 서로 다른 두 블록의 첫번째 워드가 동시에 캐시메모리에 있도록 하기 위해 메인메모리의 **블록번호**를 캐시메모리에 저장합니다.
- 이 방식은 CPU가 캐시메모리를 조사할때, 긴 주소길이로 인해 검사시간이 길어집니다.
- 빈 공간이면 무작정 적재하므로 데이터를 찾을 때 어려움
- 거의 사용되지 않음

#### 집합 연관사상

- 직접사상과 연관사상 방식의 장점을 취합한 방식입니다.
- 집합과 태그가 있는데, 집합 번호는 같고, 태그 번호가 다른 단어=(ex : 임의의 블록 두개의 첫번째 워드)들을 저장할 수 있습니다. 
  - 즉 직접사상에서의 저장공간이 여러개 있다고 생각하면 됩니다.
  - 2-way 세트 연관 사상 (캐시 세트 당 2개의 슬롯)
  - 4-way 세트 연관 사상 (적은 추가 비용 대비 성능 더욱 향상)
- 이로 인해 적중률이 직접사상보다는 높고 연관사상보다는 낮습니다.
- 또한 검사시간은 연관사상보다는 빠르지만 직접사상보다는 느립니다.

 
## 교체 알고리즘은 무엇이 있을까요?

- CPU가 현재 필요한 정보를 캐시메모리에서 찾을 때, 해당 정보가 있으면 적중이라고 하고, 없으면 실패라고 합니다. 실패했을 경우, 메인메모리에서 해당 정보를 가져와야 하는데, 이때 캐시메모리에서도 공간마련을 위해 데이터를 제거해야 합니다. 
- 이때 어떤 데이터를 제거할지 결정하는 알고리즘이 교체 알고리즘입니다.

1. LRU(Least Recently Used)알고리즘
   -  캐시메모리에서 CPU로 인출된적이 없는 블록 중에서 가장 오래된 블록을 제거하고 새로운 블록을 저장하는 방식입니다.
   -  가장 오랫동안 사용하지 않은 페이지 교체
   (페이지 폴트가 일어나는 지점을 기준으로 참조 페이지를 통해 가장 오랫동안 사용하지 않은 값을 삭제하고 새 값
    을 입력)

2. LFU(Least Frequently Used) 알고리즘
   - 캐시메모리에 적재된 블록 중에서 가장 적게 사용된 블록을 교체하는 방식입니다.
   - 가장 사용빈도가 적은 페이지 교체

3. FIFO(First In First Out)알고리즘
   - 가장 먼저 들어온 블록을 내보내는 방식입니다.


4. MRU(Most Recently Used) ↔ LRU
   - 가장 최근에 사용한 페이지 교체 
  
5. MFU(Most Frequently Used) ↔ LFU
   - 가장 사용빈도가 많은 페이지 교체
  
6. 페이지 부재 빈도 기법(Page Fault Frequency) ★★★★
   - 페이지 부재율이 상한선을 초과
      → (프레임 할당이 너무 적다는 것) 프레임 개수를 증가시켜 상한 값 유지
   - 페이지 부재율이 하한선 아래로 내려감
      → (프레임 할당을 너무 많이 받아 메모리가 낭비) 프레임 개수를 감소시켜 하한 값 유지

이외에도 랜덤 알고리즘이 있습니다.
 

## 쓰기 정책은 무엇이 있을까요?

- CPU가 연산 결과를 캐시메모리에 저장해두는 경우가 있습니다. 이 때 캐시메모리와 메인메모리의 데이터 값이 다르게 됩니다. 이를 위해 데이터를 갱신하는 과정이 필요한데, 즉시 쓰기(wirhte-though) 방식과 나중쓰기(write-back)방식이 존재합니다.

### 즉시 쓰기 방식
> CPU에서 연산결과를 캐시메모리에 저장할 경우 바로 메인메모리에도 값을 저장하는 방식입니다. 이 방식은 메인메모리와 캐시메모리의 값이 항상 동일하다는 장점이 있습니다. 하지만 쓰기 동작이 발생할 때마다 캐시메모리와 메인메모리에 쓰기 동작이 발생하기 때문에 **시간이 길어집니다**.

### 나중쓰기 방식
> CPU의 연산결과를 캐시메모리에 저장해두고 메인메모리에는 저장하지 않습니다. 변경된 캐시메모리의 블록에 1비트의 태그로 표시를 해두고, 해당 블록이 삭제되기 전에 메인메모리에 저장하는 방식입니다. 이 방식은 메인메모리와 캐시메모리 간의 데이터가 **불일치** 할 수 있습니다.


 
