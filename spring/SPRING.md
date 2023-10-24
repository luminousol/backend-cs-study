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
<hr/>
<br/>
스프링에서는 제어권을 역전하여 객체의 생성을 스프링 프레임 워크에서 담당하게 됩니다. 사용자는 new 생성자를 이용하지 않고 스프링에 의해 관리 당하는 자바 객체를 사용하게 됩니다. 

이 객체를 **스프링 빈(bean)** 이라고 부릅니다. 빈 객체는 스프링 IoC 컨테이너에 의해 초기화, 생성, 소멸 등의 관리를 받고 의존성 주입을 통해 다른 빈이나 스프링 컴포넌트들과 상호작용할 수 있습니다. 이를 통해 느슨한 결합을 가능하게 합니다.


</details>

<details>
<summary>
스프링 Bean의 생성 과정을 설명해주세요.
</summary>
<hr/>
<br/>
스프링 컨테이너는 빈 객체 생성 → 의존 관계 주입 → 초기화 → 소멸 단계의 생명 주기를 가지고 있습니다. 

Bean은 스프링 컨테이너에 의해 생명주기를 관리하며 **빈 초기화방법은 @PostConstruct** 를 **빈 소멸**에서는 **@PreDestroy** (종료 콜백) 를 사용합니다.

생성한 스프링 빈을 등록할 때는 ComponentScan을 이용하거나 @Configuration 의 @Bean 을 사용하여 빈 설정파일에 직접 빈을 등록할 수 있습니다.


</details>

<details>
<summary>
스프링 Bean의 Scope에 대해서 설명해주세요.
</summary>
<hr/>
<br/>

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
<hr/>
<br/>

![image](https://github.com/luminousol/backend-cs-study/assets/130022922/a284382e-64da-46b2-95f2-1025655004dc)


**프론트 컨트롤러 패턴(Front Controller Pattern)** 은 웹 애플리케이션의 디자인 패턴 중 하나로, 중앙의 컨트롤러가 모든 HTTP 요청을 받아서 적합한 컨트롤러에 위임하는 역할을 합니다. 

모든 요청은 먼저 프론트 컨트롤러를 거치게 되므로, 공통 처리 로직(인증, 로깅, 세션 관리 등)을 프론트 컨트롤러에서 수행할 수 있습니다. 

프론트 컨트롤러는 요청을 알맞은 핸들러나 컨트롤러로 전달(디스패치)합니다. 이를 통해 애플리케이션의 **흐름을 중앙에서 관리** 할 수 있습니다.

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

<br/>

![img1 daumcdn (5)](https://github.com/codestates-seb/seb45_main_006/assets/129938243/7955d55e-ae41-414b-8f6b-fb428547f27a)
서블릿 필터란 요청이 들어왓을 때 Dispacher Servlet 에 전달되기 전 또는 후에 URL 패턴에 부가적인 작업을 처리할 수 있는 기능이다.

필터는 웹 Context 등록되고

**요청 → WAS → 필터 1~N → 서블릿 → 컨트롤러** 순으로 처리되고 Filter 인터페이스를 사용하여 구현한다

<pre>
java
public interface Filter {

    public default void init(FilterConfig filterConfig) throws ServletException {}
    

// 이 메서드를 오버라이딩하여 구현
    public void doFilter(ServletRequest request, ServletResponse response,
            FilterChain chain) throws IOException, ServletException;
// 자원 반환
    public default void destroy() {}

}
</pre>

필터는 공통 로깅, 인증, 인가 등 에 사용한다

![img1 daumcdn (7)](https://github.com/codestates-seb/seb45_main_006/assets/129938243/3c15fef4-2bb6-447f-8787-4b4de493c146)

인터셉터는 스프링 MVC 가 제공하는 기능으로 Dispatcher Serlvet와 Controller 호출 전에 호출 된다.
인터셉터는 스프링 Context에 등록되며

**HTTP 요청 -> WAS -> 필터 -> 서블릿 -> 스프링 인터셉터1 ~ N -> 컨트롤러**

순으로 호출되고 HandlerInterceptor로 구현한다.

<pre>
java
public interface HandlerInterceptor 

//  boolean으로 반환되면 계속 진행 false면 멈춤(컨트롤러 호출 전)
    default boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler)
	throws Exception {
        return true;
    }
// HaddlerAdaptor 호출 후 실행(컨틀롤러 호출 후)    
    default void postHandle(HttpServletRequest request, HttpServletResponse response,
	Object handler, @Nullable ModelAndView modelAndView) throws Exception {
    }
-> 하위에서 예외가 발생하면 호출하지 않음
-> JSON 형태 데이터를 쓰는 RestController에선 잘 사용안

// 요청이 완료된 후 실행(뷰 렌더링 후 실행)        
    default void afterCompletion(HttpServletRequest request, HttpServletResponse response,
	Object handler, @Nullable Exception ex) throws Exception {
    }
-> 하위에서 예외가 생겨도 반드시 호출
}
</pre>

둘의 차이점
![img1 daumcdn (6)](https://github.com/codestates-seb/seb45_main_006/assets/129938243/1de2c2bb-7192-4f29-9e63-b1b4a433f549)

결론적으로 필터는 특정 요청과 컨트롤러에 관계 없이 전역적으로 처리하는 작업,

웹 어플리케이션 전반적으로 사용되는 기능을 구현할 때 적용하고

인터셉터는 클라이언트의 요청과 관련된 작업에 대해 추가적인 요구사항을 만족해야 할 때 적용한다.
</details>


<details>
<summary>
Spring에서 CORS 에러를 해결하기 위한 방법을 설명해주세요.
</summary>

<br/>

먼저 SOP(Same Origin Policy)란 어떤 출처(Origin)에서 불러온 문서나 스크립트가 다른 출처에서

가져온 리소스와 상호작용하는 것을 제한하는 보안 방식

두 객체의 프로토콜, 호스트, 포트가 모두 일치하면 같은 출처를 가졌다고 말함

HTTP, HTTPS 포트는 생략 가능 / 80과 443

출처(Origin)은 URL에서 프로토콜, 호스트, 포트를 합친 것을 의미

| URL | 결과 | 이유 |
| --- | --- | --- |
| http://example.com/app1/index.htmlhttp://example.com/app2/index.html | 동일 출처 | 프로토콜(http)와 호스트(example.com) 일치 |
| http://Example.com:80  http://example.com | 동일 출처 | HTTP의 기본 포트는 80이므로 생략가능 하기에 동일 출처(대소문자는 동일한 것으로 간주) |
| http://example.com/app1 https://example.com/app2 | 다른 출처 | 서로 프로토콜(http, https)가 다름 |
| http://www.example.com http://myapp.example.com | 다른 출처 | 서로 호스트가 다름 |
| http://example.com http://example.com:8080 | 다른 출처 | 서로 포트가 다름 |

domainA/pg2라는 페이지에서는 이전 페이지인 domainA/pg라는 페이지는 같은 출처이기 때문에

동일한 로그인 정보를 가지고 서비스를 이용할 수 있지만 domainB/pg는 다른 출처이기 때문에

잘못된 결과를 초래할 수 있음

→ 여기서 SOP가 기능을 발휘

1. domainA 에서 요청(domainB)의 출처(Origin)을 확인
2. domainB의 요청이기 때문에 domainA과 다른 출처 즉 cross origin이라 판단
3. domainB의 요청을 받아들이지 않음

만약 다른 출처 리소스가 필요하다면? CORS를 사용

CORS는 다른 출처의 자원을 공유함

추가적인 HTTP 헤더를 사용하여 출처에서 실행 중인 웹 어플리케이션의 **다른 출처**의

선택한 자원에 **접근할 수 있는 권한**을 부여함

![img1 daumcdn (8)](https://github.com/codestates-seb/seb45_main_006/assets/129938243/dffece9f-b311-4d21-8d0b-995e4e96b8dc)
![img1 daumcdn (9)](https://github.com/codestates-seb/seb45_main_006/assets/129938243/4665476c-46ec-42a1-9455-806c22d58b94)

CORS를 해결하기 위해서는

<pre>
java
 @Bean
    CorsConfigurationSource corsConfigurationSource() {
        CorsConfiguration configuration = new CorsConfiguration();
        configuration.setAllowedOrigins(Arrays.asList("URL"));

        UrlBasedCorsConfigurationSource source = new UrlBasedCorsConfigurationSource();
        source.registerCorsConfiguration("/**", configuration);

        return source;
    }
</pre>

이 예시는 스프링시큐리티 인데 CorsConfigurationSource 에 CORS 설정을 하고 빈으로 등록하면 해당 URL에 대한 CORS가 가능해진다.

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
<hr/>
<br/>

POJO(Plain Old Java Object)란 객체 지향적 원리에 충실하면서 
**환경과 기술에 종속되지 않고 필요에 따라 재활용 가능**한 확장에 제한이 없는 자바 오브젝트를 의미합니다.

SPRING에서는 **도메인과 비즈니스 로직을 수행하는 객체**, DTO, 
컨테이너에 의해 관리되는 오브젝트들, 레포지토리와 DAO 클래스(서비스 클래스)가 POJO의 대상이 될 수 있습니다.

스프링 프레임워크에서는 POJO의 사용으로 개발자들은 비즈니스 로직에 
더욱 집중할 수 있으며 테스트 용이성을 높이고 코드의 유지 보수성 또한 높일 수 있습니다.

</details>

<details>
<summary>
Spring Web MVC에서 요청 마다 Thread가 생성되어 Controller를 통해 요청을 수행할텐데, 어떻게 1개의 Controller만 생성될 수 있을까요?
</summary>
<hr/>
<br/>

스프링 Web MVC 에서 컨트롤러가 하나만 생성되는 이유는 **Bean과 Scope(범위)** 때문입니다.

스프링 프레임워크는 IoC 컨테이너를 통해 애플리케이션의 객체 생명주기와 의존성을 관리하는데 
컨테이너 내에서 객체는 **Bean**으로 정의되며 이 Bean들은 다양한 **Scope**를 가질 수 있습니다.

기본적으로 스프링에서 모든 빈은 **싱글톤 스코프**를 가지는데 컨테이너당 
Bean 인스턴스 하나만 생성되는 것으로 요청 시 동일한 인스턴스를 반환하는 것을 말합니다. 
따라서 하나의 Controller가 정의되면 **하나의 인스턴스만 생성하**고 
이후 모든 요청에 대해 **같은 Controller 인스턴스를 재사용**하게 됩니다.

싱글톤 스코프와 Spring MVC 컨트롤러의 상태를 갖지 않는 특징(멤버 변수가 없거나, 있는 경우에도 읽기 전용 이거나 스레드로부터 안전한 객체를 참조)때문에 
동시에 여러 요청이 처리 되어도 컨트롤러 상태에 대한 경쟁조건이 발생하지 않음을 보장합니다. 
→ S**pring MVC 컨트롤러의 thread-safe 한 설계**로 인해 모든 요청이 동일한 인스턴스를 안전하게 통과할 수 있음

</details>

<details>
<summary>
Filter는 Servlet의 스펙이고, Interceptor는 Spring MVC의 스펙입니다. Spring Application에서 Filter와 Interceptor를 통해 예외를 처리할 경우 어떻게 해야 할까요?
</summary>

<br/>

필터는 DispatcherServlet 외부에 존재하기 스프링의 도움을 받지 못해 예외가 발생했을 때 ErrorController에서 처리해야 한다.

만약 필터에서 MemberNotFoundException이 던져졌다면, 에러가 처리되지 않고 Dispatcher Servlet까지 전달된다. 서블릿은 예외가 핸들링 되기를 기대했지만, 
예외가 그대로 올라와서 예상치 못한 Exception을 만난 상황이다.
-> 따라서 내부에 문제가 있다고 판단하여 500 Status로 응답을 반환한다.
-> 이를 해결하려면 필터에서 다음과 같이 응답(Response) 객체에 예외 처리가 필요하다.

<pre>
java
public class MyFilter implements Filter {

    @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws IOException, ServletException {
        HttpServletResponse servletResponse = (HttpServletResponse) response;
        servletResponse.setStatus(HttpServletResponse.SC_NOT_FOUND);
        servletResponse.getWriter().print("Member Not Found");
    }
}
</pre>>
    
인터셉터는 DispatcherServlet 내부에, Spring Context에 존재하기 때문에 @ControllerAdvice, @ExceptionAdvice 등 적용해서 처리할 수 있다.
예
<pre>
java
@RestControllerAdvice
public class GlobalExceptionAdvice {
    @ExceptionHandler
    public ResponseEntity handleBusinessLogicException(BusinessLogicException e) {
        final ErrorResponse response = ErrorResponse.of(e.getExceptionCode());

        return new ResponseEntity<>(response, HttpStatus.valueOf(e.getExceptionCode().getStatus()));
    }
}
</pre>
</details>

<details>
<summary>
Spring Application을 구동할 때 메서드를 실행시키는 방법에 대해 설명해주세요.
</summary>
<hr/>
<br/>

Spring Application을 구동할 때 특정 메서드를 실행하고자 할 때 다양한 방법이 있습니다.

**Command Line Runner & Application Runner**
    
<details>
<summary>
Spring Application이 시작된 후에 특정 코드를 실행하고 싶을 때 사용됩니다. 
두 인터페이스 모두 ‘run’ 메서드를 오버라이드 하여 사용합니다
</summary>

- ApplicationRunner는 ApplicationArguments를 인자로 받아들이는 반면, CommandLineRunner는 Java의 일반적인 String[] args를 인자로 받습니다.
- 컴포넌트로 선언하고 필요한 의존성을 주입하여 사용할 수 있습니다..

<pre>
@Component
public class MyRunner implements CommandLineRunner {

    @Override
    public void run(String... args) {
        // 실행하고 싶은 코드
    }
}
</pre>
</details>

**@EventListener**
<details>
<summary>
ApplicationContext가 초기화되거나 새로고침될 때 발생하는 이벤트를 처리하고 싶을 때 사용됩니다.
</summary>

- 애플리케이션이 완전히 시작된 후에 코드를 실행해야 할 필요가 있을 때 유용합니다.
<pre>
@Component
public class MyStartupRunner {

    @EventListener
    public void onApplicationEvent(ContextRefreshedEvent event) {
        // 실행하고 싶은 코드
    }
}
</pre>

- 이 이벤트는 Spring 애플리케이션이 시작된 후 발행됩니다.
<pre>
@Component
public class MyStartupRunner {

    @EventListener(ApplicationReadyEvent.class)
    public void doSomethingAfterStartup() {
        // 실행하고 싶은 코드
    }
}
</pre>
</details>

**@Scheduled**
<details>
<summary>
@Scheduled 애노테이션을 사용하면, 정해진 시간이나 간격으로 특정 코드를 실행할 수 있습니다.
</summary>

- 주기적으로 실행되어야 하는 코드가 있을 때 유용합니다.
<pre>

@Service
@AllArgsConstructor
public class LicenseNotificationService {
    private final MemberRepository memberRepository;
    private final EmailService emailService;
    @Scheduled(cron = "0 0 15 * * ?")   // 매일 오후 세시에 스케줄러 실행
    public void sendNotificationForUpcomigEvent() throws MessagingException {
        List<Member> members = memberRepository.findAll();
        for (Member member : members) {
            handleMemberNotification(member);
        }
    }
}
</pre>
</details>

**@PostConstruct**
<details>
<summary>
@PostConstruct 애노테이션이 붙은 메서드는 해당 빈 객체의 초기화가 완료된 후에 자동으로 실행됩니다.
</summary>
<pre>
**@Component**
public class JwtTokenizer {
    @Getter
    private int accessTokenExpirationMinutes;
    @PostConstruct
    public void init() {
        this.accessTokenExpirationMinutes = this.originMinutes * 6;
    }
}
</pre>
</details>

**InitializingBean 인터페이스 구현**
<details>
<summary>
InitializingBean 인터페이스를 구현하고 afterPropertiesSet 메서드를 오버라이드하여, 
빈 객체의 프로퍼티 설정이 완료된 후에 실행할 작업을 정의할 수 있습니다.
</summary>
<pre>
@Component
public class MyBean implements InitializingBean {
    @Override
    public void afterPropertiesSet() {
        // 프로퍼티 설정 후 실행할 코드
    }
}
</pre>
</details>

**@Bean의 initMethod**
<details>
<summary>
@Bean 애노테이션을 사용하여 빈을 생성할 때 initMethod 속성을 사용하면, 
해당 빈 객체 생성 시점에 호출할 초기화 메서드를 지정할 수 있습니다.
</summary>
<pre>
@Configuration
public class MyConfiguration {
    @Bean(initMethod = "init")
    public MyBean myBean() {
        return new MyBean();
    }
}

public class MyBean {
    public void init() {
        // 빈 초기화 시 실행할 코드
    }
}
</pre>
</details>
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

<br/>

1차 캐시 :
영속성 컨텍스트는 엔티티 객체를 보관해서 동일한 엔티티를 여러 번 조회해야 할 때, 데이터베이스에서 가져오지 않고
1차 캐시에서 가져와서 효율이 좋다

지연 로딩 :
영속성 컨텍스트는 지연 로딩을 지원하여 연관 엔티티를 실제로 필요로 할 때만 DB에서 가져오도록 해서
필요한 쿼리만 실행도록 한다.

변경 감지 :
영속성 컨텍스트에서 스냅샷을 만들고 엔티티의 변경 사항을 감지한다. 만약 변경 사항이
DB로 commit 될 때 스냅샷과 비교하여 update를 알아서 생성하여 반영한다

쓰기 지연 :
트랜잭션을 지원하는 쓰기 지연 SQL 저장소 commit이 되기 전엔 SQL을 모아두고 commit 될 때 한 번에
SQL을 보내어 DB에 접근하는 횟수와 한 테이블이 DB에 접근하는 시간이 줄어 최적화가 할 수 있다.

일관성 유지:
영속성 컨텍스트는 엔티티의 상태를 일관하게 유지한다. 관리하는 모든 엔티티의 상태를 트랜잭션 단위로 일관되게 유지하고, 롤백 기능을 제공하여 데이터베이스와 애플리케이션 간의 일관성을 보장한다.
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



