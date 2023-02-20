--------------
Keystone
--------------

draft
------

인증을 위한 어떤건데..?
http?
토큰을 넘겨줌?
다른 서비스와의 인증 도움?

openstack의 다른 서비스들이 keystone을 통해 인증?   


대충 LDAP도 있고...
권한도 관리하고...
그룹 같은거도 있고

개요
------
Domain: 이건 진짜 뭐지??
Role: 역할
User: 사용자 (jkong, hdoo)
Group: 그룹 (student.42seoul.kr) -> FQDN jkong@student.42seoul.kr

Group: User들을 가짐
User: Role들을 가짐
Service: Endpoint들을 가짐

Project (== tenant): 자원에 대한 그룹
Domain : User, Group, Project의 모음?ㅏㄷ
Domain : OpenStack Identity Entity (User, Group, Project)를 관리하기 위해 1대1로 대응되는 정의역 

https://docs.openstack.org/security-guide/identity/domains.html
https://www.mirantis.com/blog/mirantis-training-blog-openstack-keystone-domains/
-> 이 문서가 설명이 나름 잘 되어있는 것 같습니다...

유저는 role을 부여받아 프로젝트 내에서 작업을 진행한다. 하나의 컴퓨터 자원에는 여러 개의 프로젝트가 생성될 수 있다.
하지만, 생성된 프로젝트들을 관리할 수 있는 영역이 추가로 필요한데, 이것이 도메인이다. 도메인 내 관리자로 선정된 유저는,
도메인 내 프로젝트들을 관리할 수 있는 권한을 가진다. 하지만 이러한 유저 역시 role과 참여 프로젝트를 가진다.

(위 문서에 따르면...)
user: 요청(request)을 전달함으로써 클라우드 서비스와 소통할 수 있는 주체.
role: user의 서비스 환경 내 권한과 관리에 영향을 주는 메타데이터.
project: 자원을 모으거나 격리하는 데 사용되는 컨테이너.
domain: 위 세개를 위한 하이-레벨 컨테이너

