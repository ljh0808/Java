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

---
## **HashSet 클래스**

- 배열과 연결 노드를 결합한 자료구조 형태
- 가장 빠른 임의 검색 접근 속도를 가진다
- 추가,삭제,검색,접근성이 모두 뛰어남
- 순서를 예측할 수 없음

```java
Set<Integer> hashSet = new HashSet<>();

hashSet.add(10);
hashSet.add(20);
hashSet.add(30);
hashSet.add(10);  // 중복된 요소 추가 X

hashSet.size(); // 3

hashSet.toString(); // [20 , 10 , 30]  자료순서 예측 X
```

---
## **LinkedHashSet 클래스**
- 순서를 가지는 Set 자료
- 추가된 순서 또는 가장 최근에 접근한 순서대로 접근 가능
- 중복을 제거하는 동시에 저장한 순서를 유지하고 싶다면, HashSet 대신 LinkedHashSEt을 사용하면 된다.

---
## **TreeSet 클래스**
- 이진 검색 트리(binary search tree) 자료구조의 형태로 데이터를 저장
- 중복을 허용하지 않고, 순서를 가지지 않음
- 데이터를 정렬 하여 저장하고 있다는 것이 특징
- 정렬,검색,범위 검색에 높은 성능을 보임

``` java

Set<Integer> treeSet = new TreeSet<>();

treeSet.add(7);
treeSet.add(4);
treeSet.add(9);
treeSet.add(1);
treeSet.add(5);

treesSet.toString(); // [1,4,5,7,9] - 자료가 알아서 정렬
```

---
## **EnumSet 추상클래스**
- Enum 클래스와 함께 동작하는 Set 컬렉션
- 중복 되지 않은 상수 그룹을 나타내는데 사용
- 산술 비트 연산을 사용하여 구현되므로 HashSet보다 훨씬 빠르며 적은메모리를 사용함
- 단, enum 타입의 요소값만 저장할 수 있고, 모든 요소들은 동일한 enum 객체에 소속되어야 함
- EnumSet은 추상클래스 이고, 이를 상속한 RegularEnumSet 혹은 JumboEnumSet 객체를 사용하게 된다

---
## **Map 인터페이스**
- 키(Key)와 값(value)의 쌍으로 연관지어 이루어진 데이터의 집합
- 값은 중복가능 , 키는 중복X
- 기존에 저장된 데이터와 중복된 키와 값을 저장하면 기존의 값은 없어지고 마지막에 저장된 값이 남게됨
- 저장 순서가 유지되지 않음

---
## **Map.Entry인터페이스**
- Map 인터페이스 안에 있는 내부 인터페이스
- Key - value 쌍의 Node 내부 클래스가 이를 구현하고 있음
- Map 자료구조를 보다 객체지향적인 설계를 하도록 유도하기 위한 것
```java
Map<String, Integer> map = new HashMap<>();
map.put("a", 1);
map.put("b", 2);
map.put("c", 3);

// Map.Entry 인터페이스를 구현하고 있는 Key-Value 쌍을 가지고 있는 HashMap의 Node 객체들의 Set 집합을 반환
Set<Map.Entry<String, Integer>> entry = map.entrySet();

System.out.println(entry); // [1=a, 2=b, 3=c]

// Set을 순회하면서 Map.Entry를 구현한 Node 객체에서 key와 value를 얻어 출력
for (Map.Entry<String, Integer> e : entry) {
    System.out.printf("{ %s : %d }\n", e.getKey(), e.getValue());
}

```

```출력결과
{ a:1 }
{ b:2 }
{ c:3 }
```
---
## **HashMap 클래스**
- Hashtable을 보완한 컬렉션
- 배열과 연결이 결합된 Hashing형태로, 키와 값을 묶어 하나의 데이터로 저장
- 중복을 허용하지 않고, 순서를 보장하지 않음
- 키와 값으로 null이 허용
- 추가,삭제,검색,접근성이 모두 뛰어남
- 비동기로 작동하기 때문에 멀티 쓰레드 환경에서는 어울리지 않음

```java
Map<String, String> hashMap = new HashMap<>();

hashMap.put("love", "사랑");
hashMap.put("apple", "사과");
hashMap.put("baby", "아기");

hashMap.get("apple"); // "사과"

// hashmap의 key값들을 set 집합으로 반환하고 순회
for(String key : hashMap.keySet()) {
    System.out.println(key + " => " + hashMap.get(key));
}
/*
love => 사랑
apple => 사과
baby => 아기
*/
```

---
## **LinkedHashMap 클래스**
- HashMap을 상속하기 때문에 흡사하지만, Entry들이 연결 리스트를 구성하여 데이터의 순서를 보장
- 들어온 순서대로 순서를 가진다

---
## 정리
**ArrayList** 

- 리스트 자료구조를 사용한다면 기본 선택
- 임의의 요소에 대한 접근성이 뛰어남
- 순차적인 추가/삭제 제일 빠름
- 요소의 추가/삭제 불리


**LinkedList**

- 요소의 추가/삭제 유리
- 임의의 요소에 대한 접근성이 좋지 않음


**HashMap / HashSet**

- 해싱을 이용해 임의의 요소에 대한 추가/삭제/검색/접근성 모두 뛰어남
- 검색에 최고성능 ( get 메서드의 성능이 O(1) )


**TreeMap / TreeSet**

- 요소 정렬이 필요할때 검색(특히 범위검색)에 적합
- 그래도 검색 성능은 HashMap보다 떨어짐


**LinkedHashMap / LinkedHashSet**
- HashMap과 HashSet에 저장 순서 유지 기능을 추가 <br/>

 **Queue : 스택(LIFO) / 큐(FIFO)** 
- 자료구조가 필요하면 ArrayDeque 사용
- Stack, Hashtable : 가급적 사용 X (deprecated)
