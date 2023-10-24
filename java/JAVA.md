# JAVA

### 🐾 10월 10일 

<details>
    <summary>JVM의 구조와 Java의 실행방식을 설명해주세요.</summary>
    <img width="1074" alt="qyTrK2Mkj8PwJALQ2nyFk-1658197983457" src="https://github.com/codestates-seb/seb45_main_006/assets/129938243/c561b3ef-93a4-440d-a3d4-08c5dbfeda4d">
    자바 컴파일러(javac)가 소스코드(.java)를 읽어 자바 바이트코드(.class) 로 변환
→ 클래스 로더를 통해 class 파일을 JVM으로 로딩 → 파일들은 Excution engine으로 해석되고 Runtime Data Areas에 배치되어 명령 수행

1. 인터프리터를 통해 코드를 한 줄씩 기계어로 번역하고 실행
   → 기본적으로 인터프리터로 실행하지만 특정 바이트 코드가 자주 실행되면 해당 바이트 코드를 JIT Compiler로 실행
2. JIT Complier를 통해 바이트 코드 전체를 기계어로 번역하고 실행
   → 특정 바이트 코드가 자주 실행 시

Class Loader : JVM 내로 클래스 파일을 로드, 링크,이니셜을 통해 배치

Execution Engine : JVM 내의 런타임 데이터 영역의 바이트 코드를 명령어 단위로 읽어 실행

Garbage Collector : 힙 메모리의 영역에 생성된 객체들 중 참조되지 않아 필요 없는 객체들을 제거

Runtime Data Area : 애플리케이션이 실행될 때 사용되는 데이터를 적재하는 영역

<img width="1428" alt="4JAw7vGWwkwhL3IspaHQC-1658200335039" src="https://github.com/codestates-seb/seb45_main_006/assets/129938243/cdcc10bd-9fd3-47b3-8abf-7a4d9d26ae37">
1. Method Area :  클래스정보(클래스명, 변수명, 메소드명,등 ), 인터페이스, 정적 메소드, 필드 등을 보관
2. Heap Area : new 키워드로 생성된 객체와 배열이 생성되는 영역
3. Stack Area :  메서드 호출시 사용되는 메모리 영역으로 메서드의 매개,지역변수, 리턴 값, 연산 시 나오는 값, 참조값 등 임시 데이터 저장
                 데이터는 스택 형식으로 순서대로 쌓이며 메서드가 끝나면 역순으로 제거됨
4. PC Register : 스레드가 생성될때 마다 생성되는 영역으로 현재 현재 수행중인 스레드의 명령어 주소를 저장하고 다음 실행할 스레드의 명령어 주소를 가리킴 
5. Native method stack : 자바 외 언어로 작성된 네이티브 코드를 위한 메모리 영역
    
</details>

<details>
    <summary>GC가 무엇인지, 필요한 이유가 무엇인지 동작방식에 대해 설명해주세요.</summary>

<br/>

GC는 동적으로 할당된 메모리 중 사용하지 않는 메모리를 자동 회수하는 과정을 말합니다. 

C, C++과 같은 기존 언어들은 개발자가 직접 메모리를 관리해야 했지만, 이로 인해 메모리 누수 같은 문제가 발 할 수 있습니다. 
Java에서는 가비지 컬렉터를 통해 자동으로 사용하지 않는 메모리를 회수해 메모리 관리를 보다 효율적으로 할 수 있습니다.

가비지 컬렉터는 **stop the world** , GC를 위해 JVM의 실행을 멈추고 참조되는 객체는 마킹, 참조되지 않는 객체는 힙에서 쓸어버리는 **Mark and sweap** 과정을 거치게 되고 작업을 재개합니다.

</details>

<details>
    <summary>컬렉션 프레임워크에 대해 설명해주세요.</summary>
<br/>

컬렉션 프레임워크는 Java에서 데이터를 효율적으로 저장하고 관리하기 위해 표준화한 클래스으 집합입니다.

자바의 인터페이스를 사용하여 구현되며 데이터를 저장하는 자료 구조에 따라 List, Set, Queue, Map 으로 정의하고 있습니다.

<details>
	<summary>
	List, Set, Map		
	</summary>

<br/>

- List : 순서가 있고 중복을 허용하는 자료 구조
    - ArrayList : 크기를 동적으로 관리, 배열처럼 주소값을 가지고 있지만 주소값이 무작위로 저장 / 최상위 타입으로 배열을 생성, 복사하기 때문에 요소의 접근에 성능이 좋음→ 검색에 효과적(인덱스를 기반으로한 접근)
    - LinkedList : 현재 가지고 있는 주소값과 다음 데이터의 주소값을 함께 저장 / 연결되어 있다보니 링크를 끊거나 연결하는 방식 → 삽입, 삭제 시 효과적


- Set : 중복요소가 없는 컬렉션으로 저장 순서를 유지하지 않는 컬렉션 (단, LinkedHashSet은 순서를 보장)
	- HashSet : interface 속성을 그대로 물려받아 중복 X, 순서 X / 해시테이블 사용하여 저장하기 때문에 검색 및 삽입, 삭제가 빠름 / null 허용 / [thread-safe](https://inpa.tistory.com/entry/JCF-%F0%9F%A7%B1-ArrayList-vs-Vector-%EB%8F%99%EA%B8%B0%ED%99%94-%EC%B0%A8%EC%9D%B4-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0) 하지 않아서 Vector나 외부에서 동기화 추가해야
	- TreeSet : 정렬방법 지정 가능(기본 오름차순) / 이진 검색 트리 형태 / 정렬된 상태를 유지하기 때문에 검색이 빠름 (HashSet에 비해 연산이 느림)


- Map : 키와 값으로 구성된 객체를 저장하는 구조로 Entry 객체라고도 한다. key는 중복 불가하지만 value는 중복 가능, 데이터 순서보장 X
	- HashMap : 매개변수 없는 생성자 사용/ 키나 값으로 null값 허용/ 검색 및 저장이 매우 빠름 / 동기화 지원 X → 여러 스레드를 사용할 때 주의
	- HashTable : 키와 값 모두 null 허용 X / 동기화 지원 → 여러 스레드 환경에서 안전하게 사용 가능

✔️ HashMap이 HashTable보다 더 많이 사용된다.

⇒ 동기화도 안되는데 왜? 동기화가 된다고 좋은 것은 아님. 동기화는 오버헤드를 불러 일으킬 수 있음. HashMap은 동기화를 지원하지 않지만 더욱 빠른 성능을 제공. 또한, 필요하면 Collections.synchronizedMap() 메서드 사용 가능

✔️ ConcurrentHashMap ?

⇒ 멀티스레드 환경에서 동시성 문제 해결할 때 세분화된 동기화를 제공해서 여러 연산이 수행될 수 있게 함

</details>
</details>

<details>
    <summary>제네릭에 대해 설명해주세요.</summary>
    자바 타입 안정성을 위해 사용되며 컴파일 과정에서 타입을 체크해주기 때문에 타입 안정성을 높이고 형변환의 번거로움을 줄여준다.
    타입을 고정하거나 타입의 대한 정의를 외부로 미룬다.
</details>

<details>
    <summary>애노테이션에 대해 설명해주세요.</summary>

<br/>

인터페이스를 기반으로 한 문법으로 주석처럼 코드를 달아 클래스에 특별한 의미를 부여하는 기능이다.
예시로 
    
@Override

개발자가 실수로 메소드 이름을 다르게 입력하여 오버라이딩이 아닌 별개의 메소드를 만들 수
있기 때문에 "이건 오버라이딩 한거야" 라고컴파일러에게 인지시키기 위해 달아놓는다

@Deprecated

기술 대체로 인해 다른 코드를 사용하여 해당 코드를 더이상 사용하지 않도록 유도하는 경우 사용한다
다른 곳에서 해당 메소드를 사용하면 경고 메시지가 나옴

@SuppressWarnings

컴파일 경고 메시지가 안나오게 만든다
애너테이션뒤에 ("null"), ("all") 등을 붙여 선택적으로 억제할 수도 있음 
-> @SuppressWarnings({"deprecation", "unused", "null"}) 여러개도 가능!

@FunctionalInterface

함수형 인터페이스를 선언할 때 사용하며 함수형 인터페이스는 오직 하나의 
추상 메서드만을 가질 수 있으므로 경고 메시지를 출력해준다

등의 표준 애노테이션이 있고

에너테이션을 정의하는 메타 에너테이션이인
@Target -> 애너테이션을 적용할 대상이며 위의 경우 메소드가 대상이 된다
		   메소드 말고도 CONSTRUCTOR FIELD TYPE 등 여러가지 가 있다
@Retention -> 애너테이션의 지속시간을 결정 SOURCE는 소스파일에 존재하며 
			  컴파일 시 확인 후 사라짐 오버라이드도 컴파일일러에서 오버라이드가 
			  잘 되었는지 확인 후 사라진다 이외에도
			  CLASS : 클래스파일에 존재, 실행시에 사용 불가 
			  RUNTIME : 클래스파일에 존재, 실행시 사용가능
       등이 있다.
</details>

<details>
    <summary>오버라이딩과 오버로딩이 무엇이며 어떤 차이가 있을까요?</summary>
</details>

<details>
    <summary>인터페이스와 추상클래스의 차이점에 대해 설명해주세요.</summary>

<br/>

추상클래스는 구체적인 구현을 가진 메서드와 추상 메서드(정의는 있지민 구현은 없는 메서드)를 모두 포함할 수 있습니다.
일반적인 멤버 변수와 생성자도 포함할 수 있습니다. 이를 통해 하위 클래스에게 상속되는 공통의 상태나 초기화 루틴을 제공할 수 있습니다.

인터페이스는 공통된 행동을 정의합니다. 이를 구현하는 클래스는 해당 인터페이스의 모든 메서드를 구현해야 합니다. 
인터페이스는 default 메서드를 포함할 수 있습니다.

</details>

<details>
    <summary>클래스는 무엇이고 객체는 무엇인가요?</summary>
</details>

<details>
    <summary>정적이란 무엇인가요?</summary>
</details>

<details>
    <summary>자바의 원시타입들은 무엇이 있으며 각각 몇 바이트를 차지하나요?</summary>
</details>

<details>
    <summary>접근 제어자의 종류와 이에 대해 설명해주세요.</summary>
</details>

<details>
    <summary>객체지향에 대해 설명해주세요.</summary>

<br/>

객체 지향이란 속성과 기능을 가진 클래스로 추상화시키고 클래스를 통해 객체라는 하나의 단위를 생성하여 객체끼리 상호작용을 통해 로직을 구성하는 것을 말한다.
객체 지향 프로그래밍은 상속, 추상화 , 캡슐화, 다형성 4가지 특징이 있다.

상속은 상위 클래스를 상속하여 하위 클래스로 확장하여 코드를 재사용 할 수 있다.
추상화는 공통된 속성 또는 기능을 하나로 묶어 하나의 상위 클래스로 만드는 것을 말한다.
캡슐화는 속성과 기능을 하나의 클래스로 정의하고 접근 제어자를 통해 정보를 필요에 따라 은닉 또는 노출할 수 있다.
마지막으로 다형성은 객체가 여러가지 타입을 가질 수 있음을 말한다.

<br/>

</details>

<details>
    <summary>SOLID(객체지향의 5대 원칙)에 대해 설명 해주세요.</summary>

<br/>

SOLID 원칙은 객체지향의 특징(추상화, 상속화, 다형성, 캡슐화)를 바탕으로 만들어진 것이다. 따라서, 코드의 재사용성을 높이며 유지 보수가 쉽고 불필요한 복잡성을 제거하여 개발의 생산성을 높일 수 있다.


| 약자  | 영어                              | 원칙          | 설명                                                                                                                        |
|-----|---------------------------------|-------------|---------------------------------------------------------------------------------------------------------------------------|
| SRP | Single Responsibility Principle | 단일 책임의 원칙   | 클래스는 단 하나의 책임만 가져야 한다. **_유지보수성_** 향상, 한 클래스는 하나의 기능을 가진다. (싱글톤 패턴)                                                       |
| OCP | Open Closed Principle           | 개방 폐쇄의 원칙   | 확장에는 열려 있고 수정에는 닫혀 있어야 한다. 기존의 코드를 변경하지 않고 기능을 수정 또는 추가할 수 있어야 한다. **_추상화**_ 함으로써 유연하게 확장시키는 것. 모듈간의 결햡도는 낮고,응집도는 높아야 한다. |
| LSP | Liskov Substitution Principle   | 리스코프 치환 원칙  | 서브타입(상속받은 자식객체)는 언제나 부모타입으로 교체할 수 있어야 한다. **_상속, 다형성과_** 관련된 원칙으로 업캐스팅된 상태에서 부모의 메서드를 사용할 수 있어야 한다.                       |
| ISP | Interface Segregation Principle | 인터페이스 분리 원칙 | 자신이 사용하지 않는 **_인터페이스_** 는 구현하지 말아야 한다. 객체 설계 시 특정 기능에 대한 인터페이스는 그 기능과 상관 없는 부분이 변해도 **_영향을 받지 않아야_** 한다.                  |
| DIP | Dependency Inversion Principle  | 의존 역전의 원칙   | 의존 관계를 맺을 때 변하기 쉬운 것 또는 자주 변하는 것 보다 변화가 자주 없는 것(추상클래스, 인터페이스)에 의존함으로써 **_관계를 느슨하게_** 만든다. 구체화된 클래스보다 추상화 클래스나 인터페이스에 의존해야 한다.   |

</details>
<br/>
<br/>

### 🐾 10월 13일

<details>
    <summary>통일성(identity)와 동등성(equality)에 대해 설명해주세요. (equals(), ==)</summary>
동등성은 두 객체가 완전히 같음을 의미한다, 기본 타입일 경우 값이 같음을, 객체일 경우는 주소값이 같음을 의미 한다.

동일성은 두 객체가 같은 정보를 같고 있음을 말한다 객체의 주소값이 다르더라도 참조하는 값이 같으면 두 객체는 동하다고 할 수있다
</details>

<details>
    <summary>원시타입과 참조타입의 차이에 대해 설명해주세요.</summary>


원시타입은 변수에 **실제 값을 저장**하는 데이터 타입으로 boolean, char, byte, short, int, long, float, double 형이 있습니다. 이 데이터 타입은 **stack 영역에 저장**되며 변수의 선언과 동시에 메모리를 생성한다는 특징이 있습니다.

참조형 타입은 이름처럼 주소를 “참조”하는 타입으로 8가지 원시타입 데이터를 제외한 모든 데이터 타입을 말 합니다. 참조형 데이터 타입은 저장된 공간의 주소를 저장할 수 있습니다. 메모리의 **heap영역에 주소값을 저장**하는 형태입니다.

✅ 원시 타입은 null 값을 가질 수 없다.

✅ 원시타입 boolean 1, char 2, byte 1, short 2, int 4, long 8, float 4, double 8  바이트를 가집니다.

🔗 https://luminousolding.tistory.com/56

</details>

<details>
    <summary>String, String Builder, String Buffer 각각의 차이에 대해 설명해주세요.</summary>
	String은 불변성, StringBuilder와 Buffer는 가변성이라는 차이점이 있다.

String은 문자열을 수할 때 객체가 변하는 것이 아니라 새로운 문자열 객체를 생성하여 많이 결합할 수록 공간의 낭비가 생기고 속도가 느려진다.

![img1 daumcdn (1)](https://github.com/codestates-seb/seb45_main_006/assets/129938243/98261796-4fa0-41af-95df-c503b4f83ebb)

하지만 StringBuilder 와 Buffer는 버퍼라는 독립적인 공간을 가지고 있어 문자열을 수정할 수 있다

![img1 daumcdn (2)](https://github.com/codestates-seb/seb45_main_006/assets/129938243/1a8061d0-1482-498b-9f9a-fbd8e0793460)


동등성 비교에서는 == 는 다른 객체와 똑같지만 버퍼와 빌더는 equals 로 비교하려면 String 객체로 바꾼 후 비교를 해야한다. 바꾸지 않으면 == 비교와 같은 결과가 나온다

버퍼는 동기화를 지원하지만 빌더는 동기화를 지원하지 않는다.

→ 버퍼는 synchronized 키워드가 붙어 있어서 멀티 스레드에서도 안전하게 동작이 가능하다

→ 버퍼와 빌더를 append 로 1만번 문자열을 붙이면 버퍼는 동기화가 잘 되어 1만번 제대로 붙지만 빌더는 동기화가 잘 되지 않아 append 가 제대로 수행되지 않는 경우가 있다.

결론 : 문자열을 자주 변경하지 않을 경우 String, 문자열을 자주 수정하고 멀티 스레드일경우 StringBuffer, 문자열을 자주 수정하고 동기화를 고려하지 않으며 속도가 더 빠른 것을 원할때 StringBuilder 를 사용하는 것이 좋다
</details>

<details>
    <summary>Checked Exception과 Unchecked Exception에 대해 설명해주세요, 스프링 트랜잭션 추상화에서 rollback 대상은 무엇일까요?</summary>
에러는 복구할 수 없는 오류

예외는 복구할 수 있는 수준의 오류를 말한다. 

CkeckedExcetpion은 단어 그대로 확인해야할 예외이다.

RuntimeException을 상속 받지 않으며 대표적으로 IOException, SQLException 등이 있고 예외 처리를 하지 않으면 컴파일 에러가 생긴다 

UnCheckedException은 RuntimeException을 상속 받으며 컴파일러가 예외처리를 강제하지 않는다.

대표적으로 NPE, illegalArgumentException 등이 있다. 

예외처리를 강제하지 않기 때문에 예외를 누락할 수 도 있다.

그리고

스프링 프레임워크에서 제공하는 @Transcational 애너테이션안에서 에러가 발생 시 체크 예외는 롤백이되지 않지만 언체크 예외는 롤백이 된다는 차이점이 있다.

예외를 처리하는 것이 좋을 것 같은데 언체크 예외가 필요한 이유?

모든 예외를 처리하기는 번거롭고, 불필요한 의존관계가 생기때문

→ 예로 SQLException은 Repository에서 데이터에 접근할 때 생길 수 있는 에러이며 SQL 문법으로 인한 오류이다. 이 오류를 처리할만한 곳이 마땅히 없이 상위로 계속 예외를 던지다 보니 Controller 까지 예외가 전달되게 된다. 이렇게 되면 Controller가 Repository를 의존하게 된다.
</details>

<details>
    <summary>try-with-resource 에 대해 설명해주세요.</summary>


"try-with-resource"는 자원 관리를 간편하게 해주는 기술로 Java 7 이후 도입된 기술입니다. 
(Java 7) 이전에는 파일과 같은 외부 리소스를 이용 후 꼭 닫아줘야 했는데 개발자가 직접 닫아주는 것은 가독성에도 좋지 않고 실수로 닫지 않을 수 있는 경우도 발생할 수 있습니다. 
이를 막기 위해 "try-with-resource"문을 사용할 수 있습니다.


력에 사용한 객체를 자동으로 반환시켜주기 때문에 입출력과 관련된 클래스를 사용할 때 매우 유용합니다. 
<pre>
try (리소스 선언 명령문) {
     ...
} 
</pre>
"try-with-resource"문의 기본 문법 구조는 try 블록 내부에서 리소스를 선언하면 try 블록이 종료될 때 자동으로 닫히는 형태입니다. 이렇게 "try-with-resource"를 사용함으로써 파일 누수, 메모리 누수를 방지할 수 있습니다.


🔗 [The try-with-resources Statement](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html) <br/>
🔗 [자바 Try With Resource 예외 처리](https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC-Try-With-Resource-%EB%AC%B8%EB%B2%95) <br/>
🔗 [[Java] try-with-resources란? try-with-resources 사용법 예시와 try-with-resources를 사용해야 하는 이유](https://mangkyu.tistory.com/217)

</details>

<details>
    <summary>강한 결합과 느슨한 결합이 무엇인지 설명해주세요.</summary>
</details>

<details>
    <summary>직렬화와 역직렬화에 대해 설명해주세요.</summary>
</details>

<details>
    <summary>자바의 동시성 이슈(공유자원 접근)에 대해 설명해주세요.</summary>


동시성 이슈는 멀티 스레딩 환경에서 여러 스레드가 동일한 자원을 공유하여 사용할 때 발생하는 문제로 좋아요가 count 되는 것을 예시로 들 수 있습니다.
게시글의 좋아요가 0인 상태에서 n명의 회원이 동시에 좋아요를 누른다면 n개의 좋아요가 더해져야 합니다. 하지만 1개의 좋아요만 추가되는 것과 같은 문제가 발생했을 때 동시성 문제 발생이라고 합니다. 


<details>
<summary>
동시성 문제를 해결하기 위한 방법
</summary>

✅ 암시적 Lock
- synchronized 키워드를 사용하여 특정 메서드나 코드 블록에 대한 동시 접근을 제한
- 한 번에 하나의 스레드만 접근이 가능하므로 병렬성은 매우 떨어짐
<pre>
class Main {
    private int i;
    public synchronized int view() {return i++;}
}
</pre>


✅ 명시적 Lock
- 복잡한 시나리오에 유용하며 ReentrantLock 같은 명시적 락 사용
- 시간 제한 두고 락 획득 시도, 여러 조건 변수 사용 등


✅ 가시성 문제
- volatile 키워드를 사용하여 CPU 캐시가 아닌 메인 메모리에서 읽고 씀
- 'vilatile' 은 원자성을 보장하지 않음
- 복합 연산에서는 적합하지 않음
- 하나의 스레드가 wtite를 하고 다른 하나의 스레드가 read만 할 경우 유용


✅ thread-safe 객체 사용
- Concurrent 패키지 자료구조는 멀티스레드 환경에서 안전하다


✅ 불변 객체 사용
- 생성 후 그 상태가 절대 변하지 않는 객체
- 데이터 불일치 문제가 발생하지 않음
- 모든 필드를 'final'로 선언, setter X


🔗 [[Java] Thread/MultiThread 4 - 동시성 문제](https://llshl.tistory.com/12) <br/>
🔗 [[Java] Java의 동시성 이슈](https://steady-coding.tistory.com/554)

</details>



</details>

<details>
    <summary>Mutable(가변 객체)와 Imutable(불변 객체)의 차이점에 대해 설명해주세요.</summary>
Mutable은 가변 객체 Immutable은 불변 객체이며 가변 객체는 말 그대로 객체가 변할 수 있음을 말하고
예시로는 StringBuilder StringBuffer 가 있다 불변 객체는 객체가 변하지 않음을 말하고 예시는 String 이 있다.
</details>

<details>
    <summary>자바에서 null을 안전하게 다루는 방법에 대해 설명해주세요.</summary>

‘**NullPointerException**’은 자주 마주치는 예외이기 때문에 null을 다루는 것은 매우 중요한 이슈입니다.

1. if 문을 써서 null을 체크 합니다.
2. Optional 클래스를 사용하여 null일 경우 연산을 수행합니다.
3. @Nullable, @NotNull 등과 같은 어노테이션을 사용하여 유효성 검사를 진행합니다.
4. 이외에도 설계 시 null 값을 반환하지 않는 것과 같은 설계 원칙을 따를 수 있습니다.

</details>

<details>
    <summary>JDK와 JRE의 차이점?</summary>
</details>

<details>
    <summary>두 객체가 동일한 hashCode를 가지면 Equals()의 값은 어떻게 되어야 하는가?</summary>
</details>

<details>
    <summary>자바에서 final의 기능은?</summary>
</details>

<details>
    <summary>자바에서 Math.round(1.5)는 무엇을 의미하는가?</summary>
</details>

<details>
    <summary>자바에서 문자열을 조작하는 클래스는 무엇이 있으며 각 클래스의 차이점은 무엇인가?</summary>
</details>

<details>
    <summary>리터럴로 생성한 String 변수와 new 연산자로 생성한 String 의 차이점?</summary>
</details>

<details>
    <summary>문자열을 반전시키는 가장 좋은 방법은?</summary>
</details>

<details>
    <summary>String 클래스의 일반적인 메서드는 무엇이 있나요?</summary>
</details>

<details>
    <summary>추상 클래스에서 추상 메서드는 필수적인가?</summary>
</details>

<details>
    <summary>보통 클래스와 추상 클래스의 차이?</summary>
</details>

<details>
    <summary>final 은 추상 클래스를 수정할 때 사용이 가능한가?</summary>
</details>

<br/>
<br/>
