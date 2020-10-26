# 정보위협의 종류

## 1. **스니핑(Sniffing)**
> 도청, 킁킁거리는 것 

## 2. 피싱(Phishing)
> 개인정보와 낚시 합성어

> 사칭 메일로 개인정보를 낚는 행위

## 3. ARP Redirect
> 라우터의 MAC 주소를 알아내어, 공격대상에게 자신의 MAC주소가 라우터인 것 처럼 속인 후, 브로드캐스트를 주기적으로 하여 패킷을 **스니핑**(도청)하는 공격방법

- ARP Spoofing과의 차이점
    
    해당 네트워크 전체를 대상으로 MAC 주소를 속여 LAN에서의 통신 흐름을 왜곡

## 4. 스푸핑(Spoofing)
> 속이는 것(= 정상 사용자로 위장)

1. TCP/IP의 약점을 이용
- IP주소를 바꾸어 접속 시도
2. 승인받은 사용자인 것처럼 시스템에 접근
3. 네트워크상에서 허가된 주소로 가장하여 접근
4. 특정 호스트로부터 접근하려는 것처럼 속이는 해킹 기법

### 1. ARP Spoofing
> 특정 호스트를 대상으로 MAC 주소를 속여 LAN에서의 통신 흐름을 왜곡시키는 공격

- ARP Redirect와 큰 차이는 없지만, 도청만 하는 것이 아니라 거짓 패킷을 보낸다는 특징을 가지고 있다. 따라서 호스트 대 호스트 공격이 가능하다.

### 2. DNS Spoofing(파밍(Pharming)) 

### 3. IP Spoofing

### 4. E-mail Spoofing


## 5. 서비스 거부 공격DoS(Denial of Service)

### 1. Ping of Death Attack 
- ICMP 패킷을 크게 많이

### 2. Land Attack
- 출발지와 목적지가 같은 패킷

### 3. Smurf Attack
- 여러 PC에 패킷을 브로드캐스팅, 다시 전송할 수신지로 희생자 주소 기입

### 4. Tear drop Attack
- TCP/IP 재조립 코드에 버그를 이용

### 5. TCP SYN Flooding Attack 
- 다량의 SYN 패킷을 보냄