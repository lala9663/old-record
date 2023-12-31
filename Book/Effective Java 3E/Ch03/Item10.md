## equals는 일반 규약을 지켜 재정의하라

equals 메서드는 잘못 재정의하면 끔찍한 결과를 초래한다. 문제를 회피하는 가장 쉬운 길은 아예 재정의 하지 않는 것이다.  
그냥 두면 그 클래스의 인스터스는 오직 자기 자신과만 같게 된다.

### euals를 재정의하지 않아야 하는 상황
1. 각 인스턴스가 본질적으로 고유하다.
   - 값을 표현하는 게 아니라 동작하는 개체를 표현하는 클래스가 여기에 해당 ex)Thread
3. 인스턴스의 논리적 동치(logical equality)를 검사할 일이 없다.
4. 상위 클래스에서 재정의한 equals가 하위 클래스에도 딱 들어맞는다. ex) 대부분의 Set 구현체는 AbstractSet이 구현한 equals를 상속 받아 쓴다.
5. 클래스가 private이거나 package-private이고 equals 메서드를 호출할 일이 없다.

### equals를 재정의해야 하는 상황
- **객체 식별성** 아니라 **논리적 동치성**을 확인해야하는 상황이고, 상위 클래스의 equals가 논리적 동치성을 비교하도록 재정의되지 않는다면 equals를 재정의해야 한다.
- 주로 **값 클래스(Integer, String**) 들이 여기 해당한다.
- 값 클래스라도 값이 같은 인스턴스가 둘 이상 만들어지지 않음을 보장하는 인스턴스 통제 클래스라면 equals를 재정의하지 않아도 된다. ex)Enum
- 같은 인스턴스가 2개 이상 만들어지지 않으면, 논리적 동치성과 객체 식별성이 사실상 똑같은 의미가 된다.
- 객체 식별성: Object identity, 두 객체가 물리적으로 같은지

### 따라서

Java에서 모든 객체는 'equals' 메서드를 가지고 있다. 이 메서드는 객체의 동등성을 확인하기 위해 사용된다.  
하지만 기본 'equals' 메서드는 객체의 참조 주소만을 비교하므로, 객체 내부의 내용을 비교하는 용도로는 적합하지 않을 수 있다.  
따라서 사용자 정의 클래스에서 'equals' 메서드를 재정의할 때는 다음의 규약을 따라야 한다.  
  
1. 반사성(Reflexivity): 어떤 객체 'x'에 대해, 'x.equals(x)'는 항상 'true'를 반환해야 한다.
2. 대칭성(Symmetry): 어떤 객체 'x'와 'y'에 대해 'x.equsls(y)'가 'true'를 반환하면, 'y.equals(x)'도 'true'를 반환해야 한다.
3. 추이성(Transitivity): 어떤 객체 'x', 'y', 'z'에 대해, 만약 'x.equals(y)'가 'true'이고, 'y.equals(z)'도 'true'이면 x.equals(z)'도 'true'여야 한다.
4. 일관성(Consistency): 어떤 객체 'x'와 'y'에 대해, 'equals'를 호출한 결과가 변하지 않는한, 여러 번 호출해도 항상 동일한 결과를 반환해야 한다.
5. null에 대한 비교(Comparison to 'null'): 모든 객체 'x'에 대해, 'x.equals(null)'은 항상 'false'여야 한다.


### 그러면

더 나은 equals 메서드 구현 방법은??  
  
1. == 연산자를 사용해 입력이 자기 자신의 참조인지 확인한다. 자기 자신이면 true를 반환 (최적화용)
2. instaceOf 연산자로 입력이 올바른 타입인지 확인한다. 그렇지 않으면 false 반환
   - 올바른 타입은 equals가 정의된 클래스인 것이 보통이지만, 가끔 그 클래스가 구현한 특정 인터페이스가 될 수 있다.
   - 어떤 인터페이스는 자신을 구현한 서로 다른 클래스끼리도 비교할 수 있도록 equals 규약을 수정하기도 한다. 이런 인터페이스를 구현한 클래스라면 equals에 클래스가 아닌 해당 인터페이스를 사용해야 한다. ex) Set, List, Map
3. 입력을 올바른 타입으로 형변환한다.
   - 2번에서 instanceOf 검사를 했기 때문에 이 단계는 통과
4. 입력 객체와 자기 자신의 대응되는 핵심 필드들이 모두 일치하는지 하나씩 검사한다. 모든 필드가 일치하면 true 를 반환, 하나라도 틀리면 false 반환
   - 2단계에서 인터페이스를 사용했다면 입력 필드 값을 가져올 때도 그 인터페이스의 메서드를 사용해야 한다.
