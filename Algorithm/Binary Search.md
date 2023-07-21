## 이진 탐색 

**정렬된 배열**에서 특정한 값을 빠르게 찾는 탐색 알고리즘이다. 배열의 중간 값과 찾고자 하는 값을 비교하여 반씩 데이터를 제거하면서 찾는 값을 찾아낸다.
이 알고리즘은 매우 효율적으로 동작하며, 배열의 크기에 따라 시간 복잡도가 O(log N)으로 매우 빠르게 수행된다. 

![이진 탐색 과정](https://blog.kakaocdn.net/dn/c0CGvA/btsg3W0R3z8/r41t7I8QQMvoeVM6fS4Kn0/img.gif)


## 예제 코드
1. while 문 사용한 이진 탐색
```
public int binarySearchIterative(int[] arr, int target) {
    int left = 0;
    int right = arr.length - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    return -1; // 원하는 값이 배열에 없는 경우
}
```
2. 재귀함수를 이용한 이진 탐색
```
public int binarySearchRecursive(int[] arr, int target, int left, int right) {
    if (left <= right) {
        int mid = left + (right - left) / 2;

        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            return binarySearchRecursive(arr, target, mid + 1, right);
        } else {
            return binarySearchRecursive(arr, target, left, mid - 1);
        }
    }

    return -1; // 원하는 값이 배열에 없는 경우
}
```


## 사용처

1. 검색:
- 데이터가 정렬되어 있을 때, 특정 값을 빠르게 찾아야 할 때 사용 (예를 들어, 전화번호부나 사전과 같은 대용량의 데이터에서 빠르게 특정 단어나 단어의 의미를 찾을 때)
2. 데이터 조회
- 정렬된 데이터에서 특정 값을 조회해야 할 때 이진 탐색을 사용
3. 삽입/삭제/수정:
- 정렬된 배열에서 새로운 데이터를 삽입하거나, 기존 데이터를 삭제 또는 수정할 때 이진 탐색을 활용
4. 가상 메모리 관리:
- 운영체제에서 가상 메모리 관리에 이진 탐색을 사용하여 페이지 테이블을 검색하는데 활용
