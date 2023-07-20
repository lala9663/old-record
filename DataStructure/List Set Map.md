![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Ftdpf5%2Fbtq127JQCI8%2FLSdj32IFJg2bsAinWk5bBK%2Fimg.png)


## List

순서가 있고 중복을 허용한다.
인덱스로 원소에 접근이 가능하다.
크기가 가변적이다.

### List의 종류와 특징
- LinkedList
   - 양방향 포인터 구조로 데이터 삽입, 삭제가 빠르다.
   - ArrayList보다 검색이 느리다.
- ArrayList
   - 단방향 포인터 구조로 데이터 순차적 접근에 강점을 가진다.
   - 배열을 기반으로 데이터를 저장한다.
   - 데이터 삽입, 삭제가 느리다.
   - 데이터 검색이 빠르다.

## Map

Key와 Value의 한쌍으로 이루어지는 데이터의 집합.
Key에 대한 중복이 없으며 순서를 보장하지 않는다.
뛰어난 검색 속도를 가진다.
인덱스가 따로 존재하지 않기 때문에 iterator를 사용한다.

### Map의 종류와 특징
- HashMap
   - Key에 대한 중복이 없으며 순서를 보장하지 않는다.
   - Key와 Value 값으로 NULL을 허용한다.
   - 동기화가 보장되지 않는다.
   - 검색에 가장 뛰어난 성능을 가진다.
- HashTable
   - 동기화가 보장되어 병렬 프로그래밍이 가능하고 HashMap 보다 처리속도가 느리다.
   - Key와 Value 값으로 NULL을 허용하지 않는다.
- LinkedHashMap
   - 입력된 순서를 보장한다.
- TreeMap
   - 이진 탐색 트리(Red-Black Tree)를 기반으로 키와 값을 저장한다.
   - Key 값을 기준으로 오름차순 정렬되고 빠른 검색이 가능하다.
   - 저장 시 정렬을 하기 떄문에 시간이 다소 오래 걸린다.    

## Set

데이터의 집합이며 순서가 없고 중복된 데이터를 허용하지 않는다.
중복되지 않은 데이터를 구할 떄 유용하다.
빠른 검색 속도를 가진다.
인덱스가 따로 존재하지 않기 때문에 iterator를 사용한다.

### Set의 종류와 특징
- HashSet
  - 인스턴스의 해시값을 기준으로 저장하기 때문에 순서를 보장하지 않는다.
  - NULL 값을 허용한다.
  - TreeSet보다 삽입, 삭제가 빠르다.
- LinkedHashSet
  - 입력된 순서를 보장한다.
- TreeSet
  - 이진 탐색 트리(Red-Black Tree)를 기반으로 한다.
  - 데이터들이 오름차순으로 정렬된다.
  - 데이터 삽입, 삭제에는 시간이 걸리지만 검색, 정렬이 빠르다.   
