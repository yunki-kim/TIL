# 221105 TIL
<br/>

## 오늘 배운 것
- Servlet & JSP
- @RequestParam & @ModelAttribute
<br/>

## 배운 내용 정리

### Servlet
- @WebServlet = @Controller + @RequestMapping
- Servlet은 항상 HttpServlet을 상속받아야함
- service 메서드 고정 (HttpServletRequest, HttpServletResponse 포함)
- 클래스에 매핑을 하기 때문에 또다른 매핑을 해야할 경우 클래스를 생성해야함
- 기본적으로 싱글톤으로 구성
```java
@WebServlet("/hello")
public class HelloServlet extends HttpServlet {
    @Override
    public void init() throws ServletException {
        // 서블릿이 초기화될때 자동 호출되는 메서드
        // 1. 서블릿의 초기화 작업 담당
        System.out.println("[HelloServlet] init() is called.");
    }

    @Override
    public void service(ServletRequest req, ServletResponse res) throws ServletException, IOException {
        // 1. 입력
        // 2. 처리
        // 3. 출력
        System.out.println("[HelloServlet] service() is called.");
    }

    @Override
    public void destroy() {
        // 3. 뒷정리 - 서블릿이 메모리에서 제거될 때 서블릿 컨테이너에 의해서 자동 호출.
        System.out.println("[HelloServlet] destroy() is called.");
    }
}
```
<br/>

### JSP
- Java in HTML
- JSP가 작성되면 Servlet으로 변환됨 (첫번째 호출, 변경시)
> <%! -- %> 클래스 영역
> <% -- %> 메서드 영역
<br/>

### Servlet & JSP
- Servlet : lazy-init
- Spring : early-init

**유효범위와 속성**
|기본객체|유효 범위|설명|
|:---:|:---:|:---|
|pageContext|1개의 JSP페이지|JSP페이지의 시작부터 끝까지, 해당 JSP내부에서만 접근 가능, EL을 사용하기위해 쓰임|
|request|1+개의 JSP페이지|요청의 시작부터 응답까지, forward를 통해 다른 JSP로 전달 가능, 요청마다 1개|
|session|n개의 JSP페이지|session의 시작부터 종료까지, 클라이언트마다 1개, 편리하지만 서버 부담이 크다|
|application|context 전체|Web Application의 시작부터 종료까지, context 내부 어디서나 접근 가능, 모든 클라이언트가 공유|

- setAttribute() : 지정된 값을 지정된 속성 이름으로 저장
- getAttribute() : 지정된 이름으로 저장된 속성의 값을 반환

**EL (Expression Language)**
- <%= 값 %> => ${값}
- 지역변수 사용 불가
- 간단하고 편리하게 사용가능
- null을 출력하지 않는다
- 문자열 + 숫자 = 숫자

**JSTL(JSP Standard Tag Library)**
- <% ~ %> => tag
- 블록태그의 불편함을 해소하기위해 사용

**Filter**
- 공통적인 요청 전처리와 응답 후처리에 사용
- 로깅, 인코딩 등
<br/>

### @RequestParam
- 요청의 파라미터를 연결할 매개변수에 붙이는 애노테이션
- 기본형, String 매개변수에 사용
- 생략가능
- name="" (파라미터 이름, 생략가능)
- required= (필수입력 여부, 기본값 true, 생략가능)
- defaultValue= (필수입력 X 일 때 기본값 지정)

### @ModelAttribute
- 적용 대상을 Model의 속성으로 자동 추가해주는 애노테이션
- 참조형 매개변수에 사용
- 반환타입 또는 컨트롤러 메서드의 매개변수에 적용가능
- 반환타입에 적용 시 호출 결과를 model에 저장하여 해당 메서드의 호출도 할 필요가 없다.
- 생략가능

**WebDataBinder**
- 요청 매개변수를 객체에 바인딩 될 때 중간역할을 함
- 타입변환과 데이터 검증을 실시한 후 결과&에러 등을 BindingResult에 저장한다.
