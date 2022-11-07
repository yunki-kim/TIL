# 221106 TIL
프로젝트를 진행하려는데 아직 spring에 대한 이해도 부족으로 오히려 그냥 붙잡고 하려다가 시간이 더갈것같아서<br/>
어제, 오늘 프로젝트에 필요한 부분을 학습하는 시간을 가졌다.<br/>
<br/>

## 오늘 배운 것
- @GetMapping, @PostMapping, @RequestMapping
- redirect, forward
- cookie
<br/>

## 문제풀이
- Login Controller
- Member Entity, DAO, DTO, VO, Service
- Member.sql
<br/>

## 배운 내용 정리

### @GetMapping
- @RequestMapping(value = "/", method = RequestMethod.GET) -> @GetMapping("/")

### @PostMapping
- @RequestMapping(value = "/", method = RequestMethod.POST) -> @PostMapping("/")

### @RequestMapping
- 맵핑될 URL의 공통 부분을 @RequestMapping으로 클래스에 적용❗️

**URL 패턴**
1. exact mapping (정확히 일치)
2. path mapping (경로 맵핑)
3. extension mapping (확장자 맵핑)
- `**`은 하위 경로 포함
<br/>

### redirect
- Web container에 redirect 명령이 들어오면 웹 브라우저는 다른 페이지로 이동
- URL이 해당 주소로 변경
- 새로운 요청이 발생하므로 request, response 객체가 새롭게 생성!
- 시스템에 변화가 생기는 요청은 redirect로 하는것이 바람직

### forward
- Web container 차원에서의 페이지 이동으로 클라이언트는 다른 페이지로 이동했는지 알 수 없다
- 현재 실행중인 페이지와 forward에 의해 호출될 페이지는 request, response 객체를 공유한다.
- 사용자의 요청을 그대로 전달!
- 시스템에 변화가 생기지 않는 단순조회의 경우 forward로 하는것이 바람직
<br/>

### Cookie
- 이름과 값의 쌍으로 구성된 작은 정보
- 서버에서 생성 후 전송, 브라우저에 저장(클라이언트를 식별할 수 있다)
- 유효기간 이후 자동 삭제
- 서버에 요청시 domain, path가 일치(하위경로 포함)하는 경우에만 자동 전송
```java
Cookie cookie = new Cookie("name", "value"); // 쿠키 생성
cookie.setMaxAge(); // 유효시간 설정(단위: sec), setMaxAge(0) - 삭제
response.addCookie(cookie); // 응답에 쿠키 추가
Cookie[] cookies = request.getCookies(); // 쿠키 읽기
```
<br/>

