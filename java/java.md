## Java

<details>
<summary>📚 공부한 자료</summary>

- 자바의 정석

</details>

### 1. JVM이 정확히 무엇이고, 어떤 기능을 하는지 설명해 주세요. ⭐️

  - 답변: 자바 가상 머신(Java Virtual Machine)으로 자바 어플리케이션을 실행하는 가상머신이다. 컴퓨터로부터 java 애플리케이션 실행을 위한 메모리를 할당 받아 Runtime Data Area를 구성한다. JVM은 인터프리터와 JIT 컴파일러를 통해서 바이트코드를 각 운영체제에 맞는 기계어로 해석해서 실행시키고, GC(가비지 컬렉션)을 통해 애플리케이션의 동적 메모리를 관리한다.
- **그럼, 자바 말고 다른 언어는 JVM 위에 올릴 수 없나요?**
  - 답변: 자바 이외의 언어도 JVM 위에 올릴 수 있다. Kotlin, Groovy, Scala 등의 언어가 JVM 위에서 실행될 수 있다.

- **반대로 JVM 계열 언어를 일반적으로 컴파일해서 사용할 순 없나요?**
  - 답변: 일반적으로 바이트코드로 컴파일한 후 JVM에서 실행하지만 바이트코드 외에도 다른 형식으로 컴파일할 수도 있다. 코틀린의 경우 Kotlin Native 컴파일러를 사용하여 기계어로 컴파일 가능하다. 하지만 JVM은 바이트코드를 실행하는 데 최적화 돼 있으므로 기계어로 컴파일 하는 것이 권장되지 않는다.

- **JVM과 내부에서 실행되고 있는 프로그램은 부모 프로세스 - 자식 프로세스 관계를 갖고 있다고 봐도 무방한가요?**
  - 답변: JVM은 운영체제 위에서 실행되는 프로그램(단일 프로세스)이며, 내부에서는 스레드(thread)를 이용해서 동시에 여러작업을 처리한다. 즉, 부모-자식 프로세스의 관계는 아니다. 스레드는 프로세스 내부에서 실행되는 실행단위로 프로세스의 자원을 다른 스레드와 공유하여 효율적인 작업 처리가 가능하다.

- **Java bytecode란 무엇인가요?**
  - 답변: 자바 바이트 코드는 **자바 가상 머신(JVM)이 이해할 수 있는 언어로 변환된 자바 소스 코드**를 의미한다. 자바 바이트 코드의 확장자는 .class이며 자바 바이트 코드는 자바 가상 머신만 설치돼 있으면 어떤 OS에서든 실행될 수 있다.

- **그렇다면 Java는 컴파일 언어일까요, 인터프리터 언어일까요?**
  - 답변: 자바는 컴파일 언어와 인터프리터 언어의 특성을 모두 가지고 있다. 자바 소스 코드는 먼저 자바 컴파일러에 의해서 자바 바이트 코드로 변환되고 이 자바 바이크 코드가 JVM에 의해서 인터프리트 방식으로 실행된다. 이러한 특성 덕분에 자바는 한번 작성하면 어느 플랫폼에서든 실행할 수 있는 '한번 쓰고 어디서나 실행(WORA)'의 특성을 가질 수 있다. 또한 자바는 JIT(Just-In-Time) 컴파일러를 통해 실행 시점에 바이트 코드를 기계어로 변환하여 실행 속도를 향상시키는 기능도 제공한다.


- **JVM의 동작 방식에 대해 간단하게 설명해주세요.**
  - 답변:
  1. javac(자바 컴파일러)가 .java 파일을 .class(자바 바이트코드)로 컴파일한다.
  2. class 파일을 실행하면 JVM은 OS로부터 메모리를 할당한다.
  3. Class Loader가 class 파일들을 JVM Runtime Data Area로 로딩한다.
  4. Runtime Data Area로 로딩된 클래스 파일들은 Execution Engine을 통해서 해석된다.
  5. 해석된 바이트 코드는 Runtime Data Area의 각 영역에 배치되어 수행된다. 이 과정에서 Execution Engine에 의해서 GC의 작동과 스레드 동기화가 이루어진다.

- **JVM의 구조에 대해 설명해주세요.**
  - 답변: JVM은 크게 Class Loader, Runtime Data Area, Execution Engine, JNI(Native Method Interface), Native Method Library로 나눌 수 있다.

- **JVM의 Runtime Data Area 영역은 무엇인가요?**

- **JVM Stack 과 Heap 영역의 가장 큰 차이점은 무엇인가요?**

- **만약 두 개의 스레드가 동시에 힙에 있는 메모리에 접근할 때 동시성 문제가 생길 수 있습니다. 구체적인 예시로는 어떤 것이 있을까요?**

- **스레드이 메서드별로 스택이 할당 되는데, 메서드가 종료되게 되면 그 메서드 안에서 아용된 로컬 변수가 쓸모 없어지기 때문에 메모리 해제가 되는데, 만약 메서드 안에서 선언한 변수가 참조형 타입인 경우에는 어떤 식으로 메모리가 사용되나요?**

- **Java 메모리 영역 중 Stack 과 Heap 에는 각각 어떤 것이 저장되나요?**

- **기본형 데이터 타입과 참조형 데이터 타입의 실제 값은 각각 어느 영역에 저장되나요?**

- **그렇다면, `Person p = new Person()` 를 실행했을 때 `p` 와 `Person() 객체` 는 각각 어느 영역에 저장되나요?**

  - 답변: p는 


- **Java 메모리의 있는 스택 프레임은 메서드가 종료되면 사라집니다. 하지만 힙 영역에 있는 객체들은 메서드가 종료되도 메모리에 남아 있습니다. 왜 그럴까요?**

- **Static 영역과 Heap 영역의 공통점과 차이점은 무엇인가요?**

### 2. final 키워드를 사용하면, 어떤 이점이 있나요?
  Answer:
    `final` 키워드는 변수 앞, 매개변수 앞, 클래스, 메소드에 붙을 수 있으며, 변수와 매개변수 앞에 붙인다면 해당 변수의 값을 변경할 수 없게 하고, 클래스 앞에 붙으면 해당 클래스를 확장할 수 없게 하며, 메소드 앞에 붙으면 자식 클래스가 해당 메소드를 오버라이드 할 수 없게 합니다.
      final 키워드의 이점은 변수 앞에 붙어서 변경되면 안되는 변수의 변경을 방지할 수 있고, final 클래스와 final 메소드를 통해 상속이나 오버라이딩으로 상위 객체의 용도에서 크게 벗어나는 하위객체가 생성되는 것을 막아줄 수 있습니다.
      또한 final 키워드는 불변 객체를 만들때 많이 사용되는데, 불변객체를 쓰는 것은 GC의 작동에 도움을 줍니다. 불변 객체가 생성되기 위해서는 해당 객체를 사용하는 컨테이너 객체가 있을 것인데, 만약 그 컨테이너 객체가 살아있다면 그 안에 있는 불변 객체가 참조되어 사용되고 있다는 것이므로 해당 불변 객체는 GC 스캔에서 스킵합니다. 즉 GC의 스캔 범위를 줄임으로써 GC의 효율을 증가시킬 수 있는 것입니다.

- **그렇다면 컴파일 과정에서, final 키워드는 다르게 취급되나요?**
  Answer:
    `final`이 붙은 클래스 같은 경우는 다른 클래스들과 컴파일 시점에 조금 다르게 처리될 수 있는데, 바로 Method Dispatch 과정에서 그렇습니다. Method Dispatch는 메소드가 호출될 때 실제로 실행될 메소드를 결정하는 과정입니다. 이 과정이 컴파일 타임에 이뤄진다면 static dispatch라고 하고, 런타임때에 이뤄진다면 dynamic dispatch라고 합니다. dynamic dispatch는 상속 등의 다형성을 지원하기 위해 있는 것인데, 상속으로 인해 어떤 메소드가 오버라이딩 되었다면 실제로 실행될 메소드는 런타임시점까지 알수가 없기 때문입니다. 하지만 `final` 클래스 같은 경우 실제로 실행될 메소드가 컴파일 시점에 결정될 수 있게 되고(static dispatch), 컴파일러가 inlining 같은 최적화를 해줌으로써 약간의 성능을 개선할 수 있습니다.

       출처: https://codingmon.tistory.com/39
    

### 3. 변수는 어떤 것인가요?

- **참조형 변수에서 실제 값을 저장하지 않고 주소값을 저장하는 이유는 무엇인가요?**

- **그렇다면 기본형 변수는 스택 영역 내에 실제 값을 저장하는 이유는 무엇인가요?**

- **변수와 상수의 차이는 무엇인가요?**

### 4. 부동소수점이 무엇인가요?

  - 답변: 
   컴퓨터에서 부호, 가수부, 지수부를 통해 실수를 표현하는 방법이다. 부동소수점 방식은 고정 소수점 방식보다 표현할 수 있는 실수의 범위가 더 넓지만, 정확도에 약간의 오차가 있다. 부동소수점 방식을 사용하는 실수 자료형은 float, double 등이 있다. 

  
    래퍼런스: https://velog.io/@maketheworldwise/float-double-%EB%B6%80%EB%8F%99%EC%86%8C%EC%88%98%EC%A0%90

- **부동소수점을 사용하면, 소수 계산 오차 문제가 사라지나요?**
  
  - 답변: 사라지지 않는다. 부동소수점 방식의 표현에는 정확도에 약간의 오차가 있다. 이로 인해 예상치 못한 결과가 발생할 수 있으며, 이는 금융 계산과 같이 정밀한 계산이 필요한 경우에 큰 문제를 일으킬 수 있다.

- **자바에서 실수형 계산을 정확하게 하기 위해서는 어떻게 해야 하나요?**
  
  - 답변: 자바에서는 BigDecimal 클래스를 이용해서 부동소수점의 오차문제를 해결할 수 있다. BigDecimal은 손실이 없는 정확한 소수점 연산을 지원하기에, 금융 계산과 같이 정밀한 계산이 필요한 애플리케이션에서 많이 사용된다.

  ```java
  BigDecimal a = new BigDecimal("0.1");
  BigDecimal b = new BigDecimal("0.2");
  BigDecimal result = a.add(b);
  ```

  subtract, multiply, divide 등의 메서드를 제공하여 산술 연산이 가능하다. 이중, divide 메서드는 반올림 모드를 지정해주어야한다. BigDecimal은 무한 소수를 표현할 수 있기 때문에, 연산 결과가 무한 소수가 될 경우 반올림 모드를 지정하지 않으면 ArithmeticException이 발생한다.


  또한 BigDecimal은 정밀한 계산을 가능하게 하지만, float, double에 비해 성능상의 오버헤드가 존재한다. 따라서 성능이 중요한 애플리케이션에서는 사용 전에 성능 테스트를 진행하는 것이 좋다.
  또한 BigDecimal은 불변 객체이므로, 연산을 수행할 때마다 새로운 객체가 생성된다. 이는 메모리 사용량이 증가할 수 있으므로 메모리 관리에도 주의가 필요하다.
  

- **그렇다면 BigDecimal 은 실수를 어떤 형태로 저장하나요?**
  - 답변: BigDecimal은 intValue * 10 ^ (-scale)과 같은 형식으로 수를 표현한다. 예를 들어 123.45는 12345 * 10 ^ (-2)로 표현된다.

  ```java
  public class BigDecimal extends Number implements Comparable<BigDecimal> {

    private final BigInteger intVal; // 수를 구성하는 전체 자리수

    private final int scale;  // 전체 소수점 자리수

    private transient int precision; // 정밀도

    // ...
  }
  ```

### 5. `==` 과 `equals` 의 차이점은 무엇인가요?

- **Object 의 `equals` 메서드는 어떻게 구현되어 있나요?**

- **아래의 코드는 어떤 결과가 나올까요? 이유를 설명해보세요.**

  ```java
  Integer a = new Integer(3);
  Integer b = new Integer(3);
  System.out.println(a==b);
  ```

- **그럼, `equals()` 와 `hashCode()` 에 대해 설명해 주세요.**

- **`hashCode()` 의 용도는 무엇인가요?**

- **본인이 `hashCode()` 를 정의해야 한다면, 어떤 점을 염두에 두고 구현할 것 같으세요?**

- **그렇다면 `equals()` 를 재정의 해야 할 때, 어떤 점을 염두에 두어야 하는지 설명해 주세요.**

- **만약 `equals()` 와 `hashCode()` 를 둘 다 재정의 했을 때, 객체의 주소값을 비교해야 한다는 상황이 온다면 어떻게 하나요?**

### 6. 다형성은 무엇인가요? 또 언제 활용할 수 있을까요?
  - 답변: 다형성이란 하나의 타입의 여러 종류의 객체를 대입할 수 있는 성질을 의미한다. 다형성을 활용하면 기능을 확장하거나, 객체를 변경해야할 때 **타입 변경없이 객체 주입**만으로 수정이 일어나게 할 수 있다.

  #### 다형성을 구현하는 방법
  - 오버로딩: 오버로딩이란, 매개변수의 타입, 개수 등을 다르게하여 같은 이름의 메소드를 여러 개 정의하는 것을 의미한다. 오버로딩은 여러 종류의 타입을 받아들여 같은 기능을 하도록 만들기 위한 작업이고, 이 메소드들을 동적으로 호출할 수 있으니 다형성이라고 할 수 있다.
  - 오버라이딩: 오버라이딩이란 상위클래스의 메서드를 하위 클래스가 상속받아 재정의하는 것을 의미한다. 오버라이딩 또한 다형성을 구현하는 방법이다.

### 7. 인터페이스와 추상클래스의 차이점은 무엇일까요?

- **왜 클래스는 단일 상속만 가능한데, 인터페이스는 2개 이상 구현이 가능할까요?**

- **인터페이스에서, `default method` 란 어떤 것인가요? 어떤 상황에서 주로 사용되나요?**

- **클래스A 가 인터페이스A, 인터페이스B 를 구현한다고 합시다. 만약 인터페이스A, 인터페이스B 에 동일한 시그니처를 가진 동일한 default method 가 있을 때, 다중 상속의 문제점이 발생하나요? 이것을 어떻게 해결하나요?**

### 8. A 라는클래스에 특정코드를 주고 싶을때, 상속과 조합의 차이는 무엇이고, 각각의 장점을 설명해주세요.
상속과 조합 모두 OOP에서 널리 사용되는 코드 재사용 기법이다.
#### 상속
- 부모클래스와 자식 클래스의 의존성이 컴파일 타임에 해결
- is-a 관계
- 부모클래스에 구현에 의존, 결합도가 높다.
- 클래스 사이의 정적인 관계
- 부모 클래스 안에 구현된 코드 자체를 물려 받아 재사용한다.

#### 조합(Composition)
- 필드로 클래스의 인스턴스를 참조하게 만드는 설계이다.
- 두 객체 사이의 의존성이 런타임에 해결
- has-a 관계
- 구현에 의존하지 않는다.
- 객체의 구현이 아닌 내부에 포함되는 인터페이스에 의존한다.
- 객체 사이의 동적인 관계
- 포함되는 객체의 퍼블릭 인터페이스를 재사용

상속의 여러가지 단점 때문에, 상속은 두 객체가 개념적으로 연관 관계가 있을 때만 하며, 코드 재사용에 있어 상속보다 조합을 지향하는 것이 좋다.
상속의 단점은 아래와 같다.

- 결합도가 높아진다: OOP에서 결합도는 낮을 수록, 응집도는 높을 수록 좋다. 상속을 하게 되면 부모 클래스와 자식 클래스의 관계가 컴파일 시점에 결정되기에 결합도가 높아질 수밖에 없다.
- 불필요한 기능 상속: 부모클래스에 메서드를 추가했을 때, 자식 클래스에는 적합하지 않은 메소드가 상속되는 경우가 발생할 수 있다.
- 부모 클래스의 결함이 자식 클래스로 그대로 넘어온다.
- 단일 상속의 한계
- 부모, 자식 클래스의 동시 수정 필요

### 9. 리플렉션에 대해 설명해 주세요.
  - 답변: 컴파일 타임이 아닌 **런타임**에 클래스, 메서드, 필드 등의 정보를 조회하고 검사할 수 있도록 하는 자바의 기능. 이미 로딩이 완료된 클래스에서 또 다른 클래스를 동적으로 로딩하여 생성자, 멤버 필드, 멤버 메서드 등을 사용할 수 있다. 구체적인 클래스 타입을 알지 못해도 그 클래스의 메소드, 타입, 변수 등에 접근할 수 있도록 해주는 Java의 API이다.

    - Reflection의 주요 기능:
      - 클래스 정보(클래스 이름, 메서드, 필드 등)을 런타임에 알 수 있다.
      - 런타임에 해당 클래스의 객체 생성 가능
      - 런타임에 메서드 호출 가능
      - 런타임에 필드에 접근하고 수정할 수 있다.


- **의미만 들어보면 리플렉션은 보안적인 문제가 있을 가능성이 있어보이는데, 실제로 그렇게 생각하시나요? 만약 그렇다면, 어떻게 방지할 수 있을까요?**
  - 답변: 리플렉션은 제한없이 사용하면 보안 문제를 일으킬 수 있다. 예를 들어 리플렉션을 통해 private처럼 보호된 필드나 메소드에 접근할 수 있는 등 보안 매커니즘을 우회할 수 있다.
  이러한 문제 방지를 위해 아래와 같은 조치를 할 수 있다.

  - **코드 검사와 테스트**: 리플렉션을 사용하는 부분에서 예기치 않은 동작이 발생하지 않도록 해야한다. 
  - **보안 매니저 사용**: Java는 SecurityManager라는 시스템을 제공한다. 이를 사용하면 애플리케이션의 보안 정책을 더 세밀하게 제어할 수 있다. 예를 들어, 특정 작업(ex. 리플렉션을 사용한 접근)을 허용하거나 금지하는 등의 설정을 할 수 있다.
  - **의존하는 라이브러리 검사**: 외부 라이브러리가 리플렉션을 어떻게 사용하는지 알아보고, 팔요하다면 그 라이브러리의 사용을 재고하는 것이 좋다.

- **리플렉션을 언제 활용할 수 있을까요?**
  - 답변: 코드를 작성할 시점에는 어떤 타입의 클래스를 사용할지 모르지만, 런타임 시점에 지금 실행하고 있는 클래스를 가져와서 실행해야하는 경우 사용된다.

  - 사용 예시:
    - 스프링 프레임워크에서 빈(Bean)의 생성과 의존성 주입.
    - 어노테이션 기반의 설정 처리
    - JPA에서 DB에서 값을 찾아오고 그 값으로 객체를 만들어주는데 이때 리플렉션으로 private 변수에 직접 접근하여 값을 할당한다.
    - 객체와 JSON 사이의 직렬화/역직렬화를 도와주는 Jackson 라이브러리도 리플렉션이라는 기능을 활용한다.

### 10. static class와 static method를 비교해 주세요.

- **static 을 사용하면 어떤 이점을 얻을 수 있나요? 어떤 제약이 걸릴까요?**
- **컴파일 과정에서 static 이 어떻게 처리되는지 설명해 주세요.**

### 11. 자바에서 `new` 키워드를 사용하면 어떤 일이 일어나나요? 메모리 관점에서 자세히 설명해주세요.
  - 답변: new 키워드로 객체를 생성하게 되면 객체는 지역 변수가 아닌 동적 메모리 즉, heap 영역에 할당된다. 따라서 GC가 해당 메모리를 해제할 때까지 heap 영역에 남아있게 된다.
  예를 들어서 자바에서 문자열을 다루는 방법에는 크게 두가지가 있다. 하나는 String 리터럴을 사용하는 방법이고, 다른 하나는 new 키워드로 String 객체를 생성하는 방식이다.
  String 리터럴은 자바의 컨스턴트 풀에 저장되며 동일한 리터럴은 메모리에서 하나의 참조로 관리된다. 반면, new 키워드로 생성된 스트링 객체는 힙 영역에 저징되며 별도의 메모리 공간을 차지한다. String 리터럴에서 컨스턴트 풀을 사용하는 이유는 자바에서 실행 성능과 메모리 사용 효율을 높이기 위해 스트링 리터럴을 재사용하기 위해서 이러한 메모리 관리 방식을 채택한 것이다.

### 12. 자바에서 스레드 풀(Thread Pool) 이란 어떤 것이고 언제 사용하나요?
  - 답변: 쓰레드 풀은 **미리 일정 개수의 스레드를 생성하여 관리하는 기법**이다. 이렇게 생성된 쓰레드들은 작업을 할당받기 위해 대기 상태에 있게 되는데, 작업이 발생하면 대기 중인 쓰레드 중 하나를 선택하여 작업을 수행한다. 작접이 완료되면 해당 스레드는 다시 대기 상태로 돌아가고, 새로운 작업을 할당 받을 준비를 한다.

  스레드 풀을 사용하면 스레드 생성 및 삭제에 따른 오버헤드를 줄일 수 있으며, 특정 시점에 동시에 처리할 수 있는 작업의 개수를 제한할 수 있다. 이를 통해 시스템의 자원을 효율적으로 관리하고 성능을 향상시킬 수 있다.

  쓰레드 풀은 작업 간의 의존성이 적은 웹 애플리케이션에 적용하기 좋다. 서버는 각 요청에 대해 별도의 쓰레드를 할당하여 처리하기에, 작업 간의 의존성이 적어서 쓰레드 풀을 효과적으로 사용할 수 있다.

### 13. Error 와 Exception 의 차이가 무엇인가요?
  - 에러: Error는 메모리 부족 등 시스템이 비정상적인 상황에 발생한다. 주로 JVM에서 발생시키기 때문에 애플리케이션 코드에서는 잡아서는 안되며 잡을 수도 없다.
  - 예외: Error와 달리 애플리케이션 코드에서 예외가 발생했을 경우에 사용된다. Exception은 다시 체크 예외와 언체크 예외로 구분된다.

- **체크 예외와 언체크 예외의 차이는 무엇인가요?**
  - 체크 예외는 RuntimeException을 상속받지 않은 예외 클래스들이다. 체크 예외는 복구 가능성이 있는 예외이므로 반드시 예외를 처리하는 코드를 함께 작성해야한다. IOException, SQLException이 대표적이다. 예외를 처리하지 않으면 컴파일 에러가 발생한다.
  - 언체크 예외는 RuntimeException 클래스를 상속받는 예외이다. 복구 가능성이 없는 예외들이므로 컴파일러가 예외처리를 강제하지 않는다. 예외처리가 강제되지 않으며, 대표적으로 NullPointerException, IllegalArgumentException 등이 있다.

- **`OutOfMemoryError` 는 어떤 경우에 발생하나요?**
  - Heap Size의 부족으로 Java Object를 힙에 할당하지 못하는 경우 발생한다.

- **`StackOverflowError` 는 어떤 경우에 발생하나요?**
  - 재귀 호출이 너무 깊게 이뤄지거나 메모리 스택이 초과될 때 발생한다. 재귀 호출 코드가 잘못되었거나 무한 루프가 존재할때 많이 발생한다.

- **왜 체크 예외는 반드시 try-catch 문으로 처리해야고 언체크 예외는 처리하지 않아도 될까요?**
  - 체크 예외는 예외 상황을 명시적으로 처리하도록 강제함으로써 시스템의 안정성을 높이기 위해 도입되었다. 언체크 예외는 이러한 체크 예외의 단점을 극복하기 위해 런타임 시점에 발생하여 예외처리를 선택적으로 할 수 있게 해줌으로써 개발자 입장에서 코드의 복잡성을 줄여주고, 유지보수를 용이하게 해준다.

### 14. 자바에서 쓰레드를 생성하는 방법에는 어떤 것들이 있나요?

- **그렇다면 두 방법의 장단점은 무엇인가요?**

- **`Runnable` 인터페이스의 용도는 무엇인가요?**

- **왜 Thread 클래스의 `public static native Thread currentThread();` 는 static 으로 선언되어 있나요?**

- **쓰레드의 `start()` 과 `run()` 메서드는 어떤 차이가 있나요?**

- **아래 코드의 결과는 어떻게 될까요?**

  ```java
  class MyRunnable implements Runnable{
    public void run(){
      System.out.println("My Runnable is running");
      Thread currThread = Thread.currentThread();
      currThread.setName("thread in run method");
      System.out.println("Current thread in run : " + currThread.getName());
    }
  }

  class TestRunnable {
    public static void main(String[] args) {
      Thread thread = new Thread(new MyRunnable());
      thread.run();
      System.out.println("Current thread in main : " + Thread.currentThread().getName());
    }
  }
  ```

- **새로 생성된 쓰레드의 호출 스택은 언제 사라질까요?**

### 15. 쓰레드의 상태값에는 어떤 것들이 있나요?

- **`WAITING` 과 `BLOCKED` 의 차이는 무엇인가요?**

- **왜 `sleep()` 과 `yield()` 는 static 메서드인가요?**

- **`yield()` 과 `join()` 의 차이점은 무엇인가요?**

- **`sleep()` 과 `wait()` 의 차이점과 공통점은 무엇인가요?**

### 16. 쓰레드의 동기화는 무엇이며, 동기화에 사용되는 방법들은 어떤 것이 있나요?

- **`synchronized` 에 의한 방법은 무엇이며, 어떤 장단점이 있을까요?**

- **`wait()`와 `notify()` 를 이용한 방법은 무엇이며, 어떤 장단점이 있을까요?**

- **`java.util.concurrent.locks` 에 있는 Lock 과 Condition 은 위의 문제들을 어떻게 해결했나요?**

- **`volatile` 키워드는 어떻게 변수에 대한 읽기와 쓰기를 동기화하나요?**

### 17. `ConcurrentHashMap` 은 무엇이며 어떻게 thread-safe 를 보장하나요?

- **버킷이 비어있는 경우, 새로운 노드를 추가할 때는 어떻게 락을 걸지 않고 thread-safe 를 보장할 수 있나요?**

### 18. 함수형 프로그래밍은 무엇이며, 왜 필요한가요?

- **함수형 프로그래밍의 특징을 설명해주세요.**

- **자바에서는 어떻게 함수형 프로그래밍을 할 수 있나요?**

- **`@FunctionalInterface` 어노테이션의 역할은 무엇인가요?**

- **람다식과 함수형 인터페이스의 관계는 무엇인가요?**

- **람다표현식과 익명클래스의 차이는 무엇인가요?**

- **자바에서 미리 함수형 인터페이스를 정의해놓은 이유는 무엇인가요?**

### 19. 자바에서 I/O가 느린이유는 무엇인가요?

- **운영체제에서 I/O는 어떻게 동작하나요?**

- **자바 IO 패키지가 OS의 I/O 보다 훨씬 느린 이유는 무엇인가요?**

- **자바에서 NIO 패키지는 왜 IO 패키지에 비해 속도가 빠른가요?**

- **그러면 IO 가 무조건 나쁜 것일까요?**
