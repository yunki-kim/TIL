# 221117 TIL
<br/>

## 오늘 배운 것
- DI
<br/>

## 배운 내용 정리

### DI
- Bean : Spring Container가 관리하는 객체
- Spring Container : Bean 저장소, Bean을 저장, 관리(생성, 소멸, 연결)
  - BeanFactory - Bean을 생성, 연결 등의 기본 기능을 정의
  - ApplicationContext - BeanFactory를 확장해서 여러 기능을 추가 정의
- ApplicationContext : Root AC, Servlet AC가 있고 Root AC 생성 -> DispathcerServlet 생성 -> Servlet AC 생성
  - Root AC는 Servlet AC의 부모

**IoC와 DI**
- 제어의 역전
- 제어의 흐름을 전통적인 방식과 다르게 뒤바꾸는 것
  - 전통적인 방식 : 사용자 코드가 Framework 코드를 호출
  - IoC : Framework 코드가 사용자 코드를 호출
  - 자주 변하지 않는 코드와 자주 변하는 코드의 분리!
  - 이때, 사용할 객체를 외부에서 주입받는 것을 **의존성 주입 DI**라고 한다❗️

**Autowired**
- 인스턴스 변수, setter, 참조형 매개변수를 가진 생성자, 메서드에 적용
- 생성자의 `@Autowired`는 생략 가능(단, 생성자가 한개일 때)
- 가능하면 생성자에서 주입하는 것이 좋다.
- 스프링 컨테이너에서 타입으로 빈을 검색해서 참조 변수에 자동 주입
  - 검색된 빈이 n개이면, 그 중에 참조변수와 이름이 일치하는 것을 주입
  - 주입 대상이 변수일 때, 검색된 빈이 **1개** 아니면 예외 발생
  - 주입 대상이 배열일 때, 검색된 빈이 **n개** OK!
  - `@Autowired(required=false)`일 때, 주입할 빈을 못찾아도 예외 발생 X
  - `@Qualifier("")`을 통해 같은 타입의 빈이 여러개일 때 이름으로 지정해서 주입 가능

**Resource**
- 스프링 애너테이션 X
- 스프링 컨테이너에서 이름으로 빈을 검색해서 참조 변수에 자동 주입
  - 일치하는 이름의 빈이 없으면 예외 발생
  - 이름 생략가능(참조변수의 이름이 빈의 이름으로 설정됨)

**Component**
- `<component-scan>`으로 `@Component`가 붙은 클래스를 자동 검색해서 빈으로 등록
- `@component("id")` id는 생략가능 클래스의 이름(CamelCase 적용)을 id로 등록
- `@Controller`, `@Service`, `@Repository`, `@ControllerAdvice`의 메타 애너테이션

**빈의 초기화**
- `<property>`를 이용한 초기화 (setter가 필요)
- `<constructor-arg>`를 이용한 초기화 (생성자 필요)

