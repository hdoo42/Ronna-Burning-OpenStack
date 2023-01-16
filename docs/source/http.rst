===========
HTTP
===========


개요
----------
Hypertext Transfer Protocol의 약자. 
W3(World wide web) 상에서 정보를 주고받기 위한 통신 규약(Protocol)이다.
모든 데이터를 텍스트(ASCII)로 주고 받는다.
// TODO: add RPC, API(interface)

메시지 포맷
---------------------
요청과 응답은 모두 헤더와 콘텐츠로 이루어진다. 
헤더의 첫 줄은 특별한 의미를 가진다.
헤더에서 Content-Type을 통해 콘텐츠의 타입을 명시할 수 있다. 
주로 쓰는 타입에는 html, json 등이 있다. 
콘텐츠에 두 줄 이상 개행이 들어가면 끝이라는 뜻이다.

.. mermaid::

    ---
    title: Request / Response Message
    ---
    classDiagram
        note "From Client to Server"
        Request --|> Server
        note for Request "status line: \nrequest method, requested URL, "
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

HTTP 프로토콜의 전송은 텍스트를 기반으로 한다. 즉 클라이언트와 서버의 HTTP 통신은 텍스트 파일을 주고받는다.
API는 사용자가 어떤 프로그램이 제공하는 기능을 사용할 수 있도록, 프로그램이 제공하는 소통 창구라고 말할 수 있다.
API를 사용하면 표준화가 쉬워진다. 프로그램이 요구하는 API 형식에만 맞춰서 요청을 보내면 되기 때문이다.
HTTP를 사용하여 API를 만들 수도 있다. (HTTP를 사용하지 않는 API도 존재한다. 대표적으로 MQTT가 그렇다.)
HTTP를 사용한 API의 대표적인 형태로, REST API가 있다. REST API는 HTTP의 장점을 최대한 활용하고자 하는 목표를 가지고 만들어졌다. 일반적으로 HTTP API와 REST API는 비슷한 의미로 사용되고 있다.


RPC
--------------
원격 프로시저 호출(Remote Procedure Call)의 약자이다. 주로 HTTP를 이용하여 API 콜을 통해 서버에 정의된 함수(프로시저)를 실행한다.
일반적으로 프로그램은 자기 자신의 주소 공간에 있는 함수만을 호출할 수 있지만, RPC를 사용하면 주소 공간의 제약 없이 다른 프로그램의 함수를 자유롭게 사용할 수 있다.

응답 코드
-------------
100번대 - informational response

200번대 - success

300번대 - redirection 
    리다이렉션은 주로 대체할 URL을 제시한다. 서버에서 정적인 파일 소개가 아니라 정의된 동작(script 등)을 통해 응답하는 경우가 많다.

400번대 - client errors

500번대 - server errors

참고자료
--------
- `API, HTTP API, REST API 차이 <https://bentist.tistory.com/37>`_
- `HTTP/1.1 example of request / response transaction <https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Response_status_codes>`_ 
