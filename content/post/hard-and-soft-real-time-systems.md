---
title: "Hard Real-Time and Soft Real-Time Systems"
date: "2015-04-13T01:54:46+01:00"
description: "Example article description"
draft: false

#thumbnail: "img/placeholder.jpg" # Optional, thumbnail
#lead: "Example lead - highlighted near the title"
disable_comments: false # Optional, disable Disqus comments if true
authorbox: true # Optional, enable authorbox for specific post
toc: false # Optional, enable Table of Contents for specific post
mathjax: true # Optional, enable MathJax for specific post
categories:
  - "Real-Time Systems"
tags:
  - "RTS"
#menu: main # Optional, add page to a menu. Options: main, side, footer
---


On your first lecture in Embedded Systems, you will definitely hear the term ‘hard’ real-time and ‘soft’ real-time. Systems such as avionic systems, automobile engine control systems and cardiac pacemakers could be included in the category of hard real-time systems, while web servers, human-machine interfaces and multimedia systems are soft real-time systems. By intuition, we can infer that these hard real-time systems are more critical and important than the soft ones. But what is the really distinction between them?

To answer this question, we should first introduce the notion of **timing requirements**. Timing requirements, which is also known as *timing constraints*, are metrics that specify the temporal behaviors of tasks during run-time. Two most important parameters when defining timing requirements are the **response time**, \\(R_i\\), and the **deadline**, \\(D_i\\). The deadline of a task is the time instant by which the task should be completed and the response time is the execution time between the release and the completion of the task.

Now we can give a formal definition of hard real-time: a hard real-time system is a system where all tasks in that system should be completed before their own pre-defined deadlines, i.e., \\(R_i <= D_i\\). Any failure to meet the deadline could possibly lead to disastrous consequence, e.g., chemical leakage, airplane crash or life risk.
When it comes to soft real-time systems, the deadline could be missed occasionally with the only consequence that the **usefulness of the result could be degraded**. Take the music streaming system as an example, the failure of delivering the audio steam in time will only cause some annoying lags, but will not do any harm to the person who is listening to it.

Since hard real-time systems require a high level of predictability, the specification is often given in a *deterministic* way. On the other hand, the timing specification of a soft real-time system is often defined in a *statistical* form, e.g., the probabilistic of deadline misses is less than 1%.
The high requirement of temporal behavior of hard real-time systems poses a great challenge in designing such systems. Many restrictions should be imposed on the design of the software, as well as the hardware architecture. Formal methods should also be used to prove the system could work properly under any possible conditions without any deadline miss.

In reality, not all systems can be identified as either soft or hard real-time systems. In these circumstances, the system can be separated into the hard and the soft sub-systems and be designed and verified separately, in order to meet their own specifications.


## Reference

1. Jane W. S. Liu, *Real-time Systems*, Prentice Hall, 2000, page 26-33
