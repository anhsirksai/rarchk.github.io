---
layout: post
title: "Few nuggets for Kernel Developers"
modified: 2014-09-03 15:51:14 +0530
tags: [OS,linux,kernel,survey]
image:
  feature: abstract-6.jpg
  credit: 
  creditlink: 
comments: True
share: True
description: Linux.com did a series, 30 linux kernel developers in 30 days. After reading their interviews, I sort of summarized the things that they had to say. 
---

Kernel Development Guidelines
==============================

### Essentials
+ Find a problem, understand it, and try to fix it. Even if your proposed solution is wrong, the feedback you receive will be a valuable learning experience. Rinse, repeat.
+ Read a lot of code and code reviews from other people in the community. This will help you in writing your own code or patches, in a manner that is understandable and not too hard on brains.
+ Read the documentation in the kernel tree; read the mailing lists for a while and do your best to understand the discussions and the code. 
+ Fix bugs.
+ Everyone gets rebuffed from time to time regardless of whether they've been working on the kernel for 15 minutes or 15 years.
+ coding fluently, source control tools, reviewing others' code, tool chain, troubleshooting, testing what you've written, and so on. The most important of these, and the most difficult to do well, are code review and thorough testing. Start mastering them early.
+ A young developer should find a mentor who understands and respects your working style. One of the best things you can learn from a good mentor is how to hear criticism constructively. Another important thing is how to work well with other developers. The breadth of our community is something closed source methodologies can’t touch.


### Where to start 
+ Don't get trapped in walled gardens. Unless you particularly want to work for a given vendor, don't get distracted by the short term and get sucked in to a vendor tree

+ Better tooling around kernels can be one field that you can work on, for eg. sparse can take a new helping hands. 
+ Another area that can always use additional help is testing. Adding new tests to test suites like xfstests, ltp, etc., would be a useful contribution that many would benefit from.

+ You can not push things into the kernel. They need to be pulled in. You need to convince the current maintainers that what you have will benefit them. 


#### Credits
*[Jes Sorensen, Shuah Khan 	,Steve Rostedt 	,Greg Kroah-Hartman 	,Paul McKenney 	,Frédéric Weisbecker 	,Herbert Xu 	,Chris Mason 	,James Bottomley 	,John Stultz 	,Jonathan Corbet 	,Glauber Costa 	,Stephen Hemminger 	,Steven Rostedt 	,H. Peter Anvin 	,Chuck Lever 	,Jiří Kosina 	,Laurent Pinchart 	,Jiri Slaby 	,Mauro Carvalho Chehab 	,Ben Hutchings 	,Julia Lawall 	,Martin Petersen 	,Johannes Berg 	,John Linville 	,Arnd Bergmann 	,Alan Cox 	,Paul Mundt 	,Dave Jones 	,Greg Kroah-Hartman 	,Jean Delvare 	,Sarah Sharp 	,Thomas Gleixner 	,Linus Torvalds]*





















