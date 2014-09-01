---
layout: post
title: "Distributed File Systems"
modified: 2014-08-29 23:37:30 +0000
tags: [OS,Architecture,Cloud,HDFS]
image:
  feature: abstract-6.jpg
  credit:
  creditlink:
comments: True
share: True
description: In this brief post, we discuss general semantics and underpinnings of distributed file systems.
---

It is a unified file system, comprising of nodes located at spatially distinct locations.

#NAS (Network Attached Storage)
Attaching storage to network servers that provide file sytstems.

#SAN (Storage Area Network)
makes storage deivces availiable over network

DFS analogy can be compared to VFS
* Everyting is file and seems like locally availiable
* Can support different kinds of FS by putting a generic wrapper around them.
* Easily sharable

#DFS Perspectives:
* DATA Perspective -- maintains the contents of files
* Meta Perspective -- maintains the vairous information about files
* Open-files Perspective  -- maintains which files are open and locked.

#Component Placement:
** Where to put what ?? ** ( heavily depends on what is intended of system)
1. Access speed
2. Consistency
3. Recovery

DFS Architecture
	* Organisation
	* Nature of cooperating processes 
	* Communication paradigm 
	* Naming How is naming often handled in DFSs?
	*Synchronization What are the file sharing semantics adopted by DFSs?
	*Consistency and Replication What are the various features of client-side caching as well
                           as server-side replication?
	*Fault Tolerance How is fault tolerance handled in DFSs?

