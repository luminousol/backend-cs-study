# NETWORK

1. [네트워크 기초](https://polydactyl-impala-301.notion.site/4a0f54a2586f469e9f28dd663395e5e4?pvs=4) - 주연
2. [대역폭 - 솔이](https://flossy-longship-14b.notion.site/Bandwidth-6c80555968904f58851373b1aecb785d?pvs=4)
3. [OSI 7계층](https://polydactyl-impala-301.notion.site/OSI-7-7d75e296ab314295a07e98b8f0b3294a?pvs=4) - 주연
4. [TCP 의 연결 및 해제 과정 (3, 4 - way hands shanking) - 솔이](https://flossy-longship-14b.notion.site/TCP-3-4-way-hands-shanking-070d08e7006149798845bc79df0d68ab?pvs=4)
5. [DNS + 웹 통신 흐름](https://polydactyl-impala-301.notion.site/DNS-e386fde72242427da4561a298f5a5e53?pvs=4) - 주연
6. [네트워크 기기 - 솔이](https://flossy-longship-14b.notion.site/fc78f1688dbf4c4085ac3f4ecd2ec41e?pvs=4)
7. [L7, L4 스위치 + 로드 밸런싱](https://polydactyl-impala-301.notion.site/L7-L4-d978833d093247ccb3047a412148f1c6?pvs=4) - 주연
8. [HTTP 진화과정 - 동민](https://www.notion.so/ehdals0405/HTTP-568841a8c7c14c66aaaab759dcd3c27d)
9. [HTTPS - 동민](https://www.notion.so/ehdals0405/HTTPS-967faa46cfc1405f9ab904a9e0fa62db)
10. [REST API + RESTful - 솔이](https://flossy-longship-14b.notion.site/REST-API-RESTful-4c03f22d4e304e699b0ed267d9dc9c2e?pvs=4)
11. [쿠키와 세션 - 동민](https://www.notion.so/ehdals0405/Cookie-Session-bfbcfdbc56334cf8b4aa47785fe748a8#d59f064fe53a4ee99a4f08fcb8e23be7) 
12. [프록시 서버 - 동민](https://www.notion.so/ehdals0405/e8c818253c1242169567427e43287f59)

## 질문
<details>
<summary>
웹 통신의 큰 흐름: https://www.google.com/ 을 접속할 때 일어나는 일
</details>
</summary>

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

<br/>
<br/>
</details>


<details>
<summary>
HTTPS에 대해서 설명하고 SSL Handshake에 대해서 설명해보세요.
</summary>
<hr/>

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

<br/>
<br/>
<details/>

<details>
<summary>
OSI7계층과 그 존재 이유, TCP/IP 4계층에 대해 설명해보세요.
</summary>
<hr/>

<br/>
<br/>
<details/>

<details>
<summary>
웹 서버 소프트웨어(Apache, Nginx)는 OSI 7계층 중 어디서 작동하는지 설명해보세요.
</summary>
<hr/>

<br/>
<br/>
<details/>


<details>
<summary>
웹 서버 소프트웨어(Apache, Nginx)의 서버 간 라우팅 기능은 OSI 7계층 중 어디서 작동하는지 설명해보세요.
</summary>
<hr/>

<br/>
<br/>
<details/>
