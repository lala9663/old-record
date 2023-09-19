## 생성자에 매개변수가 많다면 빌더를 고려하라
- 정적 팩터리와 생성자는 선택적 매개변수가 많을 때 적절히 대응하기 어렵다는 제약이 있다.
- 해당 문제의 대안으로 나온 패턴이 **점층적 생성자 패턴**(telescoping constructor patter)과 **자바빈즈 패턴**이 등장했다. 하지만 한계가 있다.
  
### 점층적 생성자 패턴
 필수 매개변수만 받는 생성자, 필수 매개변수와 선택 매개변수 1개를 받는 생성자, 필수 매개변수와 선택 매개변수 2개를 받는 생성자. 원하는 매개변수를 모두 포함한 생성자 중 가장 짧은 것을 골라 호출하는 방식

이 방식을 사용할 수 있지만, 매개변수가 많아지면 클라이언트 코드를 작성하거나 읽기 어렵다.  

### 자바빈즈 패턴
  매개변수가 없는 생성자를 호출해 인스턴스를 만들고, Setter를 이용해 원하는 매개변수의 값을 할당하는 방식이다.  
점층적 생성자패턴에 비해 인스턴스를 생성하기 쉽고, 더 읽기 쉬운 코드를 만든다. 하지만 객체 하나를 만들 때 메서드를 여러 개 호출해야 하고, 객체가 완전히 생성되기 전까지 일관성이 무너진 상태에 놓이는 단점이 있다.

### 빌더 패턴
이와 같은 단점을을 보안하기 위해 나온 패턴이다.
- 필수 매개변수만으로 생성자를 호출해 빌더객체를 얻은 뒤, 빌더가 제공하는 일종의 Setter 메서드를 이용해 원하는 매개변수를 설정한다. 마지막으로 매개변수가 없는 build 메서드를 호출해 객체를 얻는다.
- 빌더 패턴은 계층적으로 설계된 클래스와 함께 쓰기에 좋다.
- 빌더는 보통 생성할 클래스 안에 정적 멤버클래스로 만들어준다.

그럼 단점으로는 뭐가 있을까.
- 빌버 생성 비용이 크지는 않지만 성능에 민감한 상황에서는 문제가 될 수 있다.