Hypervisor
===========

.. _Hypervisor:

Hypervisor란
-------------

하이퍼바이저(Hypervisor)란 호스트 컴퓨터에서 다수의 운영 체제를 동시에 실행하기 위한 논리적 플랫폼 또는 소프트웨어를 말합니다.
가상 머신 모니터(VMM, Virtual Machine Monitor, Virtual Machine Manager)라고도 합니다.
하이퍼바이저가 하나 이상의 VM(가상 머신)을 실행하는 컴퓨터를 Host Machine 이라고 하고, 각 VM을 Guest Machine 이라고 합니다.
하이퍼바이저에서 VM을 실행하려면 메모리 관리, 프로세스 스케줄러, I/O 스택 등 운영 체제 수준의 구성 요소가 필요합니다.


Hypervisor의 분류
----------------

하이퍼바이저는 하드웨어에 직접 설치해서 실행되는 Native(Bare-metal) 방식과, 일반 어플리케이션처럼 프로그램으로 설치되는 Hosted 방식으로 분류됩니다.

.. image:: ../images/Hypervisor.png
	:alt: Hypervisor Type

- Native (Bare-metal)
	- 호스트 컴퓨터의 하드웨어 위에 하이퍼바이저가 설치되어 직접 실행되고 그 위에 OS가 실행됩니다.
	- Xen, MS의 Hyper-V 등

- Hosted
	- Host OS에서 하이퍼바이저가 실행되고 그 위에 OS가 실행됩니다.
	- VMware, VirtualBox 등 대부분의 가상화 소프트웨어


출처
-----
- `Wikipedia - Hypervisor <https://en.wikipedia.org/wiki/Hypervisor>`_
- `Red Hat - Hypervisor <https://www.redhat.com/ko/topics/virtualization/what-is-a-hypervisor>`_