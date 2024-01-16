# NETWORK

1. [네트워크 기초](https://polydactyl-impala-301.notion.site/4a0f54a2586f469e9f28dd663395e5e4?pvs=4) - 주연
2. [대역폭](https://luminousol.notion.site/Bandwidth-8e83c1a00ba54719a73162bc649e1f82?pvs=4) - 솔이
3. [OSI 7계층](https://polydactyl-impala-301.notion.site/OSI-7-7d75e296ab314295a07e98b8f0b3294a?pvs=4) - 주연
4. [TCP 의 연결 및 해제 과정 (3, 4 - way hands shanking)](https://luminousol.notion.site/TCP-3-4-way-hands-shanking-d3af9e023b8046a3bcb1f4619d714692?pvs=4) - 솔이
5. [DNS + 웹 통신 흐름](https://polydactyl-impala-301.notion.site/DNS-e386fde72242427da4561a298f5a5e53?pvs=4) - 주연
6. [네트워크 기기](https://luminousol.notion.site/e391867b84c64469a29af3dba9ba1ae9?pvs=4) - 솔이
7. [L7, L4 스위치 + 로드 밸런싱](https://polydactyl-impala-301.notion.site/L7-L4-d978833d093247ccb3047a412148f1c6?pvs=4) - 주연
8. [HTTP 진화과정](https://www.notion.so/ehdals0405/HTTP-568841a8c7c14c66aaaab759dcd3c27d) - 동민
9. [HTTPS](https://www.notion.so/ehdals0405/HTTPS-967faa46cfc1405f9ab904a9e0fa62db) - 동민
10. [REST API + RESTful](https://luminousol.notion.site/REST-API-RESTful-6aabca3f94ae48caac8b1205f7654d5d?pvs=4) - 솔이
11. [쿠키와 세션](https://www.notion.so/ehdals0405/Cookie-Session-bfbcfdbc56334cf8b4aa47785fe748a8#d59f064fe53a4ee99a4f08fcb8e23be7)  - 동민
12. [프록시 서버](https://www.notion.so/ehdals0405/e8c818253c1242169567427e43287f59) - 동민

<br/>
<br/>

## 면접 질문 ❓
<details>
<summary>
웹 통신의 큰 흐름: https://www.google.com/ 을 접속할 때 일어나는 일
</details>
</summary>

<hr/>
💬 "[https://www.google.com/"을](https://www.google.com/%22%EC%9D%84) 웹 브라우저에 입력하고 엔터를 누르면 일반적으로 다음과 같은 일련의 과정이 발생합니다.

- **DNS 질의**: 브라우저가 DNS 서버에 "[www.google.com"과](http://www.google.xn--com"-ei4p/) 연관된 IP 주소를 찾습니다.
- **TCP 연결**: 브라우저는 IP 주소를 사용하여 Google 서버와 TCP 연결을 엽니다.
- **HTTPS 보안 연결**: URL이 "https://"로 시작하기 때문에, 브라우저와 Google 서버는 SSL/TLS 암호화를 사용하여 보안 연결을 설정하기 위한 인증서를 교환합니다.
- **HTTP 요청**: 브라우저가 이 보안 연결을 통해 "[www.google.com](http://www.google.com/)" 페이지를 요청하는 HTTP GET 요청을 보냅니다.
- **서버 응답**: Google 서버가 요청을 처리한 후 Google 홈페이지를 구성하는 HTML, CSS, 및 JavaScript 파일을 돌려보냅니다.
- **페이지 렌더링**: 브라우저가 이 파일들을 읽고 화면에 Google 홈페이지를 표시합니다. 여기에는 검색 상자 및 페이지의 다른 콘텐츠가 포함됩니다.
- **사용자 상호작용**: 이제 검색 쿼리를 수행하는 등 페이지와 상호작용할 수 있습니다.
<br/>
<br/>
<details>
<summary>
TCP와 UDP의 차이점에 대해서 설명해보세요.
</summary>
<hr/>
TCP는 연결형 서비스로 3-way handshaking 과정을 통해 연결을 설정하기 때문에 높은 신뢰성을 보장하지만, 속도가 비교적 느리다는 단점이 있습니다.

UDP는 비연결형 서비스로 3-way handshaking을 사용하지 않기 때문에 신뢰성이 떨어지는 단점이 있지만, 데이터 수신 여부를 확인하지 않기 때문에 속도가 빠르다는 장점이 있습니다.

TCP는 신뢰성이 중요한 파일 교환과 같은 경우에 쓰이고 UDP는 실시간성이 중요한 스트리밍에 자주 사용됩니다.
![image](https://github.com/luminousol/backend-cs-study/assets/130022922/7f96e172-9283-4820-a3c2-10bc0c78bcc7)
<br/>
<br/>
</details>


<details>
<summary>
TCP 3, 4 way handshake에 대해서 설명해보세요.
</summary>
<hr/>
3-way handshake는 TCP의 안전하고 신뢰성있는 연결을 보장하기 위한 초기 프로세스이고 , 4-way handshake는 데이터가 안전하게 모두 잘 전송된 후 연결 해제를 할 수 있게 해주는 종료 프로세스입니다. 
<br/>
  
### ✔️ 3 way handshake 
클라이언트가 연결을 시작하고 싶다는 의미로 서버에게 SYN 패킷을 보냅니다. 버는 클라이언트의 요청을 받고, 그 요청에 대한 응답으로 SYN 패킷과 함께 ACK 패킷도 보냅니다. 마지막으로 클라이언트는 서버에게 ACK 패킷을 보내 알립니다.
<br/>
  
### ✔️ 4 way handshake
클라이언트가 더 이상 데이터 전송이 필요하지 않다면 연결을 종료하겠다는 의미로 FIN 패킷을 서버에게 보냅니다. 서버는 클라이언트의 FIN 패킷을 받아들이고 ACK 패킷을 보냅니다. 서버는 준비를 마치고 연결을 종료하겠다는 의미로 FIN 패킷을 클라이언트에게 보냅니다. 클라이언트는 마지막 ACK 패킷을 서버에게 보내 연결을 완전히 종료합니다.
<br/>
<br/>
</details>

<details>
<summary>
HTTP와 HTTPS의 차이점에 대해서 설명해보세요.
</summary>
<hr/>
💬 HTTP는 암호화가 추가되지 않았기 때문에 보안에 취약한 반면, HTTPS는 안전하게 데이터를 주고받을 수 있습니다.

하지만 HTTPS를 이용하면 암호화/복호화의 과정이 필요하기 때문에 HTTP보다 속도가 느립니다. (물론 오늘날에는 거의 차이를 못느낄 정도이다.) 또한 HTTPS는 인증서를 발급하고 유지하기 위한 추가 비용이 발생합니다.

개인 정보와 같은 민감한 데이터를 주고 받아야 한다면 HTTPS를 이용하고 노출이 되어도 괜찮은 단순한 정보 조회 등 만을 처리하고 있다면 때에 따라 HTTP를 이용해도 괜찮습니다.
<br/>
<br/>
</details>


<details>
<summary>
HTTPS에 대해서 설명하고 SSL Handshake에 대해서 설명해보세요.
</summary>
<hr/>
💬 HTTPS는 HTTP에 보안 기능을 추가한 프로토콜로, 웹 브라우저와 서버 간의 통신에 SSL 또는 TLS 암호화를 적용하여 데이터를 보호합니다. 이는 사용자 데이터의 기밀성과 무결성을 보장하며, 중간자 공격으로부터 사용자를 보호하기 위한 목적으로 설계되었습니다.

1. **클라이언트 헬로:** 클라이언트가 SSL 버전, 암호 알고리즘, 세션 ID를 포함하는 메시지를 서버로 보냅니다.
2. **서버 헬로:** 서버는 클라이언트의 요청을 수락하고 선택된 암호화 방식과 함께 자신의 인증서를 클라이언트에게 전송합니다.
3. **인증과 키 교환:** 클라이언트는 서버의 인증서를 확인하고, 공개키를 이용해 암호화된 프리마스터 시크릿을 서버에게 보냅니다.
4. **세션 키 생성:** 양쪽 모두 프리마스터 시크릿에서 세션 키를 도출하여 향후 통신에 사용합니다.
5. **핸드셰이크 완료:** 'Finished' 메시지가 교환되며, 이후부터는 이 세션 키를 사용하여 통신 데이터를 암호화합니다.
<br/>
<br/>
</details>


<details>
<summary>
GET과 POST의 차이점에 대해서 설명해보세요.
</summary>
<hr/>
GET과 POST는 HTTP 프로토콜에서 사용되는 두 가지 주요 요청 메서드입니다. GET은 데이터를 URL의 쿼리 문자열에 노출시키고, POST는 데이터를 HTTP request Body에 숨겨 전송합니다. 일반적으로는 GET을 할 때 request Body를 함께 보내지 않습니다. GET은 주로 데이터 양에 제한이 있고 URL에 노출되어 보안에 취약하며, POST는 더 많은 데이터 양을 안전하게 전송할 수 있습니다. 또한, GET은 캐싱 가능하고 북마크에 저장할 수 있지만, POST는 캐싱이 어렵고 보안적으로 강력합니다. 즉, GET은 주로 데이터 조회에, POST는 데이터 제출에 사용됩니다.
<br/>
<br/>
</details>

<details>
<summary>
HTTP 메서드와 이것이 하는 역할에 대해서 설명해보세요.
</summary>
<hr/>
💬 OPTIONS, HEAD, TRACE의 존재에 대해서는 알아만 둡시다. 특히 TRACE는 몰라도 되는 것 같습니다. OPTIONS는 해당 uri에 대해 서버가 허용하는 메서드를 확인할 때 사용합니다. HEAD는 GET과 비슷하나 header만 가져옵니다.

- GET 요청은 서버에 존재하는 데이터를 요청하는 것입니다. CRUD로 따지면 R입니다.
- POST 요청은 서버에 데이터를 생성하는 것을 요청합니다. CRUD로 따지면 C입니다.
- PUT 요청은 서버에 존재하는 데이터를 수정하거나 존재하지 않으면 생성합니다. CRUD로 따지면 C,U입니다.
- DELETE 요청은 서버에 데이터를 제거할 것을 요청합니다. 존재하지 않아도 동일하게 동작합니다. CRUD로 따지면 D입니다.
- PATCH 요청은 서버에 존재하는 데이터를 일부 수정합니다. CRUD로 따지면 U입니다.
<br/>
<br/>
</details>

<details>
<summary>
RESTful이란 무엇이며, 이것에 대해서 아는대로 설명해보세요.
</summary>
<hr/>
RESTful이란 REST한 원칙에 최대한 맞춰 API를 설계하는 것을 말합니다. REST란, 웹의 **장점을 최대한 활용할 수 있는 아키텍처**로써, REST는 **자원(Resource) 기반의 구조**로 설계되며, **각 자원은 URL로 표현**됩니다. HTTP 표준에 따라, 각 자원에 대한 **CRUD**(Create, Read, Update, Delete) 연산은 표준 HTTP 메소드를 통해 수행합니다.

### ✔️ RESTful 하지 못한 경우

- 한 가지 HTTP 메서드만 사용하여 여러 작업을 수행하는 경우
- URI에 동사나 액션을 포함시키는 경우
- 리소스 대신 CRUD 작업을 중심으로 설계하는 경우
<br/>
<br/>
</details>

<details>
<summary>
CORS란 무엇이며 이것에 대해서 설명해보세요.
</summary>
<hr/>
💬 CORS는 웹페이지가 다른 출처(도메인, 프로토콜, 포트 등이 다른 곳)의 리소스를 사용할 수 있게 하는 방법입니다. 웹은 기본적으로 보안을 위해 한 출처의 스크립트가 다른 출처의 데이터에 접근하는 것을 제한하지만, CORS를 사용하면 이 제한을 안전하게 우회할 수 있습니다.

웹사이트가 다른 출처의 데이터를 요청하면, 브라우저는 실제 요청 전에 '사전 요청'을 보내어 서버에게 허가를 구합니다. 서버는 이 사전 요청에 대해 '네, 괜찮아요'라고 응답하면서, 어떤 출처, 어떤 HTTP 메소드, 어떤 헤더가 자신의 데이터를 사용할 수 있는지 알려줍니다. 이런 정보는 보통 'Access-Control-Allow-Origin' 같은 헤더에 담겨서 오고, 이 헤더를 검사하여 브라우저는 요청이 안전한지 결정합니다.

서버가 CORS를 허용하지 않으면, 브라우저는 요청을 차단하고 사용자에게 오류 메시지를 보여줍니다. CORS는 이렇게 웹의 유용성을 높이면서도 사용자의 데이터를 안전하게 보호하는 역할을 합니다.
<br/>
<br/>
<details/>

<details>
<summary>
OSI7계층과 그 존재 이유, TCP/IP 4계층에 대해 설명해보세요.
</summary>
<hr/>
💬 OSI 7 계층은 ISO에서 개발한 컴퓨터 네트워크 프로토콜 디자인과 통신을 계층으로 나누어 설명한 개방형 시스템 상호 연결 모델입니다. 각 계층은 독립적이고 하위 계층의 기능을 이용해 상위 계층에 기능을 제공합니다.

TCP/IP 모델은 실제 인터넷에서 널리 사용되는 프로토콜 스위트로, OSI 모델보다 단순한 4계층 구조로 되어 있습니다.
<br/>
<br/>
<details/>

<details>
<summary>
웹 서버 소프트웨어(Apache, Nginx)는 OSI 7계층 중 어디서 작동하는지 설명해보세요.
</summary>
<hr/>
💬 Apache와 Nginx와 같은 웹 서버 소프트웨어는 HTTP 프로토콜을 통해 웹 페이지와 관련 파일(HTML 문서, 이미지, 스타일시트, 자바스크립트 파일 등)을 클라이언트(주로 웹 브라우저)에 제공합니다. 이들은 클라이언트의 요청을 받아 처리하고 적절한 응답을 생성하여 다시 클라이언트로 전송하는 역할을 합니다.

웹 서버 소프트웨어는 OSI 7계층 모델 중 '응용 계층(Application Layer)'에서 작동합니다. 이 계층은 사용자가 직접 상호작용하는 애플리케이션 서비스를 제공하며, 네트워크의 다른 부분과 독립적으로 통신 프로토콜과 인터페이스를 관리합니다.

※ 웹서버의 기능

- 사용자의 요청에 따라 웹 페이지를 제공합니다.
- 동적 컨텐츠를 생성하기 위해 스크립트 언어(예: PHP, Python)를 처리합니다.
- SSL/TLS를 통한 암호화된 데이터 전송을 설정하여 HTTPS 통신을 관리합니다.
- 사용자 인증, 리다이렉션, 서버 사이드 캐싱 등의 다양한 추가 기능을 제공합니다.
<br/>
<br/>
<details/>

<details>
<summary>
웹 서버 소프트웨어(Apache, Nginx)의 서버 간 라우팅 기능은 OSI 7계층 중 어디서 작동하는지 설명해보세요.
</summary>
<hr/>
💬 웹 서버 소프트웨어의 서버 간 라우팅 기능은 응용 계층에서 구현되지만, 실제 데이터 전송과 관련된 작업은 네트워크와 전송 계층에서 이루어집니다.

웹 서버 소프트웨어는 주로 OSI 모델의 응용 계층에서 작동합니다. Apache와 Nginx와 같은 웹 서버는 HTTP와 같은 프로토콜을 통해 클라이언트의 요청을 처리하고, 적절한 웹 리소스를 응답합니다. 이때 웹 서버가 서버 간 라우팅 기능을 수행할 때는, 리버스 프록시나 로드 밸런서의 역할을 하며, 이는 주로 응용 계층의 일부로 간주됩니다.

하지만 서버 간 라우팅은 OSI 모델의 여러 계층에 걸친 작업이 포함될 수 있습니다. 예를 들어, Nginx가 로드 밸런싱 기능을 수행할 때, 이는 전송 계층의 일부 기능을 수행하기도 합니다. 여기서는 TCP나 UDP 프로토콜을 사용하여 클라이언트의 요청을 적절한 내부 서버로 분배합니다. 그렇지만 웹 서버 소프트웨어 자체의 설정과 로직은 응용 계층 내에서 구성되고 실행됩니다.
<br/>
<br/>
<details/>
