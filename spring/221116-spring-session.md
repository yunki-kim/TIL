# 221116 TIL
<br/>

## 리뷰
- 스프링의 정석 ~2-25
<br/>

## 오늘 배운 것
- Session
- 예외처리
- 데이터 변환과 검증 
<br/>

## 배운내용 정리

### 세션 시작 여부
- session = "true" or session = "false"
  |-|세션이 있을 때|세션이 없을 때|
  |:---:|:---:|:---:|
  |**session = "true"**|세션 생성 X|세션 생성|
  |**session = "false"**|세션 생성 X|세션 생성 X|

- 세션이 필요없는 jsp화면에는 `session="false"`로 세션 생성을 방지
- `session="false"`가 기존 세션에는 영향을 주지 않는다.
<br/>

### 예외처리
- `@ExceptionHandler(처리할 예외 클래스)` 예외처리를 위한 메서드에 사용
- jsp파일 내에 `isErrorPage="true"`를 통해 모델에 예외 내용을 전달하지 않아도 화면에 관련 내용을 표시 가능

**`@ControllerAdvice`**
- 전역 예외 처리 클래스 작성 가능
- 패키지 지정 가능
- 예외 처리 메서드가 중복된 경우, 예외가 발생한 컨트롤러 내의 예외 처리 메서드가 우선

**`@ResponseStatus`**
- 예외 처리에 의해 예외가 처리된 경우 응답의 상태코드는 200(정상)을 띄우지만 예외가 발생한 것은 사실이기에 잘못된 표기임
- 응답 메시지의 상태 코드를 변경할 때 사용
- 예외 처리 메서드나 사용자가 정의한 예외 처리 클래스에 사용

**스프링에서의 예외처리**
- 컨트롤러 메서드 내에서 `try-catch`로 처리
- 컨트롤러에 `@ExceptionHandler` 메서드가 처리
- `@ControllerAdvice`클래스의 `@ExceptionHandler`메서드가 처리
- 예외 종류별로 뷰 지정 - `SimpleMappingExceptionResolver`
- 응답 상태 코드별로 뷰 지정 - `<error-page>`

<br/>

### 데이터 변환과 검증

#### 데이터 변환
- 모든 컨트롤러 내에서의 변환 : WebBindingInitializer를 구현 후 등록
- 특정 컨트롤러 내에서의 변환 : 컨트롤러에 `@InitBinder`가 붙은 메서드를 작성

**PropertyEditor**
- 양방향 타입 변환(String -> 타입, 타입 -> String) 
- 특정 타입이나 이름의 필드에 적용 가능

**Converter**
- 단방향 타입 변환(타입A -> 타입B)
- PropertyEditor의 단점을 개선(stateful -> stateless)

**Formatter**
- 양방향 타입 변환(String -> 타입, 타입 -> String)
- 바인딩할 필드에 적용 : `@NumberFormat`, `@DateTimeFormat`

**우선순위**
1. 커스텀 PE
2. ConversionService
3. 디폴트 PE

<br/>

#### 데이터 검증

**Validator**
- 객체를 검증하기 위한 인터페이스
- `@Valid`를 검증할 데이터에 사용하여 자동 검증 가능
- 하나의 Validator로 여러 객체를 검증할 때, 글로벌 Validator로 등록

**Global Validator**
```xml
<servlet-context.xml>

<annotation-driven validator="globalValidator"/>
<beans:bean id="globalValidator" class="com.fastcampus.ch2.GlobalValidator"/>
```
- 글로벌Validator와 로컬Validator를 동시에 적용하기 위해서는 addValidators 사용 (set은 로컬 한개만 사용할 때)

