===========
HTTP
===========


개요
----------
Hyper-Text Transfer Protocol의 약자. 
W3(World Wide Web) 상에서 정보를 주고받기 위한 통신 규약이다.
모든 데이터를 텍스트(ASCII)로 주고 받는다.

.. TODO: add RPC, API(interface)

메시지 포맷
---------------------
요청과 응답은 모두 헤더와 콘텐츠로 이루어진다.
헤더의 첫 줄은 특별한 의미를 가진다. //FIXME: 어떻게 특별한가?
헤더에서 Content-Type을 통해 콘텐츠의 타입을 명시할 수 있다. 주로 쓰는 타입에는 html, json 등이 있다. //FIXME: Content-Type 말고도 특수하게 표준에 명시된 헤더들이 있음
콘텐츠 부분의 빈 줄에 개행이 오면 메시지의 끝이라는 뜻이다. (\r\n\r\n)

.. mermaid::

    ---
    title: Request / Response Message
    ---
    classDiagram
        Request --|> Server
        note for Request "a request line: \n<request method> <requested URL> <the protocol version>"
        Request : a REQUEST line
        Request : request header fields
        Request : message body - optional

        Response --|> Client
        Response : a STATUS line
        note for Response "status line: \nrequest method,  response status code, reason phrase(), 개행으로 이루어진다."
        Response : Response header fields
        Response : message body - optional


HTTP와 API
--------------

HTTP의 전송은 텍스트를 기반으로 한다. 사실상 텍스트 파일을 주고받는 셈이다.
한편, API는 사용자가 어떤 프로그램이 자신의 기능을 사용할 수 있도록 제공하는 소통 방법의 집합이다.
또, 표준은 프로그램에서 어떤 입력을 받아서, 어떻게 작동하고, 어떤 출력을 해야하는지 정의한 집합이다.
// FIXME: 아래 수정 중
API를 사용하면 표준화가 쉬워진다. 프로그램이 요구하는 API 형식에만 맞춰서 요청을 보내면 되기 때문이다.
HTTP를 사용하여 API를 만들 수도 있다. (HTTP를 사용하지 않는 API도 존재한다. 대표적으로 MQTT가 그렇다.)
HTTP를 사용한 API의 대표적인 형태로, REST API가 있다. REST API는 HTTP의 장점을 최대한 활용하고자 하는 목표를 가지고 만들어졌다. 일반적으로 HTTP API와 REST API는 비슷한 의미로 사용되고 있다.

RPC
--------------
원격 프로시저 호출(Remote Procedure Call)의 약자이다. 주로 HTTP를 이용하여 API 콜을 통해 서버에 정의된 함수(프로시저)를 실행한다.
일반적으로 프로그램은 자기 자신의 주소 공간에 있는 함수만을 호출할 수 있지만, RPC를 사용하면 주소 공간의 제약 없이 다른 프로그램의 함수를 자유롭게 사용할 수 있다.

다른 컴퓨터의 프로세스의 함수를 호출하는 데 소켓(socket)을 이용하여도 위 기능을 수행할 수 있지만, RPC는 보다 다양한 기능을 제공하여 다른 컴퓨터와 보다 유연한 통신을 수행할 수 있다.
가령, Microsoft는 RPC를 메시지 큐 통신에 사용할 수 있도록 지원하였다(MSMQ). 또한 Microsoft Exchange 서버 통신에 RPC 암호화 정책 설정을 지원한다. 

    .. note::

        소켓이란 무엇인가요?

        소켓은 네트워크 상에서 작동하는 두 개의 프로그램의 양방향 통신을 구성하는 하나의 엔드 포인트이다.
        프로그램이 데이터를 보내거나 받기 위해선, 반드시 소켓을 열어 소켓에 데이터를 써보내거나 소켓으로부터 읽어들여야 한다.
        클라이언트가 서버의 IP 주소와 포트 번호를 알고 있다면, 해당 서버와 연결할 소켓을 열고, 서버로 연결 요청을 보낸다.
        서버가 연결을 수락하는 경우, 서버가 연 해당 포트의 소켓과 클라이언트의 소켓이 서로 연결되며, 상호 간 통신이 가능해진다.


	.. note::

		소켓과 포트의 차이점은 무엇인가요?
		
		노드(Node) : 네트워크에 연결된 모든 종류의 장치를 일컫는 용어. 네트워크 주소(IP 주소)가 할당된 노드를 호스트(Host)라고 부른다.
		포트(Port) : 네트워크 상에서 데이터를 주고받는 소켓을 식별하기 위해, 각 호스트의 프로세스가 할당받는 고유한 값.
		소켓(Socket) : 프로세스가 네트워크를 통해 데이터를 주고받기 위해 반드시 열어야 하는 창구.
		
		데이터는 프로세스 레벨에서 주고받는다. 즉, 호스트 간 데이터 전송이 이루어지기 위해선 각 호스트의 프로세스에 데이터가 전달되어야 한다.
		이러한 프로세스 간 데이터 전달의 창구 역할을 포트가 수행한다. 호스트의 프로세스는 내부적으로 포트를 할당받는다.
		그리고 각 호스트의 프로세스가 데이터를 주고받기 위해선, 호스트 모두 소켓을 열어야 한다.
        하나의 프로세스는 하나의 포트에 여러 개의 소켓을 가질 수 있다.

		소켓을 열기 위해선 호스트에 할당된 IP 주소, 포트 넘버, 프로토콜 등이 필요하며, 이 세 가지가 소켓을 정의한다.
		소켓과 포트는 모두 네트워크 연결을 바탕으로 한다. 호스트의 자체적인 서비스는 루프백 주소를 기반으로 소켓 연결을 진행하기도 한다. 

응답 코드
-------------
100번대 
    informational response

200번대
    success

300번대
    redirection 

.. note::
   리다이렉션은 주로 대체할 URL을 제시한다. 서버에서 정적인 파일 소개가 아니라 정의된 동작(script 등)을 통해 응답하는 경우가 많다.

400번대   
    client errors

500번대 
    server errors

참고자료
--------
- `API, HTTP API, REST API 차이 <https://bentist.tistory.com/37>`_
- `HTTP/1.1 example of request / response transaction <https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Response_status_codes>`_ 
- `원격 프로시저 호출 <https://ko.wikipedia.org/wiki/원격_프로시저_호출>`_
- `소켓이란 무엇인가? <https://www.daleseo.com/what-is-a-socket/>`_

