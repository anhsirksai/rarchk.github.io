---
layout: post
title: "Mapping Hierarchies in Memory"
modified: 2014-08-25 16:43:29 +0530
tags: [OS,Survey,Memory]
image:
  feature: abstract-4.jpg 
  credit: 
  creditlink: 
comments: true
share: true
description: From perspective of data-structures, a process is nothing but a very well-thought data-structure which kernel uses in storing all details of that process. Just like, in data structure, we use *malloc, calloc or realloc*, kernel manages and allocates memory via mapping it to real memory resource, be it main memory or swap. 
---
From perspective of data-structures, a process is nothing but a very well-thought data-structure which kernel uses in
storing all details of that process. Just like, in data structure, we use *malloc, calloc or realloc*, kernel manages and allocates memory via mapping it to real memory resource, be it main memory or swap. 

### Memory Mapping Hierarchy
{% highlight bash %}
Simple Program
├── malloc(...) [In Programmer land]
    ├
    ├
    └── mmap(...) [In User land]
		├
	    ├
	    └── VMA (Virtual Memory Area) [In Kernel land]
				├
				├ RAM 
				├ Flash Storage
				├ Disks
				├ NFS
				└──	Other Storage options... [In Physical land]
{% endhighlight %}


### Virtual memory
+ every process has its own virtual address space, which spans from 0 to 2^32-1, in 32 bit systems 
+ It is managed by mmu using d.s like pagetables which maps virtual address range to process related info.

###Memory mapping
+ set of page table entries, describing the properties of a consecutive virtual address range.  
+ Each memory mapping has a start address and length, permissions and associated resources (physical pages, swap pages, file contents, and so on).
+ Creating new memory mappings allocates virtual memory, but not physical memory.
+ Memory mappings cannot overlap. 
+ Virtual address ranges for which there is current memory mapping are said to be "unmapped", and attempts
to access them generate a page fault which cannot be handled.  The page fault handler sends a Segmentation
Violation signal (SIGSEGV) to the program on any access to unmapped addresses.
+ memory mapping can be anonymous, file backed, device backed, shared, or copy on write.

####Note:
Linux intentionally leaves the first few kilobytes of each process's virtual address space
unmapped, so that attempts to dereference null pointers generate an unhandled page
fault resulting in an immediate SIGSEGV, killing the process.



###Anonymous mapping
+ this is how malloc works, and uses stack and heap to achieve allocation
+ initially, only vm is allocated, and each new page is (COW) mapped to zero page(maintained by OS).
+ so any reference will read zero only.
+ Attempts to write to the page trigger the normal (COW) mechanism in the page fault handler, allocating
fresh memory only when needed to allow the write to proceed.
+ "dirtying" anonymous pages allocates physical memory, the actual allocation call only allocates virtual memory.

###Allocation of  physical memory
+ The Linux kernel uses lazy (on-demand) allocation of physical pages.
+ Memory mappings generally start out with allocating vm, but the actual memory is allocated later by the
page fault handler.
+ Virtual pages with no associated physical page will have the read, write, and execute bits disabled in their
page table entries. This causes any access to that address to generate a page fault, interrupting the
program and calling the page fault handler.

###File backed mapping
+ mirror the contents of an existing file. 
+ When page faults attach new physical pages to such a mapping, the contents of those pages is initialized by reading
the contents of the file being mapped, at the appropriate offset for that page.
+ These physical pages are usually shared via page caching, which kernel does at the time of read.
+ Writes to file mappings created with the MAP_SHARED flag update the page cache pages, making the updated file contents
immediately visible to other processes using the file, and eventually the cache pages will be flushed to disk updating
the on-disk copy of the file.
+ Writes to file mappings created with the MAP_PRIVATE flag perform a copy on write, allocating a new local copy of the 
page to store the changes.  These changes are not made visible to other processes, and do not update the on-disk copy of the file.


###Translation Lookaside Buffer (TLB)
+ Fixed size array containing mapping of virtual address of recently used pages to their physical address.

####Notes
+ Physical memory addresses are unique in the system, virtual memory addresses are unique per-process.
+ Only the kernel uses physical memory addresses directly.  Userspace programs exclusively use virtual
addresses. 
+ lazy allocation, swapping, file mapping,  copy on write, shared memory,
defragmentation etc. are implemented using virtual memory


