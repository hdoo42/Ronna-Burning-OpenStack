--------------
Keystone
--------------

개요
------


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
