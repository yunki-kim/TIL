# 221121 TIL
<br/>

## 오늘 배운 것
- AOP
- Service Layer
<br/>

## 배운 내용 정리

### AOP
- 변경에 유리한 코드를 만드는 작업
- 부가기능(advice)을 동적으로 추가해주는 기술
- 메서드의 **시작 또는 끝**에 자동으로 코드(advice)를 추가

**AOP 관련 용어**
- target : advice가 **추가될 객체** (메서드는 join point, 이를 정의한 패턴을 pointcut)
- advice : target에 동적으로 **추가될 부가 기능(코드)**
- proxy : target에 advice가 동적으로 **추가되어 생성된 객체** (이 과정을 weaving 이라함)

**Advice**
|종류|애너테이션|설명|
|:---|:---|:---|
|around advice|@Around|메서드의 **시작과 끝** 부분에 추가되는 부가 기능|
|before advice|@Before|메서드의 **시작** 부분에 추가되는 부가 기능|
|after advice|@After|메서드의 **끝** 부분에 추가되는 부가 기능|
|after returning|@AfterReturning|예외가 **발생하지 않았을 때**, 실행되는 부가 기능|
|after throwing|@AfterThrowing|예외가 **발생했을 때**, 실행되는 부가 기능|
- returning은 try블럭, throwing은 catch블럭이라 생각하면 쉽다 😁

<br/>

### Service Layer
- 서비스 계층의 분리 : 비즈니스 로직의 분리
- 트랜젝션의 관리

**TransactionManager**
- DAO의 각 메서드는 개별 connection을 사용 -> 1개의 connection에서 수행하게끔❗️
- 같은 Tx내에서 같은 Connection을 사용할 수 있게 관리

**`@Transactional`**
- AOP를 이용한 핵심 기능과 부가 기능의 분리
- 클래스나 인터페이스에도 붙일 수 있음(해당 영역 내의 모든 메서드에 적용)

**`@Transactional`의 속성**
- readOnly : Tx이 데이터를 **읽기만** 하는 경우, true로 지정하면 성능 향상
- rollbackFor : 지정된 예외가 발생하면, tx을 rollback (RuntimeException과 Error은 자동 rollback)
- propagation : Tx의 경계를 설정하는 방법을 지정
> REQUIRED : (Default) Tx이 진행중이면 참여, 없으면 새로운 Tx 시작
> REQUIRES_NEW : Tx이 진행 중이건 아니건, 새로 Tx 시작 (다른 Tx)
> NESTED : Tx이 진행 중이면, Tx의 내부 Tx로 실행 (같은 Tx)

