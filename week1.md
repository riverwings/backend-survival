---
description: Git Book은 어렵지만 데브노트 첫 시작.
---

# 1. HTTP
#### 하이퍼텍스트 전송 프로토콜
1. 프로토콜이란 규칙의 집합, 규약
2. 애플리케이션 레이어 > OSI 7계층
3. 클라이언트-서버 모델 + 메시지 교환
4. 무상태
    a. HTTP는 각각의 요청이 독립적
    b. 즉, 클라이언트는 항상 자신이 누구인지 알려줘야 한다. > 쿠키, 세션 등
5. HTTP 메시지 (주고받는 것)
    a. 기본적으로는 사람이 읽을 수 있는 형태
    b. 요청과 응답 모두 동일 구조
      - multipart/form-data
    c. HTTP Method(요청)
      ex) POST / HTTP/1.1
      GET HEAD POST(멱등성 x) PUT PATCH(멱등성 x) DELETE OPTIONS
      - 멱등성 : 동일한 요청을 반복했을 때 일정한 값이 유지되는 것
    d. HTTP Status Code(응답)
      - 리다이렉션<br><br>


# 2. HTTP Client
인터넷 프로토콜 스위트 중 TCP/IP가 가장 많이 쓰임.

### 전송계층
  TCP, UDP 전송 계층의 대표적인 프로토콜<br>
  TCP: 연결이 필요함. 전달 및 순서 보장.(전화)<br>
  UDP: 연결하지 않고 데이터를 보냄. 전달 및 순서를 보장하지 않음.(편지)<br><br>

### Socket
 Socket과 Socket API를 구분해야 헷갈리지 않음.
 Socket은 기본적으로 파일과 유사하게 다룰 수 있다(유닉스에서는 파일 디스크립터의 일종).<br>
 Java에서는 키보드 입력, 화면 출력, 파일 입출력 등과 마찬가지로 Stream(Java 8에서 도입된 Stream API가 아님에 주의할 것.)으로 다룰 수 있다.<br><br>

### TCP 통신 순서
  1. 서버는 접속 요청을 받기 위한 소켓을 연다.
    호스트는 IP 주소 또는 도메인 이름을 사용할 수 있다.
    IP주소와 포트 번호만 알면, 서버에 접속할 수 있다.
  2. 클라이언트는 소켓을 만들고, 서버에 접속을 요청한다.
    GET / HTTP/1.1
    Host: example.com
    (빈줄)
  3. 서버는 접속 요청을 받아서 클라이언트와 통신할 소켓을 따로 만든다.
  4. 소켓을 통해 서로 데이터를 주고 받는다.
  5. 통신을 마치면 소켓을 닫는다.<br><br>

### URI와 URL
URI는 특정 리소스를 식별하는 통합 자원 식별자를 의미함.<br>
웹기술에서 사용하는 고유한 문자열 시퀀스.<br>
URL은 흔히 웹 주소라고 하며, 리소스가 어디있는지 알려주기 위한 규약.<br>
URI의 서브셋.<br><br>

### 호스트(host)
IP를 가지고 있고 양방향 통신이 가능한 컴퓨터
  - IP 주소: 인터넷상에 있는 컴퓨터의 고유한 주소
  - Domain name: 사람이 읽을 수 있음.
  - DNS: 도메인 이름을 머신이 읽을 수 있는 IP주소로 변환함.<br><br>

### 포트(port)
IP내에서 프로세스 구분을 위해 사용하는 번호이며, 포트 숫자는 IP주소가 가리키는 PC에 접속할 수 있는 채널을 의미함.<br><br>

### path(경로)
파일시스템을 통해 특정 파일에 이르는 경로<br><br>
```
public class App {
    public static void main(String[] args) throws IOException {
        App app = new App();
        app.run();
    }

    private void run() throws IOException {
        System.out.println("Hello, world!");

        // 1. Connect
        Socket socket = new Socket("example.com", 80);

        System.out.println("Connect!");


        // 2. Request
        String message = "" +
                "GET / HTTP/1.1\n" +
                "Host: example.com\n" +
                "\n";

        OutputStream outputStream = socket.getOutputStream();
        Writer writer = new OutputStreamWriter(outputStream);

        writer.write(message);
        writer.flush();

        System.out.println("Request!");


        // 3. Response
        InputStream inputStream = socket.getInputStream();
        Reader reader = new InputStreamReader(inputStream);

        CharBuffer charBuffer = CharBuffer.allocate(1_000_000);

        reader.read(charBuffer);

        charBuffer.flip(); // 해줘야만 string이 제대로 나온다.

        String text = charBuffer.toString();

        System.out.println(text);

        // 4. Close
        socket.close();
    }
}
```
<br>

# 3. HTTP Server
  Java에서는 ServerSocket이라는 별도의 클래스를 사용.<br>
  클라이언트의 접속을 기다림 > 접속하면 통신용 소켓을 따로 만들어서 돌려줌.<br>
  I/O에서 이렇게 기다리는걸 Blocking이라고 함. TCP통신에서는 네트워크 상태 같은 요인에 의해 크게 지연될 수 있고, accept처럼 상대방의 요청이 없으면 영원히 기다리는 일이 벌어질 수 있으므로 멀티스레드나 비동기, 이벤트 기반 처리 등이 필요함.<br>
  - Java ServerSocket
  - Blocking vs Non-Blocking: 다른 주체가 작업할 때 자신의 제어권 여부로 구분함.<br>
  Blocking은 제어권을 가지고 Non-Blocking은 없다.<br><br>

```
public class App {
    public static void main(String[] args) throws IOException {
        App app = new App();
        app.run();
    }

    private void run() throws IOException {
        // 1. Listen

        ServerSocket listener = new ServerSocket(8080, 0);

        System.out.println("Listen!");

        while (true) {
            // 2. Accept

            Socket socket = listener.accept();

            System.out.println("Accept!");

            // 3. Request -> 처리 -> Response

            Reader reader = new InputStreamReader(socket.getInputStream());

            CharBuffer charBuffer = CharBuffer.allocate(1_000_000);
            reader.read(charBuffer);

            charBuffer.flip();
            System.out.println(charBuffer.toString());

            // 4. Response

            String body = "hello, world!";

            byte[] bytes = body.getBytes();
            
            String message = "" +
                    "HTTP/1.1 200 OK\n" +
                    "Content-Type: text/html; charset=UTF-8\n" +
                    "Content-Length: " + bytes.length + "\n" +
                    "\n" +
                    body;

            Writer writer = new OutputStreamWriter(socket.getOutputStream());
            writer.write(message);
            writer.flush();

            // 5. close

            socket.close();
        }

//        listener.close();
    }
}
```


# 4. Java HTTP Server
  - Java HTTP Server: 내부적으로 NIO를 사용하는 고수준 HTTP 서버 API
  - Java NIO: 채널을 통해 데이터를 읽음. 기본적으로 Buffer을 사용하기에 Stream으로 데이터를 주고 받는 IO에 비해 사전작업(버퍼할당, 처리)에 소요되는 비용이 큼.
  - Java Lambda expresiion(람다식): Interface생성 후 Interface 참조변수에 람다식을 대입하여 사용
    - Java Functional interface(함수형 인터페이스): 1개의 추상 메소드를 갖고 있는 인터페이스<br>
    람다식으로 만든 객체에 접근하기 위해 사용함<br>

```
public class App {
    public static void main(String[] args) throws IOException {
        App app = new App();
        app.run();
    }

    private void run() throws IOException {
        InetSocketAddress address = new InetSocketAddress(8080);
        HttpServer httpServer = HttpServer.create(address, 0);

        HttpHandler handler;
        httpServer.createContext("/", exchange -> {
            displayRequest(exchange);

            String content = "Hello, world!\n";
            sendContent(exchange, content);
        });

        httpServer.createContext("/hi", exchange -> {
            displayRequest(exchange);

            String content = "Hi, world!\n";
            sendContent(exchange, content);
        });

        httpServer.start();
    }

    private void displayRequest(HttpExchange exchange) throws IOException {
        String method = exchange.getRequestMethod();
        System.out.println("Method: " + method);

        URI uri = exchange.getRequestURI();
        String path = uri.getPath();
        System.out.println("Path: " + path);

        Headers headers = exchange.getRequestHeaders();
        for (String key : headers.keySet()) {
            // list가 아닌 map이라서 keySet 붙여줘야 함.
            List<String> values = headers.get(key);
            System.out.println(key + ": " + values);
        }

        InputStream inputStream = exchange.getRequestBody();
        String body = new String(inputStream.readAllBytes());

        System.out.println(body);
    }

    private void sendContent(HttpExchange exchange, String content) throws IOException {
        byte[] bytes = content.getBytes();

        exchange.sendResponseHeaders(200, bytes.length);

        OutputStream outputStream = exchange.getResponseBody();
        outputStream.write(bytes);
        outputStream.flush();
    }
}
```
<br>

# 5. Spring Web MVC
  - Spring: Java 기반의 웹 어플리케이션을 만들 수 있는 프레임워크.
  - Spring Boot: Spring을 더 쉽게 이용하기 위한 도구.
  - Spring initializer: spring boot 기반으로 spring 관련 프로젝트를 생성해주는 사이트.
  - Web Server와 Web Application Server(WAS): WEB서버는 정적인 컨텐츠를 제공하는 서버이고 WAS는 동적인 컨텐츠를 제공하는 서버임.<br>
  기능을 분리하여 각 서버가 감당하는 부하를 줄일 수 있도록 함.
    - Tomcat: 자바 서블릿을 이용하여 데이터 요청에 대한 응답을 자바코드로 처리, 해당 내용을 유저에게 리턴해주는 구조.
  - Model-View-Controller(MVC) 아키텍처 패턴
  - 관심사의 분리(Seperation of Concern): MVC가 추구하는 것
  - Spring MVC: Map과 유사한 Model 인터페이스를 제공. 웹에선 Controller만으로 충분하고 Controller대신 Handler란 개념을 사용하면 됨.
  - Annotation: 후술하는 클래스, 메서드, 변수 등의 상태나 속성을 표시하기 위해 사용
    - Java Annotation
    - Spring Annotation
      - @RestController
        - @Controller
        - @ResponseBody
      - @GetMapping
        - @RequestMapping
<br>
```
@RestController
public class WelcomeController {
    @GetMapping("/")
//    @ResponseStatus(HttpStatus.NO_CONTENT)
    public String home() {
        return "Hello, world!";
    }

    @GetMapping("/hi")
    public String hi() {
        return "Hi, world!";
    }
}
```



