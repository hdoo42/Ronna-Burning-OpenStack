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

1. 사용자의 신분 증명

    Keystone은 로그인한 사용자에게 신분 증명을 요구한다.

    사용자는 아이디와 패스워드를 제출하여 신분을 증명한다.

2. 범위 비지정(Unscoped) 토큰 발급

    Keystone은 인증에 성공한 사용자에게  Unscoped 토큰을 발급한다.

        Unscoped 토큰에는 아직 사용자가 이용가능한 서비스들에 대한 범위가 지정되어 있지 않다.

3. 서비스 접근 요청

    신분 증명이 완료된 사용자는 발급받은 토큰을 통하여 자신이 접속 가능한 Project 목록을 요청한다.

    Keystone은 사용자에게 할당된 role에 부합하는 Projext의 Endpoint 목록을 작성한다.

    Keystone은 사용자가 접속 가능한 Project 목록과, 사용자가 이용하기 원하는 Project를 확인하여, Project와 rold이 포함된 Scoped 토큰을 사용자에게 보낸다.

    범위가 지정된(Scoped) 토큰을 받은 사용자는, 토큰 내부의 Endpoint를 확인하고, 서비스에게 서비스 사용을 요청한다.

4. 토큰 검증

    서비스는 사용자가 제출한 토큰의 메타데이터 정보가 유효한지 검증하기 위해 Keystone에게 의뢰한다.

    Keystone은 서비스로부터 받은 메타데이터와 Policy Backend에 저장된 메타데이터를 비교한다.

    토큰 검증을 마친 Keystone은 결과를 서비스에게 제공한다.

    서비스는 keystone으로부터 토큰 검증을 완료하였으므로, 사용자의 요청(인스턴스 실행, 볼륨 생성…)을 수행한다.

5. 결과 보고
   
   서비스는 사용자의 요청에 대해 실행한 결과를 사용자에게 보고한다.


설치 방법
---------
설치 스펙: 
- Virtualbox version : 7.0
- Machine spec:

  - vcpu: 1 
  - memory: 16384
  - storage : 100 GB

- OS: ubuntu 22.04 lts

설치 과정

sudo apt install mariadb-client-core-10.6
mysql
sudo apt install mariadb
sudo apt install mariadb-server
ls
mysql
mysql -u root
mysql_secure_installation
sudo mysql_secure_installation
cat mysql_secure_installation
which mysql_secure_installation
cat $(which mysql_secure_installation)
vim $(which mysql_secure_installation)
mysql -uroot
mysql -uroot -p42
sudo apt install keystone
vim /etc/keystone/keystone.conf
sudo vim /etc/keystone/
sudo vim /etc/keystone/keystone.conf
su -s /bin/sh -c "keystone-manage db_sync" keystone
su keystone
sudo su -s /bin/sh -c "keystone-manage db_sync" keystone
sudo su keystone
sudo -c "su keystone"
sudo su keystone -c bash
sudo -c "su keystone"
sudo echo 123
sudo su keystone -c "bash"
echo $?
bash
sudo su
sudo vim /etc/keystone/keystone.conf
sudo su keystone -c "bash"
sudo su keystone -c "/bin/bash"
sudo su keystone -s "/bin/bash"
keystone-manage fernet_setup --keystone-user keystone --keystone-group keystone
sudo keystone-manage credential_setup --keystone-user keystone --keystone-group keystone
sudo keystone-manage bootstrap --bootstrap-password 42424242 --bootstrap-admin-url http://localhost:5000/v3/ --bootstrap-internal-url http://localhost:5000/v3/ --bootstrap-public-url http://localhost:5000/v3/ --bootstrap-region-id SeoulRegion
vim /etc/apache2/apache2.conf
sudo vim /etc/apache2/apache2.conf
service apache2 restart
sudo service apache2 restart
sudo ip l set enp0s8 up
sudo dhclient -v enp0s8
export OS_USERNAME=admin
export OS_PASSWORD=42424242
export OS_PROJECT_NAME=admin
export OS_USER_DOMAIN_NAME=Default
export OS_PROJECT_DOMAIN_NAME=Default
export OS_AUTH_URL=http://localhost:5000/v3
export OS_IDENTITY_API_VERSION=3
keystone-manage bootstrap
sudo keystone-manage bootstrap
sudo keystone-manage bootstrap --bootstrap-password 42424242
sudo apt install openstack-client
sudo apt install openstackclient
openstackclient
openstack-client
sudo apt install openstack
pip
sudo apt install python3-pip
pip install openstack-client
sudo pip install openstack-client
sudo pip install openstackclient
openstack
curl localhost:5000/v3
curl http://localhost:5000/v3
poweroff
sudo poweroff
history

이러케하면뒘

참고자료
-----------
- `tistory - keystone 개념 <https://justee.tistory.com/8>`_
- `tistory - keystone 인증 절차 <https://justee.tistory.com/29>`_
