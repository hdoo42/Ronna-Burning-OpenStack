Cloud
=====

Essential Characteristics:
---------------------------

**On-demand self-service**
    A consumer can unilaterally provision computing capabilities, such as
    server time and network storage, as needed automatically without requiring human
    interaction with each service provider.

**주문형 셀프 서비스**
    소비자는 각 서비스 공급자와 사람이 상호 작용할 필요 없이 필요에 따라 자동으로 서버 시간이나 네트워크 스토리지와 같은 컴퓨팅 기능을 일방적으로 프로비저닝할 수 있습니다.
    따라서 사용자는 간단한 인터페이스만으로도 클라우드의 자원에 접근하고 사용할 수 있습니다.

**Broad network access**
    Capabilities are available over the network and accessed through standard
    mechanisms that promote use by heterogeneous thin or thick client platforms (e.g.,
    mobile phones, tablets, laptops, and workstations).
    
광범위 네트워크 엑세스
-----------------
    네트워크를 바탕으로 서비스 기능이 제공되며, 여러 플랫폼에 적용되는 표준 메커니즘을 통해 컴퓨팅 자원에 접근할 수 있습니다.

**Resource pooling**
    The provider’s computing resources are pooled to serve multiple consumers
    using a multi-tenant model, with different physical and virtual resources dynamically
    assigned and reassigned according to consumer demand. There is a sense of location
    independence in that the customer generally has no control or knowledge over the exact
    location of the provided resources but may be able to specify location at a higher level of
    abstraction (e.g., country, state, or datacenter). Examples of resources include storage,
    processing, memory, and network bandwidth.

리소스 풀링
-------------
    공급자는 다수의 소비자에게 다중 테넌트 모델을 통해 서비스를 제공하기 위해 리소스를 풀링합니다. 
    고객은 일반적으로 제공된 리소스의 정확한 위치에 대한 통제권이나 지식이 없다는 점에서 위치 독립성이 있습니다.
    하지만 더 높은 수준의 추상화(예: 국가, 주 또는 데이터 센터)에서 위치를 지정할 수 있는 경우도 있습니다. 
    리소스의 예로는 스토리지, 프로세싱, 메모리 및 네트워크 대역폭이 있습니다. 

Q. multi-tenant가 뭔가요?

    소프트웨어 멀티테넌시는 단일 소프트웨어 인스턴스가 서버에서 실행되고 여러 테넌트에게 서비스를 제공하는 소프트웨어 아키텍처입니다.

Q. 리소스 풀링이란 뭔가요?

    리소스 풀링(Resource Pooling)이란, 서버나 스토리지 등의 자원을 미리 확보하고 이를 사용자 요청에 따라 제공한다는 개념 혹은 이를 확보해놓은 가상적인 공간을 의미합니다.
    풀링과 반대되는 개념은 스트리밍(Streaming)입니다. 각 개념에 대해, 풀링을 저수지의 연못으로, 스트리밍을 우물에서 물을 길어 오는 것으로 비유할 수 있습니다.
    만약 사용자가 물을 필요로 하는 경우(즉, 자원이 필요한 경우), 저수지의 둑을 개방하여 사용자가 원하는 만큼 물을 제공하는 방식을 풀링이라고 말할 수 있습니다. 반대로 우물에서 물을 길어 올려 사용자에게 제공하는 방식을 스트리밍이라고 말할 수 있지요.
    풀링은 사용자가 자원의 물리적 위치 및 상태를 고려하지 않아도 원하는 순간에 자원을 할당받을 수 있다는 장점이 있습니다. 하지만 서비스 제공자가 저수지처럼 충분한 물리적 공간을 확보하고 있어야 한다는 조건이 필요합니다. 또한 많은 사용자가 동시에 자원을 사용하는 경우, 자원이 고갈되지 않도록 주의해야 합니다. 
    반대로 스트리밍은 사용자가 요청하는 순간 자원을 생성하여 제공하기 때문에, 리소스 풀링과 대비하여 추가적인 비용이 발생한다는 단점이 있지만, 서비스 사용자가 보다 적은 자원으로도(저수지처럼 커다란 자원을 미리 할당할 필요가 없지요) 사용자에게 서비스를 제공할 수 있다는 장점이 있습니다.


**Rapid elasticity**
    Capabilities can be elastically provisioned and released, in some cases
    automatically, to scale rapidly outward and inward commensurate with demand. To the
    consumer, the capabilities available for provisioning often appear to be unlimited and can
    be appropriated in any quantity at any time.

빠른 탄력성
-------------
기능을 탄력적으로 *프로비저닝* 및 해제할 수 있으며 경우에 따라 자동으로 수요에 따라 외부 및 내부로 빠르게 확장할 수 있습니다.
소비자에게 프로비저닝에 사용할 수 있는 기능은 종종 무제한으로 보이며 언제든지 수량에 관계없이 사용할 수 있습니다.

Q. 프로비저닝이란?
프로비저닝(provisioning)은 사용자의 요구에 맞게 시스템 자원을 할당, 배치, 배포해 두었다가 필요 시 시스템을 즉시 사용할 수 있는 상태로 미리 준비해 두는 것을 말한다.

Q. 탄력성이란?
탄력성(elasticity)은 어떤 상황에 유연하게 대처하는 성질을 의미합니다. 탄력성 있는 클라우드 플랫폼은 소비자의 요구에 따라 자원을 유연하게 제공할 수 있습니다.


**Measured service**
Cloud systems automatically control and optimize resource use by leveraging
a metering capability at some level of abstraction appropriate to the type of service (e.g.,
storage, processing, bandwidth, and active user accounts). Resource usage can be
monitored, controlled, and reported, providing transparency for both the provider and
consumer of the utilized service.

서비스 측정
-------------
클라우드 시스템은 서비스 유형(예: 스토리지, 처리, 대역폭 및 활성 사용자 계정)에 적합한 추상화 수준에서 측정 기능을 활용하여 리소스 사용을 자동으로 제어하고 최적화합니다.
리소스 사용을 모니터링, 제어 및 보고할 수 있으므로 사용된 서비스의 공급자와 소비자 모두에게 투명성을 제공합니다.
즉, 사용자는 자원을 사용한 만큼만 비용을 지불할 수 있고, 사용자는 본인의 자원 사용량을 투명하게 모니터링 할 수 있습니다.


참고 자료
-------
- `https://faculty.winthrop.edu/domanm/csci411/Handouts/NIST.pdf <https://faculty.winthrop.edu/domanm/csci411/Handouts/NIST.pdf>`_
- `클라우드 컴퓨팅이란? <https://velog.io/@dbj2000/클라우드-컴퓨팅이란>`_