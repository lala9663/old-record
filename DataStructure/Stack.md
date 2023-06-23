## Stack

Stack(스택)은 데이터를 일시적으로 쌓아 놓는 자료구조로, 데이터의 입력과 출력 순서는 후입선출(LIFO: Last In First Out)이다.

즉, 가장 나중에 넣은 데이터를 가장 먼저 꺼낸다. 

</br>
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F99CDA84A5CB47EEA22" width="400" height="200">

## 특징

- 나중에 들어가나 원소가 먼저 나오는 구조
- LIFO
- 시간복잡도 : O(n)
- 공간복잡도 : O(n)

대표적인 사용처
 - 뒤로가기/ 실행취소
 - 깊이 우선 탐색(DFS)
 - 함수 호출과 반환 관리
 - 괄호 짝 맞추기 ((),{},[])

## 스택의 구현

일반적으로 스택에 사요오디는 필수적인 메서드이다.
- pop : 스택의 가장 최상위(마지막)에 위치한 데이터를 추출한 후에 스택에서 삭제한다.
- push : 스택의 가장 최상위(마지막)에 위치한 데이터를 삽입한다.
- isEmpty : 스택이 empty 상태인지 확인한다.
- clear : 스택에 저장된 모든 데이터를 삭제하고 스택을 초기화한다.
- peek : 스택의 가장 최상위에 위치한 데이터를 추출한다. pop 메서드와는 달리 스택에서 데이터를 삭제하지 않는다.

## Java에서 제공해주는 Stack 클래스

```
Stack<Element> stack = new Stack<>();
```

```
import java.util.Stack;

import javax.lang.model.element.Element;

public class Main {
    public static void main(String[] args) {
        Stack<Integer> stack = new Stack<>();
        for(int i=1; i<=10 ; i++) {
            stack.push(i);       // 1부터 10까지 넣기
            System.out.println(stack.peek()); // 1~10 출력
        } 
        stack.pop();    // 하나 꺼내고 삭제
        System.out.println(stack.peek());    //9출력
        System.out.println(stack.empty());    //false출력
    }

}
```

## 배열로 Stack 구현

```
public class ArrayStack {
    int top;
    int size;
    int[] stack;

    public ArrayStack(int size) {
        this.size = size;         // 스택 사이즈 설정
        stack = new int[size];    // 스택 배열 생성
        top = -1;                 // 스택 포인터 초기화
    }

    public void push(int item) {
        stack[++top] = item;
        System.out.println(stack[top] + " Push!");
    }

    public void pop() {
        System.out.println(stack[top] + " Pop!");
        stack[top--] = 0;
    }

    public void peek() {
        System.out.println(stack[top] + " Peek!");
    }
}
```





  


