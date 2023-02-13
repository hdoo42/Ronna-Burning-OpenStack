=======
ZeroMQ
=======

개요
-----
분산/동시성 프로그래밍에서 사용하기 위한 비동기 메시지 라이브러리이다.
메시지 큐를 제공하지만 메시지 지향 미들웨어와는 달리 메시지 브로커가 존재하지 않는다. ZeroMQ의 zero는 메시지 브로커가 없다는 것을 뜻한다.


ZeroMQ의 사용
------------

:doc:`버클리 소켓`과 같은 인터페이스를 제공하므로 버클리 소켓의 또 다른 구현이라고 간주하고 사용하면 된다.
비동기 메시징에 주로 사용되는 패턴들을 모델로 일반화 해두었다.


REQ-REP 패턴
------------

요청(Request) - 응답(Reply) 패턴이다.
클라이언트가 질문하면 서버가 답변한다.


PUB-SUB 패턴
------------

발행(Publish) - 구독(Subscribe) 패턴이다.


PUSH-PULL 패턴
------------

파이프라인 구조
분할-정복 구조 (== 병렬 Fork-Join 구조)


AMQP와의 차별점
-------------

메시징 브로커가 없어서 매우 빠르지만 메시지의 전달을 보장하지 않는다.

참고자료
----------
- `Berkeley sockets <https://en.wikipedia.org/wiki/Berkeley_sockets>`_
- `AF_INET vs. PF_INET <https://www.bangseongbeom.com/af-inet-vs-pf-inet.html#fn:bgnet-2>`_
- `Sockets <https://pubs.opengroup.org/onlinepubs/009696699/functions/xsh_chap02_10.html>`_
- `MMPS <https://zguide.zeromq.org/docs/chapter2/#Missing-Message-Problem-Solver>`_