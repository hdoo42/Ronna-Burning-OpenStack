# Ronna-Burning-OpenStack
Documentation on configuration and construction of OpenStack in 42Seoul-region

TODO
----
- Openstack의 각 Component들에 대한 지식을 Read the docs를 통해 문서화 (자세하게 문서화!)
	- keystone: Identity
	- nova: Computing resources (Compute process, Schedule)
	- neutron: Networks (외부 뿐만 아니라 내부 서비스간 까지도)
	- swift: 오브젝트 스토리지 (Key based, REST-ful)
	- cinder: 블록 스토리지 (Random access)
	- glance: Disk image 관리
	- placement: ? 아직도 뭔지 모르겠네
	- horizon: 관리용 웹 인터페이스 제공
- 개인 PC에 Openstack 서비스를 구축하여 리눅스계열 운영체제 인스턴스를 띄울수 있도록 하는 과정을 문서화
- 3-copy에 대해 자세히 알아보기
- BRTFS, XFS 알아보기
- 궁금한 개념이나 용어들은 월요일마다 문서 만들기
- 개념 설명과 더불어, 질문점을 많이 적자.
- 컨벤션 정하기.

다음 시간 할 일


오늘 할 일
	- HTTP
	- MQTT

장기 계획
- 거짓으로 출석 시간이나 평가 개수를 채우는 악성 유저를 방지할 방법도 있어야 한다.
- 평가를 인자로 사용할 경우 전체적인 평가의 질적 하락을 우려해야할 수도 있다.
- 계산식과 정책 수립을 위해서 많은 고민이 필요하다. TODO: ...
- 네트워크 용어집 만들기.
- openstack 문서의 '그 외 구성요소' 항목 보충하기.