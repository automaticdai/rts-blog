---
title: "To or Not To Use a Real-Time Operating System"
date: 2020-04-11T17:22:13+01:00
description: "Example article description"
draft: true

#thumbnail: "img/placeholder.jpg" # Optional, thumbnail
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

The most often question I have being asked in real-time systesm is: *should I use RTOS in my project or not?*

Generally speaking, it is not a simple yes or no question. It is really dependent on two things: (1) Do you have complicate function requirement? and (2) Do you have timing requirement?

## What is a RTOS?


## OS vs Bare-metal


## General Purpose OS vs RTOS




Generally speaking, the performance is dependent on your definition, so it is case-by-case.
in terms of ‘general performance’ which is the processing time and average throughput, using RTOS will hardly make any difference;
in terms of response time, using RTOS can improve the worst-case and thus make the response time more consistent;
in terms of overheads that are related to the OS, using RTOS generally has less system-level services which can leave more CPU and memory capacities to user applications. However, this is strictly not an advantage, but as a consequence of the target that RTOS is designed for.
Linux is designed as a general purpose operating system. The idea of a general OS is to improve the average task throughput, instead of meeting any specific timing requirement which is crucial for RTOS. Design considerations will certainly affect its usefulness. Even RTLinux just ease the issue instead of solving it. It is still weaker in terms of predictability than an actual RTOS.