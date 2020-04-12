---
title: "Thoughts on the Future of Real-Time Systems"
date: "2018-10-29T01:54:46+01:00"
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
  - "Scheduling"
#menu: main # Optional, add page to a menu. Options: main, side, footer
---

Have being working on real-time systems for almost four years since the beginning of my PhD, I have learnt a lot from the ground up about this research field. It is also becoming more and more clear to me what is this research really about. The most essential objective of real-time systems is to have timing guarantee, in which the tasks in the system, especially with hard real-time constraints, would meet their deadlines under any circumstances at execution time.

However, I also realized the general principle behind real-time systems is slowly changing these days: instead of trying to make 100% guarantee, new methods are investigated to relax the requirement, so even a timing failure or transient CPU overload occurs, the system would still have predictable behaviour. It is not just a requirement of modern real-time systems, but also a crucial part for designing safety-critical systems in which the consequence of failure would be catastrophic.

As with emerging embedded SoCs (System-on-Chip) and NoCs (Network-on-Chips), the new heterogeneous architectures challenge traditional programming models: the involvement of a co-processor such as a dedicated FPGA accelerator or a General-Purpose GPU (GP-GPU) for parallel computing would definitely force a re-evolution of embedded real-time systems. The new capability of these hardware would boost the computation for ten times or even hundred times faster, but as a consequence the interactions between heterogeneous systems would be more complicated and require a high inter-communication bandwidth. These new architecture enable embedded systems with higher throughput, but also increase the difficulties of timing verification.

For these reasons, real-time systems need to be reinvented in a way that will have flexibilities both in task scheduling and timing verification. Current reserach on Mixed-Criticality Systems (MCS) and Feedback Scheduling gives a good starting point, but in order to fit novel applications such as self-driving, more effects still need to be made. The research of real-time systems should pace up with the rapid movement of architectures and applications, and I believe this research will keep glowing by playing its role in the new era.
