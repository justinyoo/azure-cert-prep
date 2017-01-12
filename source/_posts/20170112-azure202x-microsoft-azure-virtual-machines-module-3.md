---
title: AZURE202x Microsoft Azure Virtual Machines - Module 3
date: 2017-01-12 09:21:48
tags: azure202x
permalink: azure202x-microsoft-virtual-machines-module-3
---

> [https://openedx.microsoft.com](https://openedx.microsoft.com) 에서 제공하는 무료 강좌인 [Microsoft Azure Virtual Machines](https://openedx.microsoft.com/courses/course-v1:Microsoft+AZURE202x+2016_T1/about) 의 모듈 3 부분에 대한 정리입니다.


## Public IP Address ##

* For public-facing services
* VMs, Internet facing load balancers, VPN gateways and application gateways
* Can configure on the public IP resource
* dynamic address
  * IP is not allocated on its creation, but assigned on starting and released on stopping
* static address
  * IP is assigned on its creation, and released on deletion or on changing to **dynamic**


## Private IP Address ##

* Within Azure VNet
* To extend on-prem with VPN Gateway or ExpressRoute
* VMs, internal load balancers and application gateways
* Can configure on the network interface resource
* We can't choose a specific IP address
* dynamic address
  * default method assigned by resource's subnet via DHCP. Changes when start/stop the resource.
* static address
  * can set static with a valid IP within the resource's subnet.


## Availability Set ##

* Logical grouping of 2+ VMs to prepare planned/unplanned failures
* Availability Set Principles
  * Multiple VMs in one Availability Set for redundancy
  * Each application tier into separate Avaliability Sets
  * Load Balancer with Availability Sets combination
* Each VM in one Availability Set is placed in one update domain and two fault domains


## Update Domains ##

* To perform incremental or rolling updates during the deployment
* Set of VMs with physical hardware that can be updated/rebooted at the same time
* Only one update domain is rebooted at a time.
* 5 UD by default, but up to 20 UDs


## Fault Domains ##

* To share a common set of hardware, switches for single point of failures
* VMs in AS are placed in at least two FDs to avoid affects from hardware failures, network outages, power interruptions or software updates


## Scale Set ##

* Azure Compute resource to deploy/manage a set of **identical** VMs
* Support true auto-scale without provisioning to build large-scale targeting big compute, big data, centralised workloads
* Often integrated with Azure Insight to measure scale up/down, Load Balancer, and NAT rules to spread workload over the available VMs
* Guidelines
  * Automatically created with load balancer NAT rules to enable SSH or RDP
  * Scale Set varies between 0 and 100 VMs and easily change the number of VMs
  * Set Max/Min number of VMs and define triggers based on resource consumption
  * On scaling out, VMs are balanced across update/fault domains for maximum availability
  * On scaling in, VMs are removed with maximum availability
