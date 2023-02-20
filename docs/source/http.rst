===========
HTTP
===========


개요
----------
Hyper-Text Transfer Protocol의 약자. 
W3(World Wide Web) 상에서 정보를 주고받기 위한 통신 규약이다.
모든 데이터를 텍스트(ASCII)로 주고 받는다.

메시지 포맷
---------------------
요청과 응답은 모두 헤더와 콘텐츠로 이루어진다.
헤더의 첫 줄은 특별한 의미를 가진다. (아래 그래프를 참조)
헤더에서 Content-Type을 통해 콘텐츠의 타입을 명시할 수 있다. 주로 쓰는 타입에는 html, json 등이 있다. `http의 모든 헤더 필드 <https://en.wikipedia.org/wiki/List_of_HTTP_header_fields#Request_fields>`_
콘텐츠 부분의 빈 줄에 개행이 오면 메시지의 끝이라는 뜻이다. (CR LF CR LF)

.. mermaid::

    ---
    title: Request / Response Message
    ---
    classDiagram
        Request --|> Server
        note for Request "a request line: \n request method, requested URL, the protocol version"
        Request : a REQUEST line
        Request : request header fields
        Request : message body - optional

        Response --|> Client
        note for Response "status line: \nrequest method, response status code, reason phrase."
        Response : a STATUS line
        note for Response "status line: \nrequest method, response status code, reason phrase."
        Response : Response header fields
        Response : message body - optional


HTTP와 API
--------------

HTTP의 전송은 텍스트를 기반으로 한다. 사실상 텍스트 파일을 주고받는 셈이다.
한편, API는 사용자가 어떤 프로그램이 자신의 기능을 사용할 수 있도록 제공하는 소통 방법의 집합이다.
또, 표준은 프로그램에서 어떤 입력을 받아서, 어떻게 작동하고, 어떤 출력을 해야하는지 정의한 집합이다.

.. note::
    표준과 API는 어떻게 다른가요? 

    표준은 규칙이고 API는 규칙이 아님. 표준은 프로그램이 갖추어야할 내용을 명시한 '문서'이고 API는 구현된 프로그램을 사용하기 위한 명령이다.
    그러므로 API는 그에 대한 표준을 가지고 있지 않을 수도 있다. 또, 표준이 있더라도 그것을 지켰을 수도 있고 지키지 않았을 수도 있다.
    예를 들어 C의 표준은 ISO에서 정하며 C99, C11 등의 버전이 있다. 그리고 이를 구현한 라이브러리인 C standard library가 API이다. `C standard library: API <https://en.wikipedia.org/wiki/C_standard_library#Application_programming_interface>`_


따라서 HTTP를 통하는 API를 만들 수 있다.
URI나 헤더, 컨텐츠 부분에 매개변수를 싣고 미리 정의한 특정한 URI 이름으로 요청을 하면, 이에 대한 응답을 하도록 하는 프로그램을 구현할 수 있다.

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

