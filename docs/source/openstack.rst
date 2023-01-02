OpenStack
=========

OpenStack을 선택한 이유
--------------------

- 오픈소스 클라우드 프로젝트 중에서 제일 대중적인 프로젝트여서 지식을 접할 수 있다
- 서비스를 구축하는데 비용이 들지 않는다 
- 프로젝트 업데이트 및 유지보수가 활발하게 이루어지고 있다
- 교육적 측면
 - OpenStack은 구축을 위해 직접 네트워크를 설정해야하는데, 그 과정에서 Born2beRoot나 NetPractice에서 배운 리눅스나 네트워크 관련 지식을 실제로 사용하며 더욱 발전시킬 수 있다. 


OpenStack 개요
-------------

오픈스택(OpenStack)이란 다양한 종류의 클라우드를 구축하고 관리하는 오픈소스 플랫폼으로, 오픈스택이 제공하는 다양한 서비스를 바탕으로 하여 사용자의 목적에 맞는 클라우드 컴퓨팅 환경을 구성할 수 있도록 한다.
오픈스택 내의 서비스들은 API(Application Programming Interface)를 사용하여 각 서비스 간 통신을 수행한다. 

.. code-block:: text
	IaaS (Infrastructure-as-a-Service)
	클라우드 인프라 서비스
	인터넷을 통해 최종 사용자에게 IT 인프라를 제공하는 형태의 클라우드 컴퓨팅
	가상화, 스토리지, 네트워크, 서버를 제공
	서비스형(as-a-Service)이라는 용어는 고객을 대신하여 클라우드 컴퓨팅 서비스를 관리한다는 의미


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

Identity (Keystone)
- 모든 컴포넌트의 인증을 담당하며, LDAP과 같은 기술을 사용하여 사용자의 중앙 디렉토리 기능을 합니다

Image (Glance)
- 인스턴스(VM)를 생성하기 위한 운영체제 디스크 이미지를 제공합니다.

Placement
- 해당 프로젝트에서 자체 리소스를 추적할 수 있습니다.

Compute (Nova)
- 인스턴스를 생성, 중지. 스케쥴링 등 인스턴스의 라이프사이클을 관리합니다

Networking (Neutron)
- 인스턴스의 네트워크를 제공하며, DHCP, VLAN, floating IP 등의 기능을 제공합니다

Block Storage (Cinder)
- 인스턴스의 저장장치인 Block을 제공합니다. Block 스토리지 장치를 생성하고 관리할 수 있도록 플러그인 가능한 드라이버 아키텍쳐 구조를 가지고 있으며, LVM, Redhat Ceph, Redhat GlusterFS, EMC, NetApp, IBM Store Virtual, Nexnta 등 스토리지를 지원합니다.

Dashboard (Horizon)
- openstack 환경을 운영 및 관리할 수 있는 웹 기반의 셀프 서비스 포탈 인터페이스를 제공합니다. openstack API, Amazon web server api를 지원합니다. python기반의 Django 프레임워크로 작성되었습니다.


그 외 구성요소
-----------

Object Storage (Swift)
- 클라우드 스토리지 소프트웨어를 제공, 간단한 API로 많은 데이터를 저장하고 검색할 수 있습니다.

Workflow (Mistral)
- 워크플로우를 관리하는 서비스. YAML 기반의 워크플로우 언어를 사용해서 작성하고 워크플로우 정의를 RESTAPI를 통해 업로드한다. 사용자는 동일한 API로 워크플로우를 시작하거나 자동화한다.

Telemetry (Ceilometer)
- openstack 전체 환경을 에이전트 기반으로 데이터를 수집하여 모니터링 및 사용량, 벤치마킹, 확장성, 통계 등을 제공하는 서비스입니다. 이를 기반으로 단일 사용자에 대한 청구 시스템을 구현할 수 있습니다.

Database (Trove)
- 관계형 또는 비관계형 데이터베이스 엔진을 서비스로 사용할 수 있게 합니다.

Elastic map reduce (Sahara)
- Hadoop 클러스터를 쉽고 빠르게 제공하는 인스턴스입니다.

Bare metal (Ironic)
- 가상머신 대신 베어메탈을 제공하는 인스턴스입니다. 베어메탈 하이퍼바이저 API 및 베어메탈 하이퍼바이저와 상호 작용하는 플러그인 세트로 생각하는 것이 가장 좋습니다.

Messaging (Zaqar)
- 웹 개발자를 위한 멀티 테넌트 기반의 클라우드 메시징 서비스입니다. 해당 서비스는 개발자가 다양한 통신 패턴을 사용하여 SaaS의 다양한 인스턴스와 모바일 애플리케이션 간에 메시지를 보내는 데 사용할 수 있는 완전한 Restful API를 제공합니다.

Shared file system (Manile)
- 공유 파일 시스템을 제공합니다. EMC, NetApp, Red Hat, HP, IBM, Oracle의 다양한 상용 스토리지를 지원합니다.

DNS (Designate)
- DNS 관리를 위한 멀티 테넌트 REST API입니다. DNS 서비스를 관리하는 기능을 제공합니다.

Search (Searchlight)
- 멀티 테넌트 클라우드 리소스 전반에 걸쳐 확장 가능한 고급 인덱싱 및 사용자 중심의 검색 기능을 제공합니다.

Key manager (Barbican)
- 보안 키의 저장, 제공 및 관리를 위해 설계된 REST API입니다.

Container orchestration (Magnum)
- Docker Swarm, Kubernetes, Apache Mesos와 같은 컨테이너 오케스트레이션 엔진을 openstack에서 리소스로 사용할 수 있도록 제공하는 openstack 서비스입니다.

Root Cause Analysis (Vitrage)
- openstack 알림 및 이벤트를 구성, 분석, 및 확장하고 문제의 근본 원인에 대한 통찰력을 제공하고 직접 발견하기 전에 그것을 추론하기 위한 openstack RCA 서비스입니다.

Rule-based alarm actions (Aodh)
- 이 알람 서비스를 사용하면 Ceilometer 또는 Gnocchi에서 수집한 분석 및 이벤트 데이터에 대해 정의된 규칙을 기반으로 작업을 트리거할 수 있습니다.