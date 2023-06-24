## Queue

Queue는 스택과 마찬가지로 데이터를 일시적으로 쌓아두는 기본 자료구조이다.</br>
Queue는 자료구조의 스택과 반대의 구조이다. 큐는 선입선출 FIFO(First In First Out)의 형태로 가장 먼저 들어온 데이터가 가장 먼저 나가는 구조이다.

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcPffuk%2FbtqRxZQDdZN%2FmiYr65640TgaOvLVjJ9xp0%2Fimg.png" width="400" height="200">


## 특징

- 먼즈 들어간 원소가 먼저 나오는 구조
- FIFO의 구조
- 활용 분야가 넓다.
- 시간 복잡도 : O(n)
- 공간 복잡도 : O(n)

대표적인 사용처
- 작업 관리(운영체제에서 프로세스 스케줄링)
- 네트워크 통신
- 대기열 관리

## 큐 용어
- enQueue() : 큐에 데이터를 넣음
- deQueue() : 큐에 데이터를 뺌
- isEmpty() : 큐가 비어있는지 확인
- isFull() : 큐가 꽉 차 있는지 확인
- peek() : 앞에 있는 원소를 삭제하지 않고 반환

## 큐 구현 하기

```
import java.util.LinkedList;
import java.util.Queue;

public class Main {

    public static void main(String[] args) {
        Queue<Integer> queue = new LinkedList<Integer>();

        queue.offer(1);
        queue.offer(2);
        queue.offer(3);
        queue.offer(4);
        queue.offer(5);

        while(!queue.isEmpty()) {
            System.out.println(queue.poll());
        }

    }

}
```

출력결과
```
1
2
3
4
5
```

그러면 2개의 스택을 이용하여 큐를 만들어보자

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Ft1.daumcdn.net%2Fcfile%2Ftistory%2F222BDF4E5462B1E00D"  width="400" height="200">

순서
1. inBox 에 데이터를 push(삽입)한다. -A,B
2. inBox 에 있는 데이터를 pop(추출)하여 outBox 에 push 한다. -B,A
3. outBox 에 있는 데이터를 pop 한다. -A,B 순으로 출력

즉, inBox 스택에 A,B 순으로 데이터를 삽입하면 위 그림 처럼 inBox 스택에 그림과 같은 순서로 쌓인다.
그리고 inBox 스택에 있는 데이터를 pop 해서 outBox로 옮깁니다. 그렇게 되면 outBox 에는 B, A 순으로 쌓인다.
그리고 다시 outBox 스택에 있는 데이터를 pop 하는경우 A,B 순으로 데이터가 출력 된다.

그럼 이걸 코드로 구현해보자.

```
public class Queue {

    private Stack inBox = new Stack();
    private Stack outBox = new Stack();

    public void enQueue(Object item) {
      if(outBox.isEmpty()) {
        while(!inBox.isEmpty()) {
          outBox.push(inBox.pop());
        }
      }
      return outBox.pop();
    }

    public static void main(String[] args) {
		Queue queue = new Queue();
		queue.enQueue("A");
		queue.enQueue("B");
		queue.enQueue("C");
		
		System.out.println(queue.deQueue());
		System.out.println(queue.deQueue());
		System.out.println(queue.deQueue());
	}
}
```

출력결과

```
A,B,C
```
</br></br></br>

참고</br>
[WooVictory](https://github.com/WooVictory/Ready-For-Tech-Interview/blob/master/Data%20Structure/%5BData%20Structure%5D%20Stack%EA%B3%BC%20Queue.md) 자료구조 </br>
[Creator Developer](https://creatordev.tistory.com/83) 님의 블로그

