# 221125 TIL
어제오늘 살짝 몸살기운이 도는듯하다 🥲 <br>
공부에도 체력관리가 중요한데 원하는대로 되지많은 않네...
<br>

## 오늘 배운 것
- REST API
- 기능 구현 순서
<br>

## 배운 내용 정리

**JSON**
- **J**ava **S**cript **O**bject **N**otation : 자바스크립트 객체 표기법
- 기존의 xml을 통한 복잡한 데이터 교환을 JSON으로 간단하게❗️
- `{속성명1:속성값1, 속성명2:속성값2, ...}`
- JSON으로 객체를 주고받을 때는 받을 때는 `@RequestBody` 줄 때는 `@ResponseBody` 사용
> JS객체를 서버로 전송하려면, 직렬화(문자열로 변환)가 필요 <br>
> 서버가 보낸 데이터(JSON문자열)를 JS객체로 변환할 때, 역질렬화가 필요 <br>
> `JSON.stringify()` : 객체를 JSON 문자열로 변환(직렬화, JS객체 -> 문자열) <br>
> `JSON.parse()` : JSON 문자열을 객체로 변환(역직렬화, 문자열 -> JS객체) <br>

**Ajax**
- **A**synchronous **j**avascript **a**nd **X**ML
- 비동기 통신으로 데이터를 주고 받기 위한 기술
- 웹페이지 전체(data + ui)가 아닌 일부(data)만 업데이트 가능
> 동기 vs 비동기 <br>
> 동기 : 요청 후 응답을 기다리는 동안 작업 불가 <br>
> 비동기 : 요청 후 추가적인 작업이 가능 대신 언제 처리가 끝났는지 알수가 없음(이에 콜백함수를 사용) <br>
<br>

### REST API
- **Re**presentational **S**tate **T**ransfer **API** : REST 규약을 준수하는 API

**`@RestController`**
- `@ResponseBody` 대신, 클래스에 `@RestController` 사용 가능 (`@Controller` + `@ResponseBody`)
> REST란? <br>
> 프로토콜에 독립적이며, 주로 HTTP를 사용해서 구현 <br>
> 리소스 중심의 API 디자인 - HTTP 메서드로 수행할 작업을 정의 <br>

**RESTful AIP 설계**
- URI에는 명사, 메서드는 동사의 역할❗️❗️
<br>

### 기능 구현 순서
1. DB테이블 생성
2. Mapper XML 작성
3. DAO 작성 & 테스트
4. Service 작성 & 테스트
5. 컨트롤러 작성 & 테스트
6. 뷰(UI)작성 & 테스트 - FE

**ResponseEntity**
- 개발자가 직접 결과 데이터와 HTTP 상태 코드를 직접 제어할 수 있는 클래스
- 에러로 인해 요청이 제대로 되지않아도 상태코드가 정상적인 200코드가 나오는것을 변경하기 위해 사용
```java
try {
    list = commentService.getList(bno);
    return new ResponseEntity<List<CommentDto>>(list, HttpStatus.OK); // 200
} catch (Exception e) {
    return new ResponseEntity<List<CommentDto>>(HttpStatus.BAD_REQUEST); // 400
}
```

**`@PathVariable`**
- `@RequestMapping` 값으로 `{}` 같은 템플릿 변수를 사용한 경우 `@PathVariable`을 이용해서 템플릿 변수와 동일한 이름을 갖는 파라미터를 추가❗️

