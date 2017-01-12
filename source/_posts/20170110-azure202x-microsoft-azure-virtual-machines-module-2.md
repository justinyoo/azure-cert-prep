---
title: AZURE202x Microsoft Azure Virtual Machines - Module 2
date: 2017-01-10 23:00:00
tags: azure202x
permalink: azure202x-microsoft-virtual-machines-module-2
---

> [https://openedx.microsoft.com](https://openedx.microsoft.com) 에서 제공하는 무료 강좌인 [Microsoft Azure Virtual Machines](https://openedx.microsoft.com/courses/course-v1:Microsoft+AZURE202x+2016_T1/about) 의 모듈 2 부분에 대한 정리입니다.


## Azure VM 생성시 고려 요소 ##

* 스토리지: 가격, 지역, 설정
* 디스크: 사이즈, persistence, 캐싱
* Compute: 용량
* 가용성: 업타임 요구사항, 지역 분포, SLA, 접근성
* 비용: 스토리지, Compute

최우선적인 고려사항은 VM과 제반 리소스에 대해 얼마만큼 비용을 지불할 의사가 있는지임.


## Azure VM 생성 방법 ##

* 포탈 이용하는 방법
* ARM 템플릿 이용하는 방법
* Azure 파워셸 이용하는 방법
* 비주얼 스튜디오 이용하는 방법


## Steps Creating Azure VM via Portal ##

* VM 이미지/디스크 선택
* 중요 정보 제공 - 호스트, username/password
* 옵션 정보 제공 - 도메인 멤버쉽, 가상 네트웍, 스토리지, 클라우드 서비스, 가용성 셋
* VM 프로비저닝

## Creating Azure VM via PowerShell ##

1. Quick Mode: `New-AzureQuickVM -Windows -ServiceName "[Service Name]" -Name "[VM Name]" -ImageName "[Image]" -Password "[Admin Password]"`
1. Advanced Mode: `New-AzureVMConfig | AddAzureProvisioningConfig | Add-AzureDataDisk | AddAzureEndPoint | Add-AzureVM`


### Comparison between Methods ###

* Both support Windows and Linux VMs
* Both create VMs from image
* Both can set Availability Set, Subnet, VNet and Location/Affinity Group

* Advanced mode only:
  * Creates VM from OS disk
  * Specifies AD domain join info
  * Creates new or attaches existing disks
  * Disables Windows Update
  * Specify time zone
  * Specify static IP
  * Specify reserved IP

### ASM vs ARM ###

* ASM uses pipe for each PS commands
* ARM uses variable to run PS commands
* All ARM PS commands has `VM` on their names


## Creating Azure VM via ARM Templates ##

* Create template file
* Create parameters file
* Create resource group
* Deploy template

* ARM template file size is allowed up to 1MB
* ARM parameters file size is allowed up to 64KB


## Creating Azure VM from Custom Images ##

* Prepare VM: `sysprep`
* Prepare VM in .VHD: Generation 1 VHD, fixed size
* Create storage container
* Upload .VHD: `Add-AzureRmVhd`
* Create VM with .VHD


## Creating Azure VM for Linux ##

* Azure SLA only applies to endorsed distros
* Non-endorsed distros may run on Azure, as long as they meet requirements
* Endorsed distros
  * CentOS 6.3+
  * CoreOS 494.4.0+
  * Debian 7.9+, 8.2+
  * Oracle Linux 6.4+, 7.0+
  * RHEL 6.7+, 7.1+
  * SUSE Linux Enterprise SLES 11 SP4, SLES 12+, SLES for SAP 11.3+
  * Open SUSE 13.2+
  * Ubuntu 12.04, 14.04, 16.04
