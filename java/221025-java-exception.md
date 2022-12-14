# 221025 TIL
<br/>

## 오늘 배운 것
- 예외처리
- Chapter7 객체지향프로그래밍II ~264p
<br/>

## 배운 내용 정리

### 예외처리
컴파일 오류
- 프로그램 코드 작성 중 발생하는 문법적 오류

실행 오류
- 실행 중인 프로그램이 의도하지 않은 동작을 하거나 프로그램이 중지되는 오류
- 비정상 종료가 되는 경우 시스템의 심각한 장애를 발생할 수 있음

**예외처리 중요성**
- 프로그램의 비정상 종료를 피하여 시스템이 원활히 실행되도록 함
- 실행오류가 발생한 경우 오류의 과정을 재현하는 것은 현실적으로 힘듬
- 오류가 발생한 경우 Log를 남겨서 추후 분석을 통해 그 원인을 파악하여 수정하는 것이 중요!

**에러**
- 시스템 오류
- 가상 머신에서 발생, 프로그래머가 처리할 수 없는 오류
- 동적 메모리가 없는 경우, 스택 메모리 오버플로우 등

**예외**
- 프로그램에서 제어 할 수 있는 오류
- 자바는 안정성이 중요한 언어로 대부분 프로그램에서 발생하는 오류에 대해 문법적으로 예외 처리를 해야한다!

**Exception**
- 모든 예외 클래스의 최상의 클래스는 Exception 클래스

**try-catch**
```java
try {
    // 예외가 발생할 수 있는 코드 부분
} catch (처리할 예외 타입 e) {
    // try 블록 안에서 예외 발생 시 예외를 처리하는 부분
}
```

**try-catch-finally**
- try{} 블럭이 수행되는 경우, finally{} 블럭은 항상 수행 됨
- finally 블럭에서 파일을 닫거나 네트웍을 닫는 등의 리소스 해제 구현을 함

**try-with-resources**
- 리소스를 사용하는 경우 자동으로 close() 되도록 함
- JDK 7+
- 해당 리소스 클래스가 AutoCloseable 인터페이스를 구현해야 
- JDK 9부터는 리소스는 try() 외부에서 선언하고 변수만 try(obj)와 같이 사용할 수 있다

**예외 처리 미루기**
- throws를 이용하면 예외가 발생할 수 있는 부분을 **사용하는 곳**에서 예외를 처리할 수 있다
- 여러개의 예외가 발생하는 경우 예외를 묶어서 하나의 방법으로 처리 가능
```java
try {

} catch (FileNotFoundException | CastNotFoundException e) {
    e.printStackTrace();
}
```
- Exception 클래스를 활용하여 default 처리를 할 때는 Exception 블록은 맨 마지막에 위치해야 함
 -> Exception 은 예외처리 클래스 중 최상의 클래스로 상단에 배치하면 하단의 예외처리에 도달할 수 없다!

**사용자 정의 예외 클래스**
- 자바에서 제공되는 예외 클래스 외에 프로그래머가 직접 만들어야하는 예외가 있을 수 있다
- 기존 예외 클래스 중 가장 유사한 예외 클래스에서 상속받아 사용자 정의 예외 클래스를 만든다.
- 기본적으로 Exception 클래스를 상속해서 만들 수 있다.


