# 221007 TIL
토이 프로젝트가 주어졌다. 처음해봐서 토이의 느낌이 안들지만 주어졌으니 해야지.. <br/>
토이 프로젝트 주제는 스마트스토어의 운영진을 위한 고객 분류 프로그램을 만드는 것이다. <br/>
내부적으로 복잡한 로직은 없어보이는데 클래스를 각각 어떻게 연결할지에 대한 것이 감이 안잡혀서
어렵게 느껴진다😅 <br/>
생각하다가 자꾸 궁금한게 생겨서 그거 찾아보다가 시간이 가는거같다.
<br/>

## 찾아본 내용
1. 어제 궁금했던 유효성 검사의 위치에 대해 알아보았다. <br/> 
보통 생성자를 통해 생성을 할 때에는 이미 DB와 연동이 되어있거나해서 생성자에서 유효성 검사를 
하기보다는 setter를 통해 해당 값을 직접 변경하는 행동이 있을 때 유효성 검사를 진행한다고 한다. <br/> 
만약 사용자가 생성자에서 올바르지 않은 값을 입력할까봐 불안할 때는 그런 문제가 있을것 같은 값은
객체 생성 시 입력받기보다는 setter를 통해서만 접근하게 설계하는것이 좋다고 한다.

2. 클래스에서 equals, hashcode를 꼭 선언해야 할까? <br/>
equals는 객체의 주소값을 비교하는 것이 아닌 내부의 값을 비교한다. <br/>
서로 다른 객체이더라도 모든 내용이 같으면 별개의 객체라고 보기 어렵기 때문에 equals를 통해 이를 잡아준다.<br/>
hashcode는 hash값을 이용하여 빠른 속도를 자랑하고ㅎ
 -> [링크](https://tjdtls690.github.io/studycontents/java/2022-07-27-equals_hashcode/) <br/>
아무튼 궁금했던 점은 만약 객체 생성마다 고유번호를 추가하게되면 어차피 그걸로 구분이 될텐데 equals와 hashcode를
굳이 오버라이딩 할 필요가 있을까였는데 명확하게 구분할 수 있거나 구분할 필요가 없으면 무조건 적으로 오버라이딩
할 이유는 없다고한다. <br/>
하지만 사용자가 어떻게 사용할지에 대한 예측이 힘들기 때문에 명확한 이유가 있는것이 아니면 사용해서 나쁠건 없다!
라고 결론을 내렸다.
