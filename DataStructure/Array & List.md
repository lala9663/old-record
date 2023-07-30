##  배열(Array)

- Array는 고정된 크기의 연속적인 메모리 공간에 요소를 저장하는 장소
- 배열을 이용하면 하나의 변수에 여러 정보를 담을 수 있고, 반복문과 결합 하면 많은 정보도 효율적으로 처리할 수 있다.
- 크기가 고정되어 있기 때문에 요소의 추가 또는 삭제가 어렵고, 메모리 재할당이 필요하다.
- 연속된 메모리 공간을 사용하기 때문에 데이터의 삽입 또는 삭제가 비효율적이다.
- 배열의 크기를 변경하려면 새로운 배열을 생성하고 이전 요소를 복사해야 한다.
- 데이터 접근 속도: O(1)
- 데이터 삽입 속도: O(N) - 데이터가 많은 경우, 비효율
- 데이터 삭제 속도: O(N)
- 메모리 할당
 - 메모리에는 Array가 선언되자 마자 Compile time에 할당 
 - 정적 메모리 할당

Array 구현 예시 코드
  ```
  public class ArrayExample {
    public static void main(String[] args) {
        // 정수형 배열 생성
        int[] numbers = new int[5];

        // 배열에 값 할당
        numbers[0] = 10;
        numbers[1] = 20;
        numbers[2] = 30;
        numbers[3] = 40;
        numbers[4] = 50;

        // 배열 값 출력
        for (int i = 0; i < numbers.length; i++) {
            System.out.println(numbers[i]);
        }
    }
}
```

## 리스트(List)
- 동적으로 크기가 조정될 수 있는 자료구조이다.
- 요소의 추가, 삭제, 검색 등을 유연하게 처리할 수 있다.
- 다양한 구현제가 있으며, ArrayList와 LinkedList가 가장 일반적으로 사용된다.
  - ArrayList는 내부적으로배열을 사용하여 요소를 저장하고, 크기가 동적으로 조정된다. 따라서 인덱스를 통해 요소에 빠른 접근이 가능하다.
  - LinkedList는 각 요소가 다음 요소를 가리키는 방식으로 구현되어 있어 삽입, 삭제가 빠르며 요소의이동이 필요하지 않는다. 그러나 인덱스를 통한 접근이 느리고 추가적인 메모리 공간을 사용한다.
- List는 여러 가지 유용한 메서드를 제공하여 요소의 추가, 삭제, 검색, 정렬 등을 쉽게 처리할 수 있다.
- 데이터 접근 속도: O(N)
- 데이터 삽입 속도
 - 중간 삽입 없이 맨 앞과 맨 뒤에만 삽입한다면: O(1)
 - 그렇지 않다면 삽입할 위치를 찾고: O(N)
- 데이터 삭제 속도: O(N) -하지만, Array보다 빠르게 삭제 연산을 수행
- 메모리 할당
 - 메모리는 새로운 Node가 추가될 때 runtime에 할당
 - 동적 메모리 할당

List(ArrayList) 구현 드
```
import java.util.ArrayList;
import java.util.List;

public class ListExample {
    public static void main(String[] args) {
        // 문자열 리스트 생성
        List<String> names = new ArrayList<>();

        // 리스트에 값 추가
        names.add("Alice");
        names.add("Bob");
        names.add("Charlie");
        names.add("David");
        names.add("Eve");

        // 리스트 값 출력
        for (String name : names) {
            System.out.println(name);
        }
    }
}
```

List(LinkedList) 구현 코드

```
import java.util.LinkedList;

public class LinkedListExample {
    public static void main(String[] args) {
        // 문자열 LinkedList 생성
        LinkedList<String> names = new LinkedList<>();

        // 리스트에 값 추가
        names.add("Alice");
        names.add("Bob");
        names.add("Charlie");
        names.add("David");
        names.add("Eve");

        // 리스트 값 출력
        for (String name : names) {
            System.out.println(name);
        }
    }
}
```

## 그럼 언제 뭘 써야할까?

Array는 크기가 고정되어 있는 경우에 유용하며, 빠른 접근 속도가 요구되는 경우에 적합하다.

List는 동적인 데이터 구조를 구현하고, 요소의 추가, 삭제가 빈번하게 발생하는 경우에 유용하다. 


