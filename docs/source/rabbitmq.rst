==========
RabbitMQ
==========

개요
-----

RabbitMQ는 오픈 소스 메시지 브로커 소프트웨어(메시지 지향 미들웨어)로, AMQP를 구현하였으며 플러그인으로 MQTT 등의 프로토콜도 지원한다.

메시지를 생산하는 생산자(Producer)가 메시지를 큐에 저장해 두면, 메시지를 수신하는 소비자(Consumer)가 메시지를 가져와 처리하는 발행-구독 모델을 따른다.

REST API를 통한 웹 기반 메시징 API를 지원한다.

.. note::

	발행-구독 모델이 뭔가요?
	
	발행-구독 모델은 비동기 메시지 모델로, 생산자가 메시지를 보내면 소비자는 구독한 특정 범주 안에서 생산자의 메시지를 받게된다.

	전통적인 클라이언트-서버 모델과는 다르게 메시지를 보내는 생산자와 메시지를 받는 소비자로 분리되어 있으며, 메시지 브로커라는 제3의 구성 요소가 생산자와 소비자 사이의 통신을 처리한다.
	 생산자와 소비자는 다음과 같이 분리되어 있다.

	- 공간 분리(Space decoupling): 생산자와 소비자는 서로의 네트워크를 알지 못하며 그 정보를 교환하지 않는다.
	- 시간 분리(Time decoupling): 생산자와 소비자는 동시에 실행되거나 네트워크로 연결되지 않는다.
	- 동기화 분리(Synchronization decoupling): 소비자는 생산자의 메시지를 기다리지 않아도 된다.
	
	메시지 브로커는 생산자로부터 수신되는 메시지를 필터링하여 소비자에게 직접 배포하며, 미들웨어 형식으로 존재한다.


.. note::

	메시지란 무엇인가요?

	메시지는 일반적으로 네트워크 송수신 과정에서 전달이 이루어지는 정보를 의미한다.
	일반적으로 메타데이터를 포함하는 Byte 배열의 형태를 가지며, header와 body로 구성된다.
	메시지에는 평문(plain text), 상태 정보(status code) 또는 명령어(command)를 포함할 수 있다.
	메시지 큐의 경우, 메시지는 생산자가 소비자에게 전송하는 정보의 일부로 여겨지며, 
	메시지의 헤더에는 메시지 브로커(message broker)가 메시지 처리에 필요로 하는 정보를 추가로 포함할 수 있다.


.. note::

	메시지 브로커란 무엇인가요?

	AMQP와 같은 비동기 프로토콜을 사용하여 네트워크, 서비스 또는 어플리케이션을 연결하는 소프트웨어이다.
	 메시지 브로커는 주로 메시지 큐를 추가하거나, 메시지를 빠르게 큐잉하는 작업을 처리하며, 메시지 큐의 특성 상 관계형 데이터베이스보다 높은 처리량을 요구하기에, 지속적으로 안정적인 통신 상태를 유지해야 한다.
	 이 외에도 권한 관리, 메시지 검증, 작업 실패 시 복구 그리고 서로 다른 생산자와 소비자의 통신을 위해 유동적으로 통신 프로토콜을 조정하는 기능을 가져야 한다.
	 대표적인 메시지 브로커로 RabbitMQ, Apache Kafka, Redis, Amazon SQS 그리고 IBM MQ가 있다.

AMQP
-----

AMQP(Advanced Message Queue Protocol)는 메시지 지향 미들웨어를 구현하기 위한 개방형 표준 응용 계층 프로토콜이다.

AMQP 이전의 MQ 소프트웨어들은 플랫폼 종속적이였으며, 서로 다른 이들이 중간에 메시지 포맷을 변경하거나 시스템을 통일시켜야 하는 불편함이 존재했다.
AMQP는 네트워크로 전송되는 명령어를 표준화하고 브로커와 클라이언트 사이의 전송방식을 통일하여 MQ 소프트웨어를 구현하기 위한 메시지 브로커의 기준을 세웠다.

AMQP에서 정의한 기능은 메시지 지향, 큐잉, 라우팅(P2P 및 발행-구독), 신뢰성, 보안이 있다.


RabbitMQ(AMQP)의 구조
---------------------

.. image:: images/AMQP.png
	:width: 600
	:alt: AMQP Model

- Exchange
	- 생산자로부터 수신한 메시지를 적절한 Queue 또는 Exchange로 분배하는 라우팅 기능을 수행한다.
	- Exchange는 여러개가 존재할 수 있으며 Exchange 끼리 상하 관계를 가질 수도 있다.

- Queue
	- 메모리나 디스크에 메시지를 저장하고, 그것을 소비자에게 전달하는 기능을 수행한다.
	- 소비자는 메시지를 수신하기 위해 Queue를 실시간으로 리스닝한다.
  	- AMQP는 이러한 Queue를 소비자의 수만큼 두어 효율을 높게 한다.
	- 각 Queue는 관심있는 메시지 타입을 가진 상위 Exchange와 결속(binding)된다.

.. note::

	왜 큐를 소비자 수 만큼 두는 것이 효율이 높은가요? (참조: MPSC, Multi-Producer Single-Consumer Wait-Free Queue)
	메시지 관리를 위한 자료구조의 접근에서 lock을 사용하게 되고, 이로 인해 메시지를 가져올 때 한 단위 시간에 한 소비자만 접근할 수 있게 되어 필연적으로 대기열이 생기게 됩니다.
	부하를 분산하기 위해서 토픽 단위로 분류한다고 하더라도 관심이 있는 소비자의 조회수를 확인할 필요가 있으므로 결국 성능이 저하됩니다.
	하지만 소비자

	.. // TODO 큐의 구조 확인하는 방법이 무엇일까...


.. note::

	리스닝(Listening)과 폴링(Polling)의 차이점은 무엇인가요?

	메시지 리스닝은 메시지가 큐에 도착하자 마자 해당 메시지를 가져오는 방식을 의미하고, 
	메시지 폴링은 일정한 간격을 두고 메시지 큐를 확인하여, 메시지가 존재하면 가져오는 방식을 의미한다.
	따라서, 메시지 폴링 방식은 메시지가 오지 않는 빈 메시지 큐를 오래 확인하게 된다면, CPU 자원을 낭비하게 될 수 있다.

	여담으로, 풀링(Pulling)은 큐에 메시지가 존재하던 말던 상관없이, 
	큐에서 메시지를 가져오는 작업을 강제로 진행한다는 점에서 폴링과 차이점이 있다.


.. note::

	큐를 소비자 수 만큼 두는 것이 추천되는 이유는 무엇인가요?

	만약 하나의 메시지 큐에 여러 소비자가 연결되어 있다면, 하나의 소비자가 큐를 읽을 동안 다른 소비자들은 블록 상태에 빠지게 된다.
	또한 여러 개의 CPU 코어로 구성된 서버에 보다 효율적으로 


.. note::

	메시지 큐에서 로드 밸런싱을 어떻게 진행하나요?


- Binding
	- 각 Queue(또는 Exchange)를 상위 Exchange로 연결하는 것이다.
	- 상위 Exchange는 수신한 메시지를 Binding된 Queue(또는 Exchange)에 전달한다.

- Routing Key
	- 메시지 Header에 포함하는 일종의 가상 주소로서, Exchange가 메시지를 전달할 때 결정하는 기준이 된다.

- Exchange Type
	- 메시지를 어떤 방법으로 매칭시킬지를 결정한다. 브로커는 여러가지의 Exchange Type 인스턴스를 가질 수 있다. 
		- Direct: 지정된 Routing Key와 완전히 동일한 Binding에 연결된 Queue에 메시지를 전달한다.
		- Fanout: Exchange와 Binding된 모든 곳에 메시지를 전달한다.
		- Topic: 와일드카드를 이용하여 Routing Pattern이 맞는 하나 또는 여러 곳에 전달한다.
		- Header: Key-Value로 정의된 Header 속성에 의해서 메시지를 전달한다.

MQTT
-----

MQTT(Message Queuing Telemetry Transport)는 ISO 표준 발행-구독 기반의 메시징 프로토콜이다.
IoT 등 리소스 제약이 있거나, 네트워크 대역폭이 제한되는 환경을 위해 설계되었다. TCP/IP 프로토콜 위에서 동작한다.

AMPQ와 같이 부하를 분산시키기 위한 Job Queue의 기능은 없지만, 저전력, 신뢰할 수 없는 네트워크, TCP/IP 기반이 아닌 환경에서 운용할 수 있는 장점을 가진다. 따라서 소형기기의 제어와 센서 정보 수집에 주로 사용된다.

참고자료
---------
- `Wikipedia - RabbitMQ <https://ko.wikipedia.org/wiki/RabbitMQ>`_
- `Wikipedia - AMQP <https://ko.wikipedia.org/wiki/AMQP>`_
- `velog - 메시지 큐와 프로토콜 <https://velog.io/@jun17114/%EB%A9%94%EC%8B%9C%EC%A7%80-%ED%81%90%EC%99%80-%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C>`_
- `tistory - AMQP <https://kaizen8501.tistory.com/217>`_
- `tistory - AMQP RabbitMQ <https://hyunalee.tistory.com/39#footnote_link_39_2>`_
- `AWS - MQTT <https:/ /aws.amazon.com/ko/what-is/mqtt/>`_
- `Wikipedia - MQTT <https://ko.wikipedia.org/wiki/MQTT>`_
- `joinc - MQTT <https://www.joinc.co.kr/w/man/12/MQTT/Tutorial>`_
- `소켓과 포트 뜻과 차이 <https://blog.naver.com/ding-dong/221389847130>`_
- `What's a Message Queue? <https://www.g2.com/articles/message-queue-mq>`_
- `MQTT, AMPQ <https://hyunalee.tistory.com/39>`_
- `pulling vs. polling <https://stackoverflow.com/questions/2761204/whats-the-difference-between-polling-and-pulling>`_
- `error handling in message queue - stack overflow <https://stackoverflow.com/questions/53011333/architecture-using-a-separate-queue-for-error-handling>`_
