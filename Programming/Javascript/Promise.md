# Promise

- Callbackhell과 같은 지저분한 JavaScript코드의 해결책
- 내용이 실행은 되었지만 결과를 아직 반환하지 않은 객체
- 비동기연산이 종료된 이후, 결과값이나 실패의 이유를 처리하기 위한 처리함수를연 결

- 다음 중 하나의 상태를 가짐

> 대기(pending) / 이행(fulfilled) / 거부(rejected)