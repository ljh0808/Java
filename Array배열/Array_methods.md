# Arrays 클래스
Java의 배열을 다룰 때 유용한 다양한 유틸리티 메서드를 포함한 클래스입니다.  
Arrays 클래스를 사용하려면 `import java.util.Arrays;`를 선언해야 합니다.

---

### 📌 주요 메서드: Arrays.copyOf()
> **설명**: 지정된 배열을 인덱스 0부터 원하는 길이만큼 복사하는 메서드 <br/>
Arrays.copyOf(복사할 배열, 복사할 길이);

#### ✅ Arrays.copyOf의 장점
- **길이 지정 가능**: 원하는 길이로 배열을 복사할 수 있습니다.
- **원본 배열 보호**: 원본 배열에 직접 영향을 미치지 않습니다.
- **간결한 코드**: 한 줄로 배열을 복사하여 유지보수가 쉬워집니다.

#### 📋 사용 예시
```java
// Arrays.copyOf(복사할배열, 복사할길이)
int[] intArr = new int[]{1, 2, 3, 4, 5};
int[] intArrCopy = Arrays.copyOf(intArr, 3);

// 결과 출력
for (int a : intArrCopy) {
    System.out.println(a);
}

```
##### 출력결과 
```
1
2
3
```
---
### 📌 주요 메서드: Arrays.copyOfRange()
> **설명**: 지정된 배열을 원하는 시작 인덱스,종료 인덱스를 지정하여 새로운 배열을 반환함 <br/>
Arrays.copyOfRange(복사할 배열, 시작 인덱스, 종료 인덱스);

#### ✅ Arrays.copyOfRange의 장점
- **길이 지정 가능**: copyOf는 인덱스를 지정할수없지만, Range는 지정가능
- **원본 배열 보호**: 원본 배열에 직접 영향을 미치지 않습니다.
- **간결한 코드**: 한 줄로 배열을 복사하여 유지보수가 쉬워집니다. 

**주의** <br/> **!** 복사를 시작할 인덱스로 복사할 원본 배열의 길이보다 큰 값을 주면 예외가 발생함

```java
int[] intArr = new int[] {1,2,3,4,5};
int[] intArrCopy = Arrays.copyOfRange(intArr,2,4);
for(int i : intArrCopy) System.out.println(i);
```
##### 출력결과
```
3
4
```

**copyOfRange 적용가능한 문제:**
[프로그래머스 링크(K번째수)](https://school.programmers.co.kr/learn/courses/30/lessons/42748)   
**내가 푼 방식:** [Github 링크](https://github.com/ljh0808/Codetest/tree/master/%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%A8%B8%EC%8A%A4/1/42748.%E2%80%85K%EB%B2%88%EC%A7%B8%EC%88%98)   

---

### 📌 주요 메서드: Arrays.sort()
> **설명**: 주어진 배열을 오름차순으로 정렬해주는 메서드 <br/>
Arrays.sort(정렬할 배열);


---

### 📌 주요 메서드: System.arraycopy()

> **설명**:  복사할 배열과 붙여넣을 배열을 합칠수 있는 메서드 <br/>
System 클래스에 포함된 메서드


**System.arraycopy(arr1,index1,arr2,index2,len)**
- arr1 : 복사할 배열
- index1 : 복사를 시작할 인덱스
- arr2 : 붙여넣기 할 배열
- index2 : 붙여넣기를 시작할 인덱스
- len: 붙여넣을 길이를 지정
```java
int[] intArr1 = new int[] {1,2,3,4,5};
int[] intArr2 = new int[] {99,98,97,96,95};
System.arraycopy(intArr1,1,intArr2,2,3);
for(int i : intArr2) System.out.println(i);
```
**출력결과**
```
99
98
2
3
4
```
**흐름** <br/>
1.  intArr1의 index[1]부터 len 길이만큼 복사
2.  복사한 배열을  intArr2 의 intArr2[2]인덱스 부터 붙여넣음

### **!주의**
>붙여넣은 배열은 기본값에 덮여씌워지는 것이므로 기본값은 지워짐



