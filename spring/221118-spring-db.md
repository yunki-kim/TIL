# 221118 TIL
<br/>

## 오늘 배운 것
- DB Connection
- DAO
- Transaction
<br/>

## 배운 내용 정리

### DAO(Data Access Object)
- 데이터에 접근하기 위한 객체
- DB에 저장된 데이터를 읽기, 쓰기, 삭제, 변경(CRUD)을 수행
- DB테이블당 하나의 DAO를 작성
- Controller단에서 DB에 직접 접근하면 Controller의 기능에 따라 중복되는 코드가 발생 
  - 계층의 분리❗️
  - Controller = Presentation Layer (데이터를 보여주는 계층)
  - Dao = Persistance Layer(Data Access Layer)

### Transaction
- 더 이상 나눌 수 없는 작업의 단위

**Transaction 속성**
- 원자성(Atomicity) : 나눌 수 없는 하나의 작업으로 다뤄져야 한다.
- 일관성(Consistency) : 트랜젝션 수행 전과 후가 일관된 상태를 유지해야 한다.
- 고립성(Isolation) : 각 트랜젝션은 독립적으로 수행되어야 한다.
- 영속성(Durability) : 성공한 트랜젝션의 결과는 유지되어야 한다.

**Commit, Rollback**
- 커밋 : 작업 내용을 DB에 영구적으로 **저장**
- 롤백 : **최근** 변경사항을 취소(마지막 커밋으로 복귀)
> 자동커밋, 수동커밋
> - 자동 커밋 : (Default) 명령 실행 후, 자동으로 커밋이 수행(rollback 불가❗️)
> - 수동 커밋 : 명령 실행 후, 명시적으로 commit 또는 rollback을 입력

**Isolation level**
1. READ UNCOMMIT : 커밋되지 않은 데이터도 읽기 가능(dirty read)
2. READ COMMITED : 커밋된 데이터만 읽기 가능(phantom read)
3. REOEATABLE READ : (Default) 트랜젝션이 시작된 이후 변경은 무시됨
4. SERIALIZABLE : 한 번에 하나의 트랜젝션만 독립적으로 수행 (고립도 최상)
- 적절한 조절이 필요❗️

