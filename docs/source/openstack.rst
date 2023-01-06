=========
OpenStack
=========

선택한 이유
---------
 - 가장 대중적인 클라우드 프로젝트라서 지식을 쉽게 접할 수 있다.
 - 프로젝트 업데이트 및 유지보수가 활발하게 이루어지고 있다.
 - 오픈소스 프로젝트로 서비스 구축에 비용이 필요하지 않다.

OpenStack 개요
-------------

OpenStack이란 클라우드를 구축하고 관리하는 오픈소스 플랫폼으로, OpenStack이 제공하는 다양한 서비스를 조합하여 사용자의 목적에 맞는 클라우드 컴퓨팅 환경을 구성할 수 있도록 한다.

OpenStack을 사용하는 기업
---------------------

1. 국내
	- kakao - 사내 VM 제공을 위해 사용
	- NHN - 퍼블릭 클라우드 제공을 위해 사용
	- KT
2. 해외
	- Rackspace - openstack을 설립
	- Redhat - OpenStack 서비스 제공을 비지니스 모델로 삼기 위해 많은 기여

최소 구성 요소
----------

 - Keystone: Identify
	- 모든 컴포넌트의 인증을 담당하며, 사용자의 권한을 관리한다.
	- LDAP 등을 사용하여 사용자의 중앙 디렉토리 기능을 담당한다.
	Q. LDAP는 뭔가요?
	- Lightweight Directory Access Protocol의 약자이다.

 - Glance: Image
	- 인스턴스를 생성하기 위한 운영체제 디스크 이미지를 제공한다.
	Q. 인스턴스란 뭔가요?

 - Placement
	- 프로젝트에서 사용하는 리소스를 추적한다.

 - Nova: Compute
	- 인스턴스를 생성-중지하는 라이프사이클을 관리합니다.
	- 인스턴스의 컴퓨팅 스케줄링을 담당합니다.

 - Neutron: Network
	- 인스턴스에 외부 및 내부 서비스간 네트워크를 제공한다.
	- DHCP, VLAN, floating IP 등의 기능도 제공한다.

 - Cinder: Block Storage
	- 블록 스토리지 장치를 생성하고 관리할 수 있도록 백엔드를 플러그-인 할 수 있다.
	- 지원하는 백엔드로 LVM, Redhat Ceph, Redhat GlusterFS, EMC, NetApp, IBM Store Virtual, Nexnta 등이 있다.
	Q. Block Storage가 뭔가요?
		TODO: 

 - Horizon: Dashboard
	- OpenStack 환경을 운영 및 관리할 수 있는 웹 기반의 셀프 서비스 포털 인터페이스를 제공한다.
	- python기반의 Django 프레임워크로 작성되었다. OpenStack API와 Amazon Web Server API를 지원한다.
	Q. Dashboard가 뭔가요?
	Q. 셀프 서비스 포털이란 뭔가요?
	

그 외 구성요소
-----------

 - Swift: Object Storage
	- 클라우드 스토리지 소프트웨어를 제공, 간단한 API로 많은 데이터를 저장하고 검색할 수 있다.

 - Mistral: Workflow
	- 워크플로우를 관리하는 서비스. YAML 기반의 워크플로우 언어를 사용해서 작성하고 워크플로우 정의를 RESTAPI를 통해 업로드한다. 사용자는 동일한 API로 워크플로우를 시작하거나 자동화한다.

 - Ceilometer: Telemetry
	- openstack 전체 환경을 에이전트 기반으로 데이터를 수집하여 모니터링 및 사용량, 벤치마킹, 확장성, 통계 등을 제공하는 서비스이다. 이를 기반으로 단일 사용자에 대한 청구 시스템을 구현할 수 있다.

 - Trove: Database 
	- 관계형 또는 비관계형 데이터베이스 엔진을 서비스로 사용할 수 있게 한다.

 - Sahara: Elastic map reduce 
	- Hadoop 클러스터를 쉽고 빠르게 제공하는 인스턴스이다.

 - Ironic: Bare metal 
	- 가상머신 대신 베어메탈을 제공하는 인스턴스이다. 베어메탈 하이퍼바이저 API 및 베어메탈 하이퍼바이저와 상호 작용하는 플러그인 세트로 생각하는 것이 가장 좋다.

 - Zaqar: Messaging 
	- 웹 개발자를 위한 멀티 테넌트 기반의 클라우드 메시징 서비스이다. 해당 서비스는 개발자가 다양한 통신 패턴을 사용하여 SaaS의 다양한 인스턴스와 모바일 애플리케이션 간에 메시지를 보내는 데 사용할 수 있는 완전한 Restful API를 제공한다.

 - Manile: Shared file system 
	- 공유 파일 시스템을 제공한다. EMC, NetApp, Red Hat, HP, IBM, Oracle의 다양한 상용 스토리지를 지원한다.

 - Designate: DNS 
	- DNS 관리를 위한 멀티 테넌트 REST API이다. DNS 서비스를 관리하는 기능을 제공한다.

 - Searchlight: Search 
	- 멀티 테넌트 클라우드 리소스 전반에 걸쳐 확장 가능한 고급 인덱싱 및 사용자 중심의 검색 기능을 제공한다.

 - Barbican: Key manager 
	- 보안 키의 저장, 제공 및 관리를 위해 설계된 REST API이다.

 - Magnum: Container orchestration 
	- Docker Swarm, Kubernetes, Apache Mesos와 같은 컨테이너 오케스트레이션 엔진을 openstack에서 리소스로 사용할 수 있도록 제공하는 openstack 서비스이다.

 - Vitrage: Root Cause Analysis 
	- openstack 알림 및 이벤트를 구성, 분석, 및 확장하고 문제의 근본 원인에 대한 통찰력을 제공하고 직접 발견하기 전에 그것을 추론하기 위한 openstack RCA 서비스이다.

 - Aodh: Rule-based alarm actions 
	- 이 알람 서비스를 사용하면 Ceilometer 또는 Gnocchi에서 수집한 분석 및 이벤트 데이터에 대해 정의된 규칙을 기반으로 작업을 트리거할 수 있다.
