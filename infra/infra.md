## Infra

### **1. 가상화가 무엇이고, 이것이 가상머신과 어떠한 차이가 있는지 설명해 주세요.**

- **그렇다면 Docker는 둘 중 어디에 속하나요? 왜 사람들이 Docker를 많이 채택할까요?**
- **하나의 Host OS에서 돌아간다면 충분히 한 컨테이너가 다른 컨테이너에 간섭할 수 있는 위험이 있지 않을까요? 이를 어떻게 방어할 수 있을까요?**
- **Docker 위에 Docker를 올릴 순 없을까요?**
- **Docker Engine 은 무엇인가요?**

### **2. CI/CD 를 사용해 본 경험이 있나요? 있다면 간단하게 설명해 주세요.**

### **3. Web Server, Web Application Server 의 차이는 무엇인가요?**

  답변:
  웹서버
    
  - 웹 서버는 **정적인 콘텐츠**(HTML, CSS, 이미지)등을 제공하는 서버이다.
  - HTTP 프로토콜을 이용해 클라이언트에게 웹 페이지를 제공한다.
  - 웹 서버의 임무는 크게 두가지이다. 첫번째는 단순히 저장된 웹 리소스들을 클라이언트로 전달하고, 클라이언트로부터 콘텐츠를 전달받아 저장하거나 처리한다.
  - 사용자로부터 동적인 요청이 들어왔을때, 해당 요청을 웹서버 자체에서 처리하기 어렵기에 WAS에게 요청한다.
  - Apache, Nginx가 대표적이다.

  WAS(Web Application Server)
  - **동적인 컨텐츠**(웹 애플리케이션)을 처리하고 제공하는 서버이다.
  - 웹 애플리케이션 실행 및 데이터 처리, 웹 서버와 클라이언트 간의 중계 역할을 한다. 웹 애플리케이션을 실행하여 동적 콘텐츠를 생성하고 웹 서버와 클라이언트 간의 데이터 처리를 담당하는 역할을 한다. 즉, WAS 서버는 클라이언트의 요청에 따라 데이터베이스에서 정보를 가져오거나, 웹 애플리케이션을 실행하여 동적인 웹 페이지를 생성한 후 결과를 웹 서버에 전달한다. 웹 서버는 이를 받아 클라이언트에게 전달한다.
  - 톰캣이 대표적이다.



  WAS와 웹 서버를 효율적으로 사용하는 방법
      
   WAS는 DB 조회 등 다양한 로직을 처리하는데에 집중해야한다. 따라서 단순한 정적 콘텐츠는 웹 서버에게 맡기고 기능을 분리해서 서버부하를 방지해야한다.
   WAS가 정적 콘텐츠 요청까지 처리하게 되면, 부하가 커지고 동적 콘텐츠 처리가 지연되면서 수행 속도가 느려진다. 이러면 페이지 노출시간이 늘어나는 문제가 발생하게 된다.
     따라서 웹 서버를 앞단에 두고, WAS는 웹 서버가 처리하기 힘든 서버 사이드 코드의 로직을 수행하면 효율적으로 WAS와 Web Server를 활용할 수 있다.


### 4. Git에 대해 설명해 주세요.

- **여러 브랜치를 합쳐야 할 때, 어떤 방법을 사용할 수 있는지 "모두" 설명해 주세요.**
- **여러 브랜치를 합쳐야 할 때, 어떤 방법을 사용할 수 있는지 "모두" 설명해 주세요.**
