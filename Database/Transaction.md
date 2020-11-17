# Transaction(트랜잭션)

## 트랜잭션이란
> 하나의 작업을 처리하기 위한 연산의 집합
- COMMIT(성공) : 완료 및 저장 SQL 명령 
- ROLLBACK(실패) : 원상복귀 

## 트랜잭션의 ACID 성질 ★★★ 
- 원자성(Atomicity) : 완전히 수행되거나 전혀 수행되지 않거나 (All or Nothing) (※ 로그 파일로 원자성 보장)
- 일관성(Consistency) : 트랜잭션의 실행은 D/B의 일관성을 유지 
- 독립성(Isolation, 격리성, 고립성) : 다른 트랜잭션에 방해 받으면 X
- 영속성(Durability) : 트랜잭션 실행 성공 –> 그 결과는 어떠한 경우에도 영속

## 트랜잭션의 회복
> 트랜잭션 실행 중 데이터베이스가 손상된 경우 손상 이전의 정상 상태로 복구하는 작업

### 회복 기법의 종류
- [자세한내용](https://youn16.github.io/cs/database/2020/11/14/DB_%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%ED%9A%8C%EB%B3%B5/#more)
- 즉시 갱신(Immediate Update)
  - 트랜잭션 연산 중 데이터의 변경 결과를 데이터베이스에 즉시 반영
  - 회복 시 undo 연산, redo 연산
- 지연 갱신(Deferred Modification)
  - 트랜잭션 실행 중 변경 내용을 로그에 보관
  - 부분 완료 시점에 저장된 로그를 사용해 변경 결과를 데이터베이스에 반영 
  - 회복 시 redo 연산 사용 (undo 연산 사용하지 않음 ★)
- 검사시점(Check Point)
- 그림자 페이지(Shadow Paging)