---
title: "To Use an RTOS or Not?"
date: 2020-04-13T12:22:13+01:00
description: "Example article description"
draft: false

thumbnail: "/img/cover-rtos.jpg" # Optional, thumbnail
#lead: "Example lead - highlighted near the title"
disable_comments: false # Optional, disable Disqus comments if true
authorbox: true # Optional, enable authorbox for specific post
toc: false # Optional, enable Table of Contents for specific post
mathjax: true # Optional, enable MathJax for specific post
categories:
  - "Real-Time Systems"
tags:
  - "Design"
  - "RTOS"

#menu: main # Optional, add page to a menu. Options: main, side, footer
---

> *Should I use an RTOS in my project or not?*

This is the most often question I was asked in real-time systesms. Generally speaking, there is no simple yes or no answer. In this post, I will answer this question step by step, starting by explaining what is an RTOS and when should we use an RTOS. This post is a compile of my previous answers on Quora with some other additional references.


## 1. Definition of RTOS

A real-time opeating system (RTOS) is an operating system that is designed for real-time applications, which has consistency in regarding of the time it completes a tasks after the task is ready. RTOS are widely used in industrail automation, instrumentation, telecommunications, medical, test and measurement, multimedia, defense process control, aerospace and electronics. 

Defined by the *POSIX 1003.1* standard, the real-time OS attribute of an operating system is *the ability of the operating system to provide the required service level in a short predefined response time*. Real-time operating systems are mainly used for their rapid response capability, which is not guaranteed by a general purpose operating system (GP-OS), such as Windows or Linux. The real-time capability is achieved by carefully handled task and thread execution, scheduling and resource sharing. The real-time application designed with RTOS can thus have deterministic behaviour, and the resultant system is analysable through mathematical equations. Some of the most known RTOS are uCosIII, FreeRTOS, QNX, RTEMS and WindRiver VxWorks. 


## 2. General Purpose OS vs RTOS

To understand the difference between real-time and general purpose OS, there are two aspects to consider: (1) performance; (2) features.


### 2.1 Performance Comparison

Generally speaking, there is a number of definitions of the performance of an OS:

- In terms of 'general performance', which is normally refer to the average processing time and throughput, using RTOS will hardly make any difference. Using an RTOS will not make it 'faster';
- In terms of 'response time', i.e. time elapsed after reponse to an event, using RTOS can improve the worst-case and thus make the response time more consistent;
- In terms of 'overheads' that are related to the OS, using RTOS generally has less system-level services which can increase determinism and leave more CPU and memory capacities to user applications. 


### 2.2 Features Comparison

I have produced a table to compare the key differences of GPOS and RTOS:

|                            | General purpose opearting systems (GP-OS) | Real-time opearting systems (RTOS) |
|----------------------------|-------------------------------------------|------------------------------------|
| *Applications*             | General purpose applications              | Suitable for real-time tasks       |
| *Scheduling Policy*        | Fair                                      | Cyclic Executives / FPS / EDF      |
| *Response Latency*         | High                                      | Low                                |
| *Deadline*                 | Not supported                             | Can be guaranteed                  |
| *Jitter*                   | High                                      | Low                                |
| *Synchronization*          | Semaphores, locks, mutex                  | Mainly mutex and spin-locks        |
| *Inter-Task Communication* | Pipelines, message queues, shared memory  | Similar to GP-OS                   |
| *Priority Inversion*       | Not explicitally handled                  | Can be well handled                |
| *Formal Approvable*        | No                                        | Yes                                |


## 3. Finally, when do you need an RTOS?

General purpose operating systems like Linux are not designed for any worst-case guarantees. The idea of a GP-OS is to improve the system average throughput, instead of meeting any specific timing requirement which is on the other hand, crucial for RTOS. Design considerations will certainly affect its usefulness. Even RTLinux just ease the issue instead of completed solving it, and it is still weaker in terms of predictability than an actual RTOS.

So if hard timing is a consideration in your application, then definitely RTOS is the right thing to go. However, there are also some downsides, and some of them could mean a lot. First is that RTOS does not provide a competitive 'eco-system' as good as GP-OS, most of the cases you have to build your application from the ground up without reusing some other readily libraries. Second is that to make sure timing is not violated, the programming paradigm is different and limit some of the functions you can use (e.g. self-suspension). Third, specific knowledge is needed so you need either to let engineers to learn or hire experts that have the domain knowledege. Nevertheless, designing a real-time is not an easy job and RTOS is only a small piece of it.

One misconcept of RTOS is that once RTOS is used, everything can be magically guaranteed. This is not true as using RTOS is just a necessary condition but not sufficient. A counter example is given as the Mars Pathfinder spacecraft which suffered a series of system resets due to a priority inversion flaw in 1997. More design and analysis efforts should also be put to make sure the guarantee is actually met. This is another stroy which will be covered in my future posts.


## References

1. Robomart Blog - REAL TIME OPERATING SYSTEM (RTOS). https://www.robomart.com/blog/real-time-operating-system-rtos/
2. Exploring Real-Time Operating Systems. https://www.onlogic.com/company/io-hub/exploring-real-time-operating-systems/
3. Intel. Real-Time Systems and Intel take industrial embedded systems to the next level.
4. Embedded. Introduction to Real-Time. https://www.embedded.com/introduction-to-real-time/