## 220920 TIL


### 오늘 배운 것
- Conditional
- Loop

### 배운 내용 정리

#### Conditional
- if - else if - else문
```java
if (조건식1) {
    수행문1; // 조건식1이 참인 경우 수행하고 전체 조건문을 빠져나감
} else if (조건식2) {
    수행문2; // 조건식2이 참인 경우 수행하고 전체 조건문을 빠져나
} else {
    수행문3; // 위 조건이 모두 해당되지 않는 경우 (디폴트)
}
```

- switch - case문
```java
switch (변수) {
    case 값1:
        수행문1;
        break; // 없을 경우 해당 케이스 아래의 모든 케이스 실
    case 값2:
        수행문2;
        break;
    default:
        수행문3; // 위 조건이 모두 해당되지 않는 경우
```

#### Loop
- while문
```java
while (조건식) { // 조건식이 참인 동안 반복 수행
    수행문1;
}
```

- do - while문
```java
do {
    수행문1; // 조건에 상관없이 수행을 한 후 조건을 체크
} while (조건식) {
    수행문2;
}
```

- for문
```java
for (초기화식; 조건식; 증감식) {
    수행문;
}
```

- break문
  - 감싸고 있는 제어문의 블록을 빠져나오는 기능
  - 반복문이 중첩되어 있는 경우엔 break문이 포함되어있는 반복문만 빠져나옴

- continue문
  - 조건문과 같이 사용하며, 조건이 맞는 경우 반복문 블럭 내부의 다른 수행문을 수행하지 않는다.
