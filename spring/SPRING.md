# SPRING

<details>
<summary>
Spring DI/IoC는 어떻게 동작하나요?
</summary>
</details>

<details>
<summary>
Spring Bean이란 무엇인가요?
</summary>


스프링에서는 제어권을 역전하여 객체의 생성을 스프링 프레임 워크에서 담당하게 됩니다. 사용자는 new 생성자를 이용하지 않고 스프링에 의해 관리 당하는 자바 객체를 사용하게 됩니다. 

이 객체를 **스프링 빈(bean)**이라고 부릅니다. 빈 객체는 스프링 IoC 컨테이너에 의해 초기화, 생성, 소멸 등의 관리를 받고 의존성 주입을 통해 다른 빈이나 스프링 컴포넌트들과 상호작용할 수 있습니다. 이를 통해 느슨한 결합을 가능하게 합니다.


</details>

<details>
<summary>
스프링 Bean의 생성 과정을 설명해주세요.
</summary>


스프링 컨테이너는 **“빈 객체 생성 → 의존 관계 주입 → 초기화 → 소멸”** 단계의 생명 주기를 가지고 있습니다. 

Bean은 스프링 컨테이너에 의해 생명주기를 관리하며 **빈 초기화방법은 @PostConstruct** 를 **빈 소멸**에서는 **@PreDestroy** (종료 콜백) 를 사용합니다.

생성한 스프링 빈을 등록할 때는 ComponentScan을 이용하거나 @Configuration 의 @Bean 을 사용하여 빈 설정파일에 직접 빈을 등록할 수 있습니다.


</details>

<details>
<summary>
스프링 Bean의 Scope에 대해서 설명해주세요.
</summary>


빈스코프란 빈이 존재할 수 있는 범위를 의미합니다. 

각 범위 및 생성 관리 방식에 따라 종류가 나누어 지며 총 여섯가지의 스코프가 있습니다.

- **Singleton** - 기본 스코프로, 각각의 IoC 컨테이너당 Bean 인스턴스 하나만 생성됩니다. 따라서, 요청 시 동일한 인스턴스를 반환하는 것이 특징입니다. 
✨ GOF 패턴의 싱글톤 패턴과는 다른 것
- **Prototype** - 클라이언트가 요청할 때 마다 새로운 Bean 인스턴스가 생성됩니다. 즉, 빈이 다른 빈에 주입되거나 getBean() 메서드를 통해 요청합니다. Stateful Bean(요청이 독립적인 환경)에는 프로토타입 스코프를 사용해야 하고 Stateless Bean(상태 공유가 허용되지 않을 때)에는 싱글톤 스코프를 사용해야 합니다.
    
    [+) 프로토 타입 + 싱글톤 타입](https://docs.spring.io/spring-framework/reference/core/beans/factory-scopes.html#beans-factory-scopes-sing-prot-interaction)
    
- **Web Scope** - 웹 환경에서만 동작하는 형태입니다.
    - request - 각 HTTP 요청이 생성될 때마다 Bean이 생성되고, 해당 요청이 끝날 때 소멸합니다. 각각의 HTTP 요청마다 별도의 빈 인스턴스가 생성되고 관리됩니다.
    - session - Bean은 HTTP 세션당 하나씩 생성되고, 세션 종료시 소멸합니다.
    - application - 서블릿 컨텍스트 당 하나의 Bean 인스턴스를 생성하여 서블릿 컨텍스트와 동일한 생명주기를 가집니다. 이는 전체 웹 애플리케이션에서 동유됩니다.
    - web socket - websoket 세션당 하나의 Bean 인스턴스를 유지합니다.

🔗 https://docs.spring.io/spring-framework/reference/core/beans/factory-scopes.html#beans-factory-scopes-sing-prot-interaction

</details>

<details>
<summary>
IoC 컨테이너의 역할은 무엇이 있을까요?
</summary>
</details>

<details>
<summary>
DI 종류는 어떤것이 있고, 이들의 차이는 무엇인가요?
</summary>
  
</details>

<details>
<summary>
Autowiring 과정에 대해서 설명해주세요.
</summary>  
</details>

<details>
<summary>
프론트 컨트롤러 패턴이란 무엇인가요?
</summary>

![image](https://github.com/luminousol/backend-cs-study/assets/130022922/a284382e-64da-46b2-95f2-1025655004dc)


**프론트 컨트롤러 패턴(Front Controller Pattern)** 은 웹 애플리케이션의 디자인 패턴 중 하나로, 중앙의 컨트롤러가 모든 HTTP 요청을 받아서 적합한 컨트롤러에 위임하는 역할을 합니다. 

모든 요청은 먼저 프론트 컨트롤러를 거치게 되므로, 공통 처리 로직(인증, 로깅, 세션 관리 등)을 프론트 컨트롤러에서 수행할 수 있습니다. 

프론트 컨트롤러는 요청을 알맞은 핸들러나 컨트롤러로 전달(디스패치)합니다. 이를 통해 애플리케이션의 **흐름을 중앙에서 관리**할 수 있습니다.

프론트 컨트롤러는 처리 결과에 따라 적절한 뷰를 선택하고 응답을 구성할 수 있습니다.

모든 요청 처리 중 발생하는 예외를 **중앙에서 관리**하고 적절한 응답을 제공할 수 있습니다.

프론트 컨트롤러 패턴의 예로는 Java의 Spring Framework의 **DispatcherServlet** 이나 Java EE의 **Servlet** 등이 있습니다. 이들은 웹 애플리케이션에서 모든 요청을 초기에 받아들이고 적절한 컨트롤러나 핸들러로 요청을 전달하는 역할을 합니다.


</details>

<details>
<summary>
Spring Web MVC의 Dispatcher Servlet의 동작 원리에 대해서 간단히 설명해주세요.
</summary>
</details>

<details>
<summary>
Servlet Filter와 Spring Interceptor의 차이는 무엇인가요?
</summary>
</details>

<details>
<summary>
Spring에서 CORS 에러를 해결하기 위한 방법을 설명해주세요.
</summary>
</details>

<details>
<summary>
Bean/Component 어노테이션에 대해서 설명해주시고, 둘의 차이점에 대해 설명해주세요.
</summary>
</details>

<details>
<summary>
POJO란 무엇인가요? Spring Framework에서 POJO는 무엇이 될 수 있을까요?
</summary>
</details>

<details>
<summary>
Spring Web MVC에서 요청 마다 Thread가 생성되어 Controller를 통해 요청을 수행할텐데, 어떻게 1개의 Controller만 생성될 수 있을까요?
</summary>
</details>

<details>
<summary>
Filter는 Servlet의 스펙이고, Interceptor는 Spring MVC의 스펙입니다. Spring Application에서 Filter와 Interceptor를 통해 예외를 처리할 경우 어떻게 해야 할까요?
</summary>
</details>

<details>
<summary>
Spring Application을 구동할 때 메서드를 실행시키는 방법에 대해 설명해주세요.
</summary>
</details>

<details>
<summary>
의존성과 설정값을 생성자 인자로 주입해야 하는 이유에 대해 설명해주세요.
</summary>
</details>

## JPA

<details>
<summary>
JPA 영속성 컨텍스트의 이점(5가지)을 설명해주세요.
</summary>
</details>

<details>
<summary>
JPA Propagation 전파단계를 설명해주세요.
</summary>
</details>

<details>
<summary>
JPA를 쓴다면 그 이유에 대해서 설명해주세요.
</summary>
</details>

<details>
  <summary>
    N + 1 문제는 무엇이고 이것이 발생하는 이유와 이를 해결하는 방법을 설명해주세요.
  </summary>
</details>


## SECURITY


