---
title: AZURE202x Microsoft Azure Virtual Machines - Module 1
date: 2017-01-10 13:40:11
tags: azure202x
permalink: azure202x-microsoft-virtual-machines-module-1
---

> [https://openedx.microsoft.com](https://openedx.microsoft.com) 에서 제공하는 무료 강좌인 [Microsoft Azure Virtual Machines](https://openedx.microsoft.com/courses/course-v1:Microsoft+AZURE202x+2016_T1/about) 의 모듈 1 부분에 대한 정리입니다.


## Virtual Machines On-Prem vs On-Azure ##

| 특징                                 | On-Prem | On-Azure |
| ------------------------------------ | --- | ----------- |
| Console Access to VM                 | YES | NO          |
| Genereation 2 VM                     | YES | NO          |
| VHDX                                 | YES | NO          |
| Guest OS Upgrade                     | YES | NOT SUPPORT |
| Ownership & Physical Hardware Access | YES | NO          |
| Anti-virus                           | YES | YES         |
| 1+ Virtual Network Adapter           | YES | Depends     |


## Azure VM 에 적합한 용도 ##

* Highly available service
* Unpredictable growth or short-term increased
* Spiking workloads
* Steady workloads
* Periodic workloads


## Azure VM 에 적합하지 않은 용도 ##

* Low volume or limited growth
* Regulated environment &ndash; hybrid might be suitable


## Azure VM 이 지원하지 않는 기능들 ##

* Multipath I/O
* Network Load Balancing

* 추가 소프트웨어는 별도 라이센스 비용이 필요할 수도 있음

* OS 업그레이드 지원하지 않음. 대신 추가로 이미 업그레이드 된 VM 설치후 기존 VM을 이전해야 함.

* 지원하는 Windows Server Role:
  * Application Server Role
  * Web Server Role
  * Remote Access Role
  * Windows Server Update Service Role


## Azure VM 사이즈 ##

| Level                               | Size                                                        |
| ----------------------------------- | ----------------------------------------------------------- |
| Entry Level                         | Basic_A0 - Basic_A4 and Standard_A0 - Standard_A4           |
| High Memory Entry Level             | Standard_A5 - Standard_A7                                   |
| High Performance Computing          | Standard_A8 - Standard_A11                                  |
| General Purpose Production          | Standard_D1 - Standard_D14 and Standard_DS1 - Standard_DS14 |
| High Memory and Dense Local Storage | Standard_G1 - Standard_G5 and Standard_GS1 - Standard_GS5   |

* A1 is the smallest size for production
* SQL 서버 엔터프라이즈 버전 설치를 위해서는 최소 4 코어 이상의 VM 선택
* 각 클라우스 서비스는 최대 50개의 VM 설치 가능
* [https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-windows-sizes?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#size-tables](https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-windows-sizes?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json#size-tables) 꼭 읽어볼 것
* ACU (Azure Compute Unit) 는 A1 사이즈를 100으로 놓고 다른 사이즈의 SKU를 비교함.

## Azure Cost Estimator Tool ##

* 기존 하드웨어와 장비를 15분 정도 스캔
* 가장 잘 맞는 VM 사이즈 추천
* 각 인스턴스당 30일 기준 비용 산정

