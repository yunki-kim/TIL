# 221017 TIL
<br/>

## 오늘 배운 것
- 컬렉션 프레임워크
<br/>

## 배운 내용 정리

### 컬렉션 프레임워크
- 프로그램 구현에 필요한 자료구조를 구현해놓은 JDK 라이브러리
- java.util 패키지에 구현되어 있음
<img src="//gitlab.com/easyspubjava/javacoursework/-/raw/master/Chapter5/5-09/img/colle">
<br/>

#### Collection 인터페이스
- **하나**의 객체를 관리하기 위한 메서드가 선언된 인터페이스
- 하위에 List와 Set 인터페이스가 있음

**List 인터페이스**
- 객체를 순서에 따라 저장하고 관리하는데 필요한 메서드가 선언된 인터페이스
- 중복을 허용함
- **ArrayList**, Vector, LinkedList, Stack, Queue 등..

**Set 인터페이스**
- 순서와 관계없이 중복을 허용하지 않고 유일한 값을 관리하는데 필요한 메서드가 선언된 인터페이스
- 저장된 순서와 출력된 순서는 다를 수 있다.
- **HashSet**, TreeSet 등..

#### Map 인터페이스
- **쌍**으로 이루어진 객체를 관리하는데 사용하는 메서드가 선언된 인터페이스
- 객체는 key - value의 쌍으로 이루어짐
- key는 중복을 허용하지 않음
- HashTable, **HashMap**, Properties, TreeMap 등..

#### Iterator
- 컬렉션 프레임워크에 저장된 요소들을 하나씩 차례대로 참조하는 것
- Set 인터페이스의 경우 `get(i)` 메서드가 제공되지 않으므로 Iterator를 활용하여 객체를 순회
> boolean hasNext() : 이후에 요소가 더 있는지를 체크, 있는 경우 true를 반환 <br/>
> E next() : 다음에 있는 요소를 반환
<br/>

#### Comparable, Comparator

**TreeSet 클래스**
- 내부적으로 이진 검색 트리로 구현됨
- 저장하기 위해 각 객체를 비교해야 함
- 비교 대상이 되는 객체에 Comparable이나 Comparator 인터페이스를 구현해야 TreeSet에 추가

**Comparator 활용**
- 이미 Comparable이 구현된 경우 Comparator을 이용해 비교하는 방식을 다시 구현 가능
```java
class MyCompare implements Comparator<String>{

	@Override
	public int compare(String s1, String s2) {
		return (s1.compareTo(s2)) *-1 ;
	}
}

public class ComparatorTest {

	public static void main(String[] args) {

		Set<String> set = new TreeSet<String>(new MyCompare());
		set.add("aaa");
		set.add("ccc");
		set.add("bbb");

		System.out.println(set);
	}
}
```

