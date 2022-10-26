# 221026 TIL
<br/>

## 오늘 배운 것
- Logger
- Chapter7 객체지향프로그래밍II ~273p
<br/>

## 문제풀이
- Toy Project 1 Refactoring
<br/>

## 배운 내용 정리

### Logger

**logging**
- 시스템 운영에 대한 기록
- 오류가 발생했을 때 그 오류에 대한 기록을 남겨 디버깅을 용이하게 함

> 어느정도의 로그를 남길 것인가??
> - 적은 로그: 정황상 시스템의 상황을 파악하기 어려움
> - 많은 로그: 빈번한 file I/O의 오버헤드, 로그파일의 백업 문제 등

**java.util.logging**
- 자바에서 기본적으로 제공되는 log package
- 잘 사용하지 않고 오픈소스로 log4j를 많이 사용하고 있음
