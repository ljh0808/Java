# Collection Framework
### 컬렉션 프레임워크란?
- **컬렉션**은 다수의 데이터, **프레임워크**는 표준화된 프로그래밍 방식을 의미
- **컬렉션 프레임워크**란 데이터 그룹을 저장하는 클래스들을 표준화한 설계

### 컬렉션 프레임워크 장점
- 인터페이스와 다형성을 이용한 객체지향적 설계를 통해 표준화되어 있기 때문에, 사용법을 익히기에도 편리하고 재사용성이 높음

- 데이터 구조 및 알고리즘의 고성능 구현을 제공하여 프로그램의 성닝과 품질을 향상시킴

- 관련 없는 API 간의 상호 운용성을 제공함

- 이미 구현되어있는 API를 활용하여, 새로운 API를 익히고 설계하는 시간이 줄어듦

- 컬렉션 프레임워크는 크게 **Collection 인터페이스** 와 **Map 인터페이스** 로 나뉨

- Map 인터페이스 컬렉션들은 두개의 데이터를 묶어 한쌍으로 다루기 때문에 
Collection 인터페이스와 분리되어 있음 

>컬렉션 프레임워크에 저장할 수 있는 데이터는 오직 객체(Object) 뿐이다.
즉, int형이나 double형 같은 primitive 타입은 적재를 하지못하므로, wrapper 타입으로 변환하여 Integer 객체나 Double 객체로 박싱하여 저장하여야 함


---

### Iterable 인터페이스

- 컬렉션 인터페이스들의 가장 최상위 인터페이스

- 자료들을 순회할때 이터레이터 객체를 사용하는데, 이 객체를 관리하는 터페이스

>참고:  Map은 iterable 인터페이스를 상속받지 않기 때문에 iterator()와 spliterator()는 Map에서 사용할수 없음

---

### Collection 인터페이스

- **List,Set,Queue** 에 상속을하는 실질적인 최상위 컬렉션 타입

- 업캐스팅으로 다양한 종류의 컬렉션 자료형을 받아 자료를 삽입하거나 삭제,탐색 기능을 할 수 있음(다형성)

---

## **List 인터페이스**

- ArrayList,LinkedList,Vector,Stack 으로 구성
- 순서가 있는 저장공간

### 특징
- 저장 순서가 유지되는 컬렉션을 구현하는 데 사용
- 같은 요소의 중복 저장을 허용
- 배열과 마찬가지로 index로 요소에 접근
- 배열과의 가장 큰 차이는 리스트는 **자료형 크기**가 고정이 아닌 데이터 양에 따라 **동적으로 늘어났다 줄어들수 있다**는 점(가변)
- 요소 사이에 빈공간을 허용하지 않아 삽입/삭제 할때마다 배열 이동이 일어남

### 대표적인 메서드

- **add(E e)** : 요소를 추가
- **remove(Object o)** : 지정한 객체와 같은 첫 번째 객체를 삭제
- **contains(Object o)** : 지정한 객체가 컬렉션에 있는지 확인 있을경우 true, 없을경우 false를 반환
- **size()** : 현재 컬렉션에 있는 요소 개수를 반환
- **get(int index)**: 지정된 위치에 지정된 원소를 반환
- **set(int index, E elements)**: 지정된 위치에 있는 요소를 지정된 요소로 변경
- **isEmpty()**: 현재 컬렉션에 요소가 없다면 true, 존재한다면 false를 반환
- **equals(Object o)**: 지정된 객체와 같은지 비교
- **indexOf(Otject o)** " 지정된 객체가 있는 첫 번째 요소의 위치를 반환 , 만일 없을경우 -1을 반환
- **clear()** : 모든 요소들을 제거

---
## **ArrayList 클래스**

- 배열을 이용하여 만든 리스트
- 데이터의 저장순서가 유지되고 중복을 허용
- 데이터량에 따라 공간(capacity)가 자동으로 늘어나거나 줄어들음
- 단방향 포인터 구조로 자료에 대한 순차적인 접근에 강점이 있어 조회가 빠름
- 삽입/삭제가 느리다. 단, 순차적으로 추가/삭제하는 경우에는 가장 빠름
```java
List<String> arrayList = new ArrayList<>();

arrayList.add("Hello");
arrayList.add("World");

arrayList.get(0); // "Hello"
```
---
## **LinkedList 클래스**

- 노드(객체)를 연결하여 리스트 처럼 만든 컬렉션
- 데이터의 중간 삽입,삭제가 빈번할 경우 빠른 성능을 보장
- 임의의 요소에 대한 접근 성능은 좋지 않음
- 자바의 LinkedList는 양방향 포인터구조로 이루어져 있음
- 스택,큐,트리 등의 자료구조의 근간이 된다

```java
List<String> linkedList = new LinkedList<>();
linkedList.add("Hello");

linkedList.get(0); //"Hello"
```
---
## **Vector 클래스**
- ArrayList의 구형 버전
- ArrayList와의 차이는 모든메서드가 동기화 되어있어 Thread-Safe 하다는 점
- 구버전 자바와 호환성을 위해 남겨두었으며, 잘 쓰이진 않음
> 현업에서 컬렉션에 동기화가 필요하면 Collections.synchronizedList() 메서드를 이용해 ArrayList를 동기화 처리하여 사용한다.
```java
List<Integer> vector = new Vector<>();

vector.add(10);
vector.add(20);

vector.get(0); // 10
```
---
## **Stack 클래스**

- 후입선출 LIFO(Last-In-First-Out) 자료구조
- 마지막에 들어온 원소가 처음으로 나간다
- 들어올때는 push, 나갈때는 pop
- Vectort를 상속하기 때문에 문제점이 많아 잘 쓰이지 않음.
```java
Stack<Integer> stack = new Stack<>();

stack.push(30);
stack.push(50);

stack.pop(); // 50
stack.pop(); // 30
```
## **Queue 인터페이스**
- 선입선출 FIFO(First-In-First-Out) 구조
- 처음 들어온 원소가 가장먼저 출력
- 자바에서는 Queue는 인터페이스이고 필요에 따라 큐 컬렉션을 골라 사용

> 추가공부이후 정리예정

---
## **Set 인터페이스**

- 데이터의 중복을 허용하지 않고 순서를 유지하지 않는 데이터의 집합 리스트
- 순서 자체가 없으므로 인덱스로 검색해서 가져오는 `get(index)` 메서드도 존재하지 않음
- 중복 저장이 불가능하며, null 값도 하나만 저장할 수 있음
