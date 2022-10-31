# 221031 TIL
<br/>

## 오늘 배운 내용
- 원격 프로그램 실행
- HTTP Request & Response
<br/>

## 배운 내용 정리

### 원격 프로그램 실행
1. 프로그램 등록 (@Controller)
2. URL과 프로그램을 연결 (@RequestMapping("/"))
> 인스턴스 메서드인데 어떻게 호출되는 것일까?
> - 톰캣 내부에서 호출 시 객체를 생성해주기 때문에 인스턴스 메서드가 호출 가능
> - 접근제어자가 private 이여도 객체를 생성해준다
> **Reflection API**를 이용하여 가능하게해줌❗️
<br/>

### HTTP Request & Response

**Request (요청)**
- HttpServletRequest를 통해 요청받은 URL정보를 request 객체에 담아 매개변수로 받을 수 있다
- QueryString : 값을 전달할 때 사용

**Response (응답)**
- HttpServletResponse를 통해 브라우저에 값을 출력할 수 있다.
