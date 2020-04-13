---
title: "Introduction to Feedback Scheduling"
date: 2018-11-30T23:22:13+01:00
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
  - "Theory"
  - "Feedback Scheduling"
#menu: main # Optional, add page to a menu. Options: main, side, footer
---

Fixed-Priority Scheduling (FPS) and Earliest-Deadline-First (EDF) are the two dominating scheduling algorithms in real-time systems [1]. Over the last few decades, the industry has migrated from using time-triggered cyclic-executives into these more advanced priority-based methods.
FPS and EDF work fine in most of the circumstances. 

However, for FPS, one identified issue is that there are cases in which low-priority tasks could miss deadlines or even starve if tasks with higher-priorities overrun beyond their specified worst-case execution times. In these cases, low-priority tasks will be blocked more than expected and thus have less chance to execute their code. As a consequence, the system functionality will be critical, especially considering the truth that most of the time lower priority does not imply lower importance or lower safety critical in the context of priority-based scheduling. 
For EDF, the staving issue is alleviated. However, overloaded CPU can still produce a domino effect, in which case a chain of tasks will continuously miss their deadlines.
Furthermore, in some applications, there is Quality-of-Service (QoS) requirement, or services need to be differenced to many categories of user (normal, advanced, premium, etc.). This suggests a more flexible scheduling algorithm that could handle run-time uncertainties and satisfies resource distribution constraints.

*Feedback Scheduling* [2] are *closed-loop* schedulers that use feedback information from a run-time observor, e.g., deadline misses, CPU utilization, execution times, etc. Standard FPS and EDF are known as *open-loop* schedulers as they do not consider run-time status of the system.
The idea of using feedback in scheduling is first proposed in the form of multilevel feedback queue scheduling in general operating systems. It uses feedback mechanisms that is originally from control theory, in which systems will continuously monitor and change its workload. Using feedback scheduling, the system designer could set a target utilization for each task or each group of tasks. If the task or taskset uses more resources than its allowance, then the additional request will be rejected, or alternatively the task will have to reduce its running frequency or execution time in order to stick with its constraints. 

Hope this post explains the basis of feedback scheduling. I will introduce more details about feedback scheduling in my future posts.


## Reference
1. Liu, C.L. and Layland, J.W., 1973. *Scheduling algorithms for multiprogramming in a hard-real-time environment.* Journal of the ACM (JACM), 20(1), pp.46-61.
2. Cervin, A. and Eker, J., 2000, December. *Feedback scheduling of control tasks.* In Proceedings of the 39th IEEE Conference on Decision and Control (Cat. No. 00CH37187) (Vol. 5, pp. 4871-4876). IEEE.
