### Computer Network

<details>
<summary>📚 공부한 자료</summary>

- 네트워크 하향식 접근
- HTTP 완벽 가이드
- 성공과 실패를 결정하는 1%의 네트워크 원리

</details>

### **1. 쿠키와 세션의 차이에 대해 설명해 주세요.**
  Answer:
  쿠키란 웹 브라우저(클라이언트)에 저장되는 키-값으로 이뤄져 있는 작은 데이터 파일입니다. 쿠키는 사용자가 따로 요청하지 않아도 서버에 리퀘스트를 보낼 때 헤더에 넣어서 서버로 전송됩니다.
  세션은 서버측에 클라이언트 데이터를 저장해 놓는 것으로 쿠키를 이용하여 동작합니다. 웹 브라우저에 저장된 쿠키 중 SESSION ID를 저장하는 쿠키가 있는데, 이 쿠키가 리퀘스트 헤더에 포함되어 전송되어 세션 아이디와 일치하는 세션에서 클라이언트 정보를 찾을 수 있습니다.
    쿠키와 세션의 가장 큰 차이점은 저장되는 위치입니다. 쿠키는 웹 브라우저에, 세션은 서버 측에 저장되어 관리됩니다.
  또한, 쿠키는 파일로 저장되기 때문에 만료 시간을 설정해서 브라우저가 종료되더라도 남아있도록 할 수 있지만 세션은 웹 브라우저가 종료되면 함께 사라집니다.

- **세션 방식의 로그인 과정에 대해 설명해 주세요.**
  Answer: 세션 방식 로그인은 사용자의 인증 정보를 서버의 세션 저장소에 저장되는 방식입니다. 사용자가 로그인을 하면 해당 인증 정보를 서버의 세션 저장소에 저장하고, 사용자에게는 Session ID를 발급합니다. 이 세션 아이디는 쿠키로 브라우저에 저장되지만 실제 인증 정보는 서버 세션에 저장됩니다. 브라우저는 인증 절차를 마친 이후, 요청을 보낼 때마다 서버에 세션 아이디 쿠키를 함께 전송합니다. 서버는 세션 아이디에 해당하는 세션 정보를 보고 해당 사용자가 인증이 된 사용자인지 아닌지를 확인합니다. 


- **HTTP의 특성인 Stateless에 대해 설명해 주세요.**
  Answer: stateful은 서버가 클라이언트의 이전 상태를 보존한다는 의미입니다. 반대로 stateless는 서버가 클라이언트의 이전 상태를 보존하지 않습니다. stateful의 경우, 서버가 클라이언트의 이전 정보를 보존해야하기 때문에, 클라이언트의 요청의 결과가 항상 같은 서버에서 반환되는 것이 보장되어야 합니다. 하지만 stateless는 클라이언트의 이전 정보를 가지고 있지 않으므로 클라이언트는 어느 서버에 응답이 오더라도 상관 없습니다. 하지만 로그인과 같은 기능들은 stateless로는 구현할 수가 없기 때문에 서버 세션 등을 이용해서 구현할 수 있습니다.

- **Stateless의 의미를 살펴보면, 세션은 적절하지 않은 인증 방법 아닌가요?**
  Answer: 
  세션은 서버에 클라이언트의 정보를 보관하므로 stateless에 반하는 것이기는 합니다. 하지만 웹 서비스를 구현할 때 불가피하게 로그인 상태 유지와 같이 클라이언트의 정보를 저장해야하는 일이 생기기 때문에 세션을 이용하는 것 같습니다. 세션을 이용하지 않는다면 stateless 특성 때문에 매 통신마다 클라이언트의 정보와 요청 내용을 같이 전송하는 방식으로 통신하게 되고, 이런 방식은 웹 페이지의 로딩을 느리게 하고 통신에서 오는 부하를 증가시키기 때문에 이를 줄이기 위해서 세션을 사용하는 것 같습니다.

- **규모가 커져 서버가 여러 개가 된다면, 세션을 어떻게 관리할 수 있을까요?**
  Answer:
  ** Stiky Session ** 방식이라고 하여, 클라이언트의 IP를 추적하거나 쿠키를 이용해서 같은 클라이언트의 요청이 해당 클라이언트에 대한 세션을 가지고 있는 같은 서버로 계속 가게하는 방법이 있습니다. 하지만 이 방법은 로드 밸런싱의 효율을 떨어뜨리고, 한 서버가 다운되면 그 서버가 관리하는 세션이 모두 유실된다는 단점이 있습니다.
  그래서 나온 방식이 session 저장소를 여러 서버가 공유하는 방식입니다. ** Session clusering **이라는 방식으로 여러 서버의 세션 저장소를 하나로 묶어 관리하는 방식입니다. 하지만 모든 서버의 세션데이터를 동일하게 하기 위해서 하나의 세션이 생기면 모든 서버의 세션 저장소를 업데이트 해주어야 하고 그만큼 많은 메모리가 필요하기에 성능 저하가 발생하게 됩니다.
  마지막으로 Redis 같은 인메모리 저장소를 이용해서 여러 서버가 공유하는 별도의 ** 세션 서버 **를 두는 방법이 있습니다. 이 또한 세션 서버가 다운되면 세션이 모두 유실된다는 단점이 있지만, Redis 같은 인메모리 저장소는 메모리에 데이터를 저장하면서 다른 서버의 메모리에 실시간으로 복사본을 저장하거나 디스크에 직접 저장을 하면서 백업이 가능하고 Master - Slave 형식으로 구성이 가능하여 Master 서버가 다운되어도 Slave 서버로 접속하여 서비스를 유지할 수 있습니다.

- **토큰 기반 방식은 어떤 장점이 있을까요?**
  Answer: 토큰 방식 인증은 확장성에서 장점을 갖습니다. 세션 기반 인증은 여러 개의 서버를 사용할 경우, 세션 불일치 문제를 해결하기 위해서 Stiky Session, Session Clustering, Session Storage 등의 방법을 사용해야하고, 이런 방법을 사용할 경우 새로운 서버를 추가해야할 때, 추가적인 작업을 해주어야합니다. 예를 들면, Session Clustering 방식으로 세션 불일치를 해결하고 있었다고 하면, 새로운 서버가 들어왔을 때 이 서버도 클러스터에 추가하고, 기존 서버들의 세션 저장소의 내용을 해당 서버 세션 저장소에 복사해야하는 등의 추가 작업이 필요합니다. 하지만 토큰 방식의 인증은  클라이언트가 인증 정보를 저장하고 있기 때문에 확장을 했을 때 세션 불일치를 피하기 위한 추가적인 작업이 없습니다. 또한 토큰 방식은 인증 데이터를 클라이언트가 관리함으로써 서버에 가해지는 부하를 줄일 수 있습니다.


### **2. HTTP 응답코드에 대해 설명해 주세요.**
  Answer: HTTP 프로토콜로 요청-응답을 주고 받을 때 요청의 처리 결과를 알 수 있는 코드 입니다. 100~500번대로 정의되어 있는데, 100번대는 요청이 수신되어 처리 중, 200번대는 요청이 정상 처리됨, 300번대는 요청을 완료하려면 추가 행동이 필요함, 400번대는 클라이언트 오류, 500번대는 서버 오류의 의미를 가지고 있습니다.

- **401 (Unauthorized) 와 403 (Forbidden)은 의미적으로 어떤 차이가 있나요?**
  Answer: "400 Bad Request"는 "요청에 문제가 있어(synctax의 오류) 처리를 하지 않겠다"는 의미입니다. "403 Forbidden"은 "요청은 이해하지만 권한으로 인해 처리하지 않겠다"는 의미입니다.

- **200 (ok) 와 201 (created) 의 차이에 대해 설명해 주세요.**
  Answer: "200 OK"는 클라이언트의 요청을 서버가 정상적으로 처리하였다는 의미이며, "201 Created"는 서버가 클라이언트의 요청을 정상적으로 처리하여 새로운 리소스가 생겼다는 의미입니다. 201 상태코드는 POST, PUT 요청에 대한 응답으로 주로 이용되고 응답에는 생성된 리소스에 대한 설명과 링크가 제공됩니다. 클라이언트의 요청이 성공적으로 처리되었다는 점에서 동일하지만 201은 새로운 리소스가 생성되었다는 의미를 포함한다는 점에서 다릅니다. 생성 요청에 대한 응답을 200으로 해도 되지만, 정확한 의미 전달을 위해 201로 응답하는 것이 더 좋습니다.

- **필요하다면 저희가 직접 응답코드를 정의해서 사용할 수 있을까요? 예를 들어 285번 처럼요.**
  Answer: 상태 코드를 커스텀 하여 사용할 수도 있습니다. 예를 들면 에러이긴 한데 HTTP 표준 상태 코드(ex. 404, 400)로는 표현할 수 없는 디테일한 의미를 포함해야한다면 커스텀 에러 코드를 만들어 사용할 수도 있습니다. 하지만 표준 상태 코드는 전세계가 쓰는 표준이지만 직접 정의한 상태 코드는 팀 안에서만 쓰는 것이기 때문에 새로운 팀원이 들어온다면 인수인계 해줄 내용이 늘어나게 되고, 개발자들이 해당 코드의 의미를 까먹게 되는 일이 발생할 수 있기 때문에 꼭 필요한 경우가 아니라면 쓰지 않는 것이 좋을 것 같습니다. (이 질문에 답변에 대해서는 정보가 많지 않아 확신이 없습니다. 위 답변의 출처: https://okky.kr/articles/821691)


### **3. HTTP Method 에 대해 설명해 주세요.**
  Answer:
    HTTP 메소드란 서버와 클라이언트가 HTTP 프로토콜을 통해 요청과 응답 데이터를 전송하는 방식을 말합니다. 즉, 요청을 할 때 HTTP 메소드의 종류마다 클라이언트가 서버에 요청하는 내용(예를 들어 데이터 조회, 리소스 생성, 프로세스 처리 등등)이 달라진다고 할 수 있습니다.

- **HTTP Method의 멱등성에 대해 설명해 주세요.**
  Answer:
    서버에 동일한 요청을 한번 보내는 것과 여러 번 보내는 것이 같은 효과를 가지고 서버의 상태도 동일하게 남을 때 해당 HTTP 메소드가 멱등성을 갖는다고 말합니다.
    멱등성을 가지는 HTTP method에는 GET, HEAD, PUT, DELETE, OPTION 등이 있고, 멱등성을 가지지 않는 메소드에는 POST, PATCH 등이 있습니다.
- **GET과 POST의 차이는 무엇인가요?**
  Answer:
    GET은 특정 representaion(resource라고도 함)을 조회하겠다는 의미의 메소드입니다. GET은 서버에 전달하고자 하는 정보를 쿼리 스트링으로 전달하는데, 이 정보는 HTTP request에서 헤더 부분에 담기게 됩니다. GET도 request의 body 부분을 사용할 수는 있지만, 지원하지 않는 서버들이 많아 권장하지 않습니다.
      POST는 요청한 데이터를 서버가 처리해달라는 의미의 메소드입니다. GET과의 다른 점은 서버에 전달하고자 하는 정보를 메시지의 헤더가 아닌 메시지 바디에 넣어 전달한다는 점입니다.
        GET은 주로  정보의 조회, POST는 주로 신규 리소스를 등록하거나 어떤 프로세스를 처리해달라고 할 때 쓰입니다.
- **POST와 PUT, PATCH의 차이는 무엇인가요?**
  Answer:
    POST는 클라이언트가 요청을 보낼 때 리소스의 URI를 알 필요 없고, URL까지만 알면 됩니다. 예를 들어 클라이언트가 게시판에 글을 생성하려고 할 때, 클라이언트는 자신이 몇번째 글(글의 id)을 생성할 것인지 모릅니다. 물론 이는 리소스 생성에 대한 예시이고, POST 요청도 URI로 자원을 특정하여 이 자원을 어떻게 처리해달라는 요청을 보낼 수 있습니다.
      하지만 PUT과 PATCH는 클라이언트가 요청을 보낼 때 반드시 리소스의 URI를 알고 있어야합니다. PUT은 해당 리소스가 없다면 생성, 있다면 덮어쓰는 것이고, PATCH는 해당 리소스가 없다면 생성, 없다면 부분 수정을 하는 메소드인데, 이 두 메소드는 클라이언트가 전체 URI로 리소스를 특정해주어야 합니다.
    
- **HTTP 1.1 이후로, GET에도 Body에 데이터를 실을 수 있게 되었습니다. 그럼에도 불구하고 왜 아직도 이런 방식을 지양하는 것일까요?**
  Answer: 
    이유는 크게 2가지입니다.
      첫번째는 어떤 서버들은 바디가 있는 GET 요청을 지원하지 않습니다. HTTP 1.1이 처음에 body가 있는 GET request에 defined-semantics가 포함되어있지 않다면 그 body를 무시하라고 권고했기 때문에 그에 따라 구현된 오래된 서버들은 GET 요청의 바디의 내용을 무시할 가능성이 있습니다. 또는 구현에 따라 바디가 있는 GET 요청을 거절(reject)하기도 합니다.
      두번째는 GET 요청시 바디에 데이터를 넣어보내면 캐시를 통한 성능 개선이 원활하게 이뤄지지 않을 수 있습니다.
      GET 요청에 의해서 응답으로 돌아온 데이터는 일반적으로 브라우저 캐시에 캐싱되었다가 같은 요청이 들어오면 서버에 요청을 보내지 않고 캐시에서 데이터를 찾음으로써 성능을 개선할 수 있습니다. 하지만 메시지 바디에 요청에 대한 데이터가 있다면 그 내용은 브라우저에 캐싱되지 않을 것이고, 같은 요청에 대해서 여러번 서버의 api를 호출해야하기 때문에 캐싱이 주는 장점을 활용할 수 없게 됩니다.
        출처: https://www.baeldung.com/cs/http-get-with-body


### **4. HTTP에 대해 설명해 주세요.**

- **공개키와 대칭키에 대해 설명해 주세요.**
- **왜 HTTPS Handshake 과정에서는 인증서를 사용하는 것 일까요?**
- **SSL과 TLS의 차이는 무엇인가요?**

### **5. 웹소켓과 소켓 통신의 차이에 대해 설명해 주세요.**
  
  Answer:
    소켓은 애플리케이션 계층과 전송 계층 사이에 위치하는 것으로, 한 프로세스가 IP와 포트 번호를 통해서 다른 프로세스와 네트워크 연결을 할 수 있게 해주는 역할을 합니다. 즉 애플리케이션 계층의 프로그램들이 TCP/IP 프로토콜을 써서 네트워크 통신을 할 수 있게 해주는 연결부 역할을 합니다.
      HTTP는 비연결성으로 인해 통신을 할 때마다 커넥션을 생성해야하고, request과 response를 주고 받는 단방향 통신이라는 점 때문에 실시간 통신이 어려운데, 이런 점을 보완하기 위해 실시간 통신을 지원하는 것이 웹 소켓입니다.
        소켓과 웹 소켓의 차이는 동작하는 레이어(계층)가 다르다는 것인데, 소켓은 애플리케이션 계층과 전송 계층 사이에서, 웹 소켓은 HTTP 레이어에서 동작한다는 것이 다릅니다.


- **소켓과 포트의 차이가 무엇인가요?**
  Answer:
    소켓은 한 프로세스와 다른 프로세스가 통신하기 위해 연결해야하는 창구 같은 것입니다.
    한 호스트 내에서는 여러 애플리케이션이 실행될 수 있는데, 각각의 애플리케이션은 애플리케이션을 식별하기 위한 각각의 고유 번호인 포트를 부여 받습니다.
    소켓 연결을 할 때 프로세스가 실행되고 있는 호스트의 IP 주소, 프로세스의 포트 번호, 프로토콜 세가지가 필요합니다. 그리고 같은 IP, 포트번호에 대해서도 여러 개의 소켓을 연결할 수 있습니다.
    비유하자면 소켓은 아파트의 입구이고 포트는 특정 아파트의 호수과 같다고 할 수 있습니다.

- **여러 소켓이 있다고 할 때, 그 소켓의 포트 번호는 모두 다른가요?**
  Answer:
    위 질문의 답변에서도 언급했듯이, 같은 IP, 포트번호에 대해서 여러 소켓을 생성할 수 있기 때문에 여러 소켓들이 존재한다면 그 소켓의 포트번호는 같을 수도 있고 다를 수도 있습니다.  
    

- **사용자의 요청이 무수히 많아지면, 소켓도 무수히 생성되나요?**
  Answer: 사용자의 요청이 증가함에 따라 서버가 생성하는 소켓의 개수가 많아질 수는 있지만, 실제로 무수히 많은 소켓이 생성되는지 여부는 서버의 용량, 응용 프로그램의 설계, 사용되는 기술의 특성에 따라서 달라집니다.

### **6. HTTP/1.1과 HTTP/2의 차이점은 무엇인가요?**

- **HOL Blocking 에 대해 설명해 주세요.**
- **HTTP/3.0의 주요 특징에 대해 설명해 주세요.**

### **7. TCP와 UDP의 차이에 대해 설명해 주세요.**
  
  Ansewer: TCP는 연결 지향 프로토콜로, 연결시에 3-Way-Handshake 연결 종료시에 4-Way-Handshake를 진행하여 연결을 하고 연결을 끊습니다. 또한 송수신 측이 ACK을 주고 받으며 세그먼트가 제대로 도착하였는지 확인하고, 제대로 도착하지 않았다면 재송신합니다. 흐름 제어가 가능하기에 신뢰성이 높지만, ACK을 주고 받는 과정에서 wait이 발생하여 UDP 보다 느립니다.
    UDP는 데이터그램 방식을 사용하는 프로토콜입니다. 데이터그램 방식은 목적지만 정해져 있다면 어떤 경로를 타서 가도 상관이 없기 때문에 TCP에서 했던 3-way-handshake, 4-way-handshake 과정을 하지 않습니다. 따라서 TCP 보다 빠르게 전송이 가능한 것입니다. 하지만 UDP 또한 애플리케이션 레이어에서 TCP처럼 흐름제어, 혼잡제어 등과 같은 기능을 구현하면 송수신의 정확성을 보장해 줄 수 있습니다. 이처럼 UDP는 신뢰성이 없는 프로토콜이라기 보다는 신뢰성을 보장해주는 기능이 구현되지 않은 프로토콜이기 때문에 개발자가 커스터마이징이 가능하다는 특징이 있습니다.

- **Checksum이 무엇인가요?**
  Answer: TCP와 UDP 통신에서 세그먼트가 전달되는 동안 변형, 손상이 되었는지 확인하기 위해 존재하는 필드입니다. checksum의 값은 TCP와 UDP 헤더에 존재합니다.

- **TCP와 UDP 중 어느 프로토콜이 Checksum을 수행할까요?**
  Answer: TCP는 항상 checksum을 수행하지만 UDP의 checksum 여부는 옵션입니다.

- **그렇다면, Checksum을 통해 오류를 정정할 수 있나요?**
  Answer: 네. checksum과 송신측이 데이터를 16비트로 나눠 모두 더하고 캐리가 생기면 이것도 더해서 구한 수를 더해서 모든 비트가 1이라면 데이터가 변경되지 않은 것이지만, 0이 하나라도 있다면 세그먼트가 변경되었다는 의미입니다. 그런 경우 해당 세그먼트 재전송을 통해 오류를 정정할 수 있습니다.

- **TCP가 신뢰성을 보장하는 방법에 대해 설명해 주세요.**
  Answer: TCP는 수신측이 데이터를 잘 받았다면 ACK을, 체크섬을 확인해보았을 때 손상된 세그먼트를 받았다면 NCK을 보냅니다. 만약 NCK을 받는다면 해당 세그먼트를 재전송하고, wait 상태에서 ACK이나 NCK이 오지 않은 상태로 타임아웃이 되어도 재전송을 하는 방식으로 신뢰성을 보장해줍니다.
    

- **TCP의 혼잡 제어 처리 방법에 대해 설명해 주세요.**
  Answer: TCP는 주로 AIMD라고 하는 합 증가-곱 감소 방법과 슬로스타트라는 방식을 적절하게 섞어 혼잡 윈도우(CWND)의 크기를 조절하여 혼잡 제어를 합니다.
    AIMD란, 윈도우 사이즈만큼 패킷을 전송했을 때 모두 문제 없이 잘 도착했다는 ACK을 받으면 혼잡 윈도우의 사이즈를 1씩 증가 시킵니다. 그러다가 NCK을 받거나 타임아웃이 발생하게 되면 윈도우의 크기를 절반으로 네트워크 혼잡 상황을 제어하는 방법입니다.
      슬로스타트란 처음에 패킷을 1개를 보내고 잘 도착했다면 다음엔 2개, 4개, 8개처럼 윈도우 사이즈를 2배씩 늘려나가는 방식입니다. 윈도우 사이즈를 늘려나가던 중 패킷 손실이 발생하면 윈도우 사이즈를 1로 줄여 혼잡 제어를 하는 정책입니다.
        그외에도 혼잡 회피와 빠른 회복 정책도 존재하며 슬로스타트와 함께 쓰입니다. 혼잡 회피란, 슬로스타트 방식으로 윈도우사이즈를 늘려가다가 직전 손실이 시작된 cwnd의 절반값에 도달하면 지수 증가 대신 윈도우사이즈를 선형 증가로 늘려가는 방식입니다. 이 과정에서 손실이 발생하면 다시 윈도우 사이즈를 1로 줄여 슬로우 스타트로 돌아갑니다.
          빠른 회복이란 혼잡 회피로 인해 1씩 윈도우 사이즈를 증가시키다가 손실이 발생한 경우 적용되는 정책으로,3중복 ACK이 발생한 경우와 타임아웃이 발생한 경우를 구분합니다. 3 중복 ACK 즉 가벼운 손실이 일어나면 윈도사이즈를 절반+3MSS로 줄이고 타임아웃이 발생하면 1MSS로 줄이게 됩니다.
        출처: https://uzun.dev/166
      
- **왜 HTTP는 TCP를 사용하나요?**
  Answer: TCP는 연결을 위한 3-way-handshake, 오류 제어, 흐름제어, 혼잡 제어가 보장되는 프로토콜이기 때문에 패킷을 유실없이 보낼 수 있도록 TCP 기반에서 작동한다고 생각합니다. 

- **Websocket 은 TCP/UDP 중 어떤 방식을 사용하고, 그 이유는 무엇일까요?**

- **그렇다면, 왜 HTTP/3 에서는 UDP를 사용하나요? 위에서 언급한 UDP의 문제가 해결되었나요?**
  Answer: 앞에서 언급하였다 싶이, UDP는 그 자체만으로는 신뢰성을 보장할 수 있는 장치가 거의 없지만, 개발자가 애플리케이션 레벨에서 기능을 구현한다면 신뢰성 등을 보장할 수 있게 됩니다. HTTP/3는 전송계층 프로토콜로는 UDP 프로토콜을 사용하지만 애플리케이션 레이어에서 구현한 QUIC이라는 프로토콜을 추가로 사용합니다. 이 QUIC이 TCP처럼 연결, 흐름제어의 역할을 해주기 때문에 UDP 기반이어도 손실없이 데이터를 주고 받을 수 있습니다.

- **그런데, 브라우저는 어떤 서버가 TCP를 쓰는지 UDP를 쓰는지 어떻게 알 수 있나요?**
- **본인이 새로운 통신 프로토콜을 TCP나 UDP를 사용해서 구현한다고 하면, 어떤 기준으로 프로토콜을 선택하시겠어요?**
- **UDP를 사용하면 신뢰성을 보장하지 못하는 이유가 무엇일까요?⭐️**


### **8. DHCP가 무엇인지 설명해 주세요.**

- **DHCP는 몇 계층 프로토콜인가요?**
- **DHCP는 어떻게 동작하나요?**
- **DHCP에서 UDP를 사용하는 이유가 무엇인가요?**
- **DHCP에서, IP 주소 말고 추가로 제공해주는 정보가 있나요?**
- **DHCP의 유효기간은 얼마나 긴가요?**

### **9. IP 주소는 무엇이며, 어떤 기능을 하고 있나요?**

- **IPv6는 IPv4의 주소 고갈 문제를 해결하기 위해 만들어졌지만, 아직도 수많은 기기가 IPv4를 사용하고 있습니다. 고갈 문제를 어떻게 해결할 수 있을까요?**
- **IPv4와 IPv6의 차이에 대해 설명해 주세요.**
- **수많은 사람들이 유동 IP를 사용하고 있지만, 수많은 공유기에서는 고정 주소를 제공하는 기능이 이미 존재합니다. 어떻게 가능한 걸까요?**
- **IPv4를 사용하는 장비와 IPv6를 사용하는 같은 네트워크 내에서 통신이 가능한가요? 가능하다면 어떤 방법을 사용하나요?**
- **IP가 송신자와 수신자를 정확하게 전송되는 것을 보장해 주나요?**
- **IPv4에서 수행하는 Checksum과 TCP에서 수행하는 Checksum은 어떤 차이가 있나요?**
- **TTL(Hop Limit)이란 무엇인가요?**
- **IP 주소와 MAC 주소의 차이에 대해 설명해 주세요.**

### **10. OSI 7계층에 대해 설명해 주세요.**

- **Transport Layer와, Network Layer의 차이에 대해 설명해 주세요.**
- **L3 Switch와 Router의 차이에 대해 설명해 주세요.**
- **각 Layer는 패킷을 어떻게 명칭하나요? 예를 들어, Transport Layer의 경우 Segment라 부릅니다.**
- **각각의 Header의 Packing Order에 대해 설명해 주세요.**
- **ARP에 대해 설명해 주세요.**

### **11. 3-Way Handshake에 대해 설명해 주세요.**

- **ACK, SYN 같은 정보는 어떻게 전달하는 것 일까요?**
- **2-Way Handshaking 를 하지않는 이유에 대해 설명해 주세요.**
- **두 호스트가 동시에 연결을 시도하면, 연결이 가능한가요? 가능하다면 어떻게 통신 연결을 수행하나요?**
- **SYN Flooding 에 대해 설명해 주세요.**
- **위 질문과 모순될 수 있지만, 3-Way Handshake의 속도 문제 때문에 이동 수를 줄이는 0-RTT 기법을 많이 적용하고 있습니다. 어떤 방식으로 가능한 걸까요?**

### **12. 4-Way Handshake에 대해 설명해 주세요.**

- **패킷이 4-way handshake 목적인지 어떻게 파악할 수 있을까요?**
- **빨리 끊어야 할 경우엔, (즉, 4-way Handshake를 할 여유가 없다면) 어떻게 종료할 수 있을까요?**
- **4-Way Handshake 과정에서 중간에 한쪽 네트워크가 강제로 종료된다면, 반대쪽은 이를 어떻게 인식할 수 있을까요?**
- **왜 종료 후에 바로 끝나지 않고, TIME_WAIT 상태로 대기하는 것 일까요?**

### **13. [www.github.com을](http://www.github.xn--com-of0o/) 브라우저에 입력하고 엔터를 쳤을 때, 네트워크 상 어떤 일이 일어나는지 최대한 자세하게 설명해 주세요.**
  
  Answer:
사용자가 브라우저에 도메인 네임을 입력하면, DNS에서 해당 도메인 네임을 검색하여 해당 서버의 IP 주소를 찾아 사용자가 입력한 URL 정보와 함께 전달합니다.
이렇게 전달된 IP 주소를 가지고 HTTP 프로토콜을 이용해서 HTTP 요청 메시지를 생성하고 그 메시지를 TCP 프로토콜을 사용하여 인터넷을 거쳐 해당 IP 주소의 컴퓨터로 전송됩니다.
이렇게 도착한 HTTP 리퀘스트는 HTTP 프로토콜에 의해 웹 페이지 URL 정보로 변환되어 웹 페이지 URL 정보에 해당하는 데이터를 검색합니다. 해당 데이터를 찾았다면 HTTP 프로토콜로 HTTP 리스폰스 메시지를 생성하고 TCP 프로토콜을 사용하여 인터넷을 거쳐 원래 컴퓨터로 전송됩니다. 도착한 HTTP 리스폰스는 HTTP 프로토콜을 사용하여 웹 페이지 데이터로 변환되어 웹 브라우저에 의해 출력됩니다.


- **DNS 쿼리를 통해 얻어진 IP는 어디를 가리키고 있나요?**
  
  Answer: www.github.com의 웹 서버를 가리킵니다.
- **Web Server와 Web Application Server의 차이에 대해 설명해 주세요.**
  
  Answer:
  웹 서버는 클라이언트에게 정적인 파일(html, css, 이미지 등)을 제공하는 역할을 합니다. 대표적으로 아파치(Apache), 엔진엑스(Nginx) 등이 있습니다.
WAS는 동적인 컨텐츠를 생성하고 데이터를 처리하는 역할을 합니다. 예를 들면 데이터베이스 조회, 비즈니스 로직 처리 등을 WAS가 하게 되고 그에 따라 생성된 동적 컨텐츠를 클라이언트에게 제공합니다.
WAS는 정적, 동적 요청 처리가 모두 가능합니다. 하지만 정적 데이터 요청까지 WAS가 처리하는 것은 WAS에 과부하를 주어 비효율적입니다. 따라서 웹 서버를 앞단에 두고 정적 콘텐츠 요청을 처리하고, WAS는 웹 서버가 처리할 수 없는 서버 사이드 코드의 로직을 수행하도록 해야합니다.

- **URL, URI, URN은 어떤 차이가 있나요?**
  
  Answer:
URI(Uniform Resource Identifier)는 인터넷 상의 리소스를 고유하게 식별하는 문자열입니다. URL과 URN은 URI의 하위 개념입니다.
URL(Uniform Resource Locator)는 네트워크 상에서 리소스가 어디에 위치하고 있고 어떻게 얻을 수 있는지에 대한 정보를 나타냅니다. HTTP 프로토콜 뿐만 아니라 FTP, SMTP 등 다른 프로토콜에서도 사용할 수 있습니다.
URN은 http 같은 프로토콜을 제외하고 리소스의 이름으로 리소스를 특정하는 표기 방식입니다. URN에는 리소스 접근 방법과 웹 상의 위치가 표기되어 있지 않기 때문에, 리소스를 찾기 위해서는 URN을 URL로 변환하여 사용해야합니다.
예를 들어, "https://myblog.com/cs/network.html#posts"이라는 문자열이 있다면, 여기서 전체 문자열은 URL에 해당하고, 위치까지를 나타내는 "https://myblog.com/cs/network.html"는 URL에, 프로토콜을 빼고 자원을 특정하는 "myblog.com/cs/network.html#posts"는 URN에 해당합니다.

### **14. DNS에 대해 설명해 주세요.**

- **DNS는 몇 계층 프로토콜인가요?**
- **UDP와 TCP 중 어떤 것을 사용하나요?**
- **DNS Recursive Query, Iterative Query가 무엇인가요?**
- **DNS 쿼리 과정에서 손실이 발생한다면, 어떻게 처리하나요?**
- **캐싱된 DNS 쿼리가 잘못 될 수도 있습니다. 이 경우, 어떻게 에러를 보정할 수 있나요?**
- **DNS 레코드 타입 중 A, CNAME, AAAA의 차이에 대해서 설명해주세요.**
- **hosts 파일은 어떤 역할을 하나요? DNS와 비교하였을 때 어떤 것이 우선순위가 더 높나요?**

### **15. SOP 정책에 대해 설명해 주세요.**

- **CORS 정책이 무엇인가요?**
- **Preflight에 대해 설명해 주세요.**

### **16. Stateless와 Connectionless에 대해 설명해 주세요.**

- **왜 HTTP는 Stateless 구조를 채택하고 있을까요?**
- **Connectionless의 논리대로면 성능이 되게 좋지 않을 것으로 보이는데, 해결 방법이 있을까요?**
- **TCP의 keep-alive와 HTTP의 keep-alive의 차이는 무엇인가요?**

### **17. 라우터 내의 포워딩 과정에 대해 설명해 주세요.**

- **라우팅과 포워딩의 차이는 무엇인가요?**
- **라우팅 알고리즘에 대해 설명해 주세요.**
- **포워딩 테이블의 구조에 대해 설명해 주세요.**

### **18. 로드밸런서가 무엇인가요?**

- **L4 로드밸런서와, L7 로드밸런서의 차이에 대해 설명해 주세요.**
- **로드밸런서 알고리즘에 대해 설명해 주세요.**
- **로드밸런싱 대상이 되는 장치중 일부 장치가 문제가 생겨 접속이 불가능하다고 가정해 봅시다. 이 경우, 로드밸런서가 해당 장비로 요청을 보내지 않도록 하려면 어떻게 해야 할까요?**
- **로드밸런서 장치를 사용하지 않고, DNS를 활용해서 유사하게 로드밸런싱을 하는 방법에 대해 설명해 주세요.**

### **19. 서브넷 마스크와, 게이트웨이에 대해 설명해 주세요.**

- **NAT에 대해 설명해 주세요.**
- **서브넷 마스크의 표현 방식에 대해 설명해 주세요.**
- **그렇다면, 255.0.255.0 같은 꼴의 서브넷 마스크도 가능한가요?**

### **20. 멀티플렉싱과 디멀티플렉싱에 대해 설명해 주세요.**

- **디멀티플렉싱의 과정에 대해 설명해 주세요.**

### **21. XSS에 대해서 설명해 주세요.**
  
  Answer:
  Cross site scripting
XSS는 게시판이나 웹 메일 등에 자바 스크립트와 같은 스크립트 코드를 삽입해서 개발자가 고려하지 않은 기능이 작동하게 하거나,  쿠키나 세션 토큰등의 민감한 정보를 탈취하는 공격입니다.
대부분의 웹 해킹 공격과는 다르게 클라이언트를 대상으로 한 공격입니다.
이러한 공격은 웹 애플리케이션이 사용자로부터 입력받은 값을 제대로 검사하지 않고 사용할 경우 발생하게 됩니다.

- **CSRF랑 XSS는 어떤 차이가 있나요?**
  
  Answer:
  CSRF는 사용자가 자신의 의지와는 무관하게 공격자가 의도한 행위(수정, 삭제, 등록 등)를 특정 웹사이트에 요청하게 하여 공격하는 방법을 말합니다.
    XSS가 클라이언트가 서버를 신뢰하는 점을 노린 공격이라면, CSRF는 서버가 웹 브라우저(클라이언트)를 신뢰하는 상태를 노린 공격 방식입니다. 사용자가 웹 사이트에 로그인한 상태로 CSRF 공격 코드가 삽입된 페이지를 열면, 공격 대상이 되는 웹 사이트는 공격 명령이 신뢰하는 사용자(로그인된 사용자)로 부터 발송된 것으로 판단하여 공격에 노출되는 것입니다.


- **XSS는 프론트엔드에서만 막을 수 있나요?**
  Answer:
  아니요. 웹 서버의 응답 헤더에 Content-Security-Policy 헤더를 추가하여 XSS 공격을 막을 수 있습니다 헤더에 "Content-Security-Policy: 설정할 정책 내용"을 적어주면 됩니다. CSP 헤더를 받은 사용자 브라우저는 허용 목록에 있는 도메인에서 수신한 스크립트만 실행하고 그 외 스크립트는 무시하는 방식으로 XSS 공격을 방지할 수 있습니다. CSP 헤더의 경우, 정책의 내용을 직접 적어주어야 하기 때문에 올바르지 않은 정책을 적을 경우 공격을 막을 수 없으므로 정책 내용을 올바로 적는 것이 중요합니다.




### **22. HTTPS 는 HTTP 와 어떻게 다른가요?**

H

- **HTTP 프로토콜은 어떻게 작동하나요?**

- **HTTPS 프로토콜은 어떻게 작동하나요?**

- **TLS 기술은 무엇인가요?**

### **23. REST API 는 무엇인가요?**
  Answer:
  REST API를 이해하기 위해선 REST에 대한 설명이 필요합니다. REST(Representational State Transfer)란 HTTP URI를 통해 자원을 명시하고, HTTP Method(POST, GET, PUT, DELETE, PATCH) 등을 통해 해당 URI가 가리키는 자원에 대해 CRUD Operation을 적용하는 것을 말합니다.
  REST API란 REST의 원리를 따르는 API를 의미합니다. REST API를 올바르게 설계하기 위해서는 지켜야하는 몇가지 규칙이 있습니다.
  - URI는 동사보다는 명사를, 대문자 보다는 소문자를 써야합니다.
  - URI의 마지막에 '/'를 넣지 않습니다
  - URI는 언더바 대신 하이픈을 사용합니다.
  - 파일확장자(.jpg 등)는 URI에 포함시키지 않습니다.
  - URI에는 행위를 포함시키지 않습니다.(예를들어 '.../delete-post/1' 이라고 할 필요없이 '.../post/1' 이런식으로 작성합니다.)

### **24. 토큰 기반 인증 과 쿠키 / 세션 이용한 인증의 차이는 무엇인가요?**
  Answer: 세션을 이용한 인증은 사용자가 아이디, 비밀번호 같은 인증 정보를 서버에 요청으로 보내면 서버는 해당 인증 정보를 확인하고 제대로 된 인증 정보라면 해당 정보를 저장한 세션을 생성하고 그 세션 아이디를 클라이언트에게 응답으로 전달합니다. 그러면 클라이언트는 그 세션 아이디를 쿠키에 저장해놓고 서버에 요청을 보낼 때마다 같이 전송합니다. 요청과 함께 전송된 세션 아이디로 세션은 해당 클라이언트의 인가를 처리합니다.
    JWT와 같은 토큰 기반 인증은 사용자가 아이디, 비밀번호 같은 인증 정보를 서버에 요청으로 보내면 서버가 해당 정보를 확인하고 인증 정보와 서버의 시크릿 키를 더해서 특정한 암호화 방식으로 암호화한 결과를 토큰에 저장하여 클라이언트에 보냅니다. 클라이언트는 그 토큰을 쿠키 또는 로컬 스토리지에 저장하고 서버에 요청을 보낼 때마다 함께 전송합니다. 서버는 요청과 함께 전달된 토큰에서 암호화된 부분을 복호화하여 인증 서버의 시크릿 키와 비교하여 해당 토큰이 위조, 변경된 것인지를 확인할 수 있습니다. JWT의 경우, 헤더, 페이로드, 시그니처 세 부분으로 나뉘어 있는데, 헤더에는 암호화 알고리즘이 명시되어 있고, 페이로드에는 인증에 필요한 정보, 그리고 시그니처에는 헤더의 내용, 페이로드의 내용, 시크릿키를 더하여 헤더에 명시되 암호화 방법으로 암호화한 결과가 들어있습니다. 서버는 시그니처 부분을 복호화하여 해당 JWT가 위조되었는지 확인합니다.
      세션 방식의 로그인은 인증 정보를 서버가 직접 관리하기 때문에 토큰 기반 방식보다 보안면에서 더 안전합니다. 하지만 세션을 저장할 저장소가 필요하므로, 세션이 늘어날 경우 서버에 부하가 생길 수 있습니다. 토큰 방식의 로그인은 인증 정보가 들어있는 토큰이 클라이언트 쪽에 저장되어 있어 세션 방식보다는 보안상 덜 안전할 수 있지만, 시그니처 부분을 통해 위조되었는지를 확인할 수 있으며 서버에 별도의 저장공간이 필요하지 않습니다. 단, 토큰의 길이가 길어지게 되면 요청을 보낼 때 네트워크 부하가 생길 수 있습니다.

### **25. OpenAI API 를 stream 방식으로 사용한다면, 서버와 클라이언트는 어떤 프로토콜을 사용하여 통신하는 것이 좋을까요?⭐️**

- **서버 - 클라이언트가 소통하는 프로토콜에는 어떤 방법이 있나요 ? HTTP 방식 말고 다른 방식도 설명해보세요.**

- **그렇다면 마이크로서비스 형태에서 서로 다른 서버끼리 소통하는 상황을 봅시다. 이때는 서버끼리 어떠한 형태의 프로토콜을 사용해서 소통하는 것이 좋을까요?**

- **만약 클라이언트에서 10초가 지나면 무조건 timeout 이 된다면, 서버가 API 에 요청을 보내 10초 이상 기다린 후 response 받은 것을 어떤 방식으로 클라이언트에게 알려줄 수 있을까요? 프로토콜을 설계해도 됩니다.**

### 26. 127.0.0.1 은 특별한 IP 주소입니다. 이 IP 주소의 의미는 무엇인가요?

- **로컬호스트 주소는 어떤 용도로 사용되나요?**

### 27. form-data 와 x-www-form-urlencoded 의 차이는 무엇인가요?