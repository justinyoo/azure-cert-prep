---
title: AZURE202x Microsoft Azure Virtual Machines - Module 4
date: 2017-01-12 11:03:27
tags: azure202x
permalink: azure202x-microsoft-virtual-machines-module-4
---

> [https://openedx.microsoft.com](https://openedx.microsoft.com) 에서 제공하는 무료 강좌인 [Microsoft Azure Virtual Machines](https://openedx.microsoft.com/courses/course-v1:Microsoft+AZURE202x+2016_T1/about) 의 모듈 4 부분에 대한 정리입니다.


## VM Disk Types ##

* All VMs have at least 2 disks - OS disk and temp disk. They can have 1+ data disk
* Disk are stored as .vhd and up to 1023GB
* OS disk: SATA drive and labelled as C by default
* Temp disk: labelled as D by default and for storing `pagefile.sys`
* Data disk: SCSI drive and labelled with my choice, stored in BLOB storage
* Depending on VM size, temp disk size and number of data disk are determined


## VM Disks Management ##

* Attach, remove or modify data disk
* Modify settings
  * caching behaviour
  * size
* Storage spaces in VMs
  * Increase I/O throughput
  * Volume larger than 1TB
* Through portal
* Through PowerShell &ndash; `Add-AzureDataDisk` (ASM), `Add-AzureVMDataDisk` (ARM)
* Good to know
  * VM size determines number of data disks to Attach
  * Premium storage needs DS/FS/GS series VM
  * New/empty disk is created when attaching
  * When attaching, `name`, `type`, `size`, `location` and `caching` needs to be provided
  * Stored as .vhd files in blob storage
  * .vhd disk should already exist when attaching the existing disk

## Disk Import & Export ##

* Useful to move large amount of data from on-prem hard disk to Azure blob storage (or vice-versa)
* Scenario:
  * Large amount of data migration to cloud
  * Content distribution
  * Backup
  * Data recovery
