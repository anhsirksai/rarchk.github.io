---
layout: post
title: "Containers for Everyone!"
modified: 2014-09-11 10:13:35 +0530
tags: [OS,linux,containers,docker,warden]
image:
  feature: abstract-6.jpg
  credit: 
  creditlink: 
comments: True
share: True
description: In last post, we discussed primitive features on which present container solutions are based. In this post, we take a short  overview  on the present container solutions.   
---
Container is group of processes contained in isolated environment, which can run on native host OS.

It provides different level of virtualization than KVM,Xen etc., which tries to simulate whole operating system environment. Containers are also much more faster than previous virutalization methods, as it runs on host OS. Containers are good for life, and is currently topic of great interest.

### Brief History 
The idea of containers is not new, in fact cgroups and namespace were in linux kernel since 2006. We were already using chroot and BSD jails etc. to virutalize our operations  in native space. 

But it was *Docker* that made container much of a jargon on today's nerd lingua franca. 

### LXC
1. Uses cgroups and namespace to provide net,cpu,mem,fs, deivce isolation 
2. Very basic api, been there for quite a while.

### Docker
1. Uses LXC, but integrates it with AUFS to create an image form of containment.
2. Provides tools to manage life-cycle of containers. 
3. A detailed overview on [Docker Architecture](http://www.slideshare.net/rajdeep/docker-architecturev2)  

### Others
1. Warden
	+ Uses LXC and is used in CloudFoundry Framework
	+ Each container managed by warden daemon. 
	+ overlay FS as filesystem 
2. OpenVZ
	+ Modified kernel to support container features. 
	+ Provides tool to maintain life-cycle of containers
	+ Interesting resource management *{bean counters,fair share CPU}*.
3. Google lmctfy
	+ Google re-created api to bypass semantics of cgroups.
	+ Allows intent based configuration
	+ Improves resource sharing and provides performance guarantees 	   