---
layout: post
title: "Gems within /proc"
modified: 2014-09-04 04:05:14 +0530
tags: [linux,OS,survey]
image:
  feature: abstract-6.jpg
  credit: 
  creditlink: 
comments: True
share: True
description: All linux processes are stored in /proc directory. In this post, we take a brief overview of /proc directory. 
---
## Structure of /proc directory 

{% highlight bash%}
/proc
├── Process Directories(PIDs) (contains info about particular process)
├   ├ fd/ -- directory of allfile descriptors
├ 	├ maps 
├ 	└ stat, statm, status -- process realted info
├	 
├── {self,bus,fs,driver,scsi,tty}
├	
├
├── net (System network statistics)
├ 	├ arp 																	
├ 	├ tcp,udp,igmp, snmp, sockstat, unix (protocols)
├ 	├ netstat, iptables, route (statistics)
├	├ dev,wireless (device info)
├   
├── irq set IRQ to CPU affinity, which allows the system 
├		to connect a particular IRQ to only one CPU
├
├── sysvipc relates to System V IPC calls for messages (msg),
├			 semaphores (sem), and shared memory (shm).
└
{%endhighlight%}    
            
        