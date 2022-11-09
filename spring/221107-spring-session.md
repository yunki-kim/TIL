# 221107 TIL
<br/>

## 오늘 배운 것
- session
<br/>

## 문제풀이
- Login Test 관련 코드 추가
<br/>

## 배운 내용 정리

### Session
- 서로 관련된 요청들을 하나로 묶은 것(쿠키를 이용 - 세션ID를 쿠키에 담아)
- 브라우저마다 개별 저장소(session 객체)를 서버에서 제공, 서버에 저장❗️
- 보안에 유리하지만 서버 다중화에 불리
- 쉽게 Login ~ Logout 까지가 하나의 세션이라 생각하자
```java
HttpSession session = request.getSession // 세션 얻기
session.setAttribute("name", "value") // 세션에 저장
session.getAttribute("name", "value") // 세션에서 불러오기
session.invalidate() // 세션 종료
session.setMaxInactiveInterval() // 세션 유효기간 설정 (단위 : 초)
```
