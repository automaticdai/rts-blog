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

After being working on real-time systems for almost four years during my PhD, I have learnt so much about this research field, and it is becoming more clear to me what is this research really about. The most critical part of real-time systems is timing guarantee, in which the tasks in the system, especially with hard real-time constraints, would meet their deadlines.

However, I also realized the general principle behind real-time systems is changing these days: instead of trying to make 100% guarantee, new methods are invested to relax the requirement so even a timing failure/cpu overload occurs, the system would still have predictable behaviour. It is not just a requirement of real-time system specifications, but also a crucial part for designing safety-critical systems in which the consequence of failure would be catastrophic.

As for emerging embedded SoCs (System-on-Chip) and NoCs (Network-on-Chips), the new heterogeneous model would challenge traditional programming workflows: the involvement of a co-processor such as a dedicated FPGA accelerator or a General-Purpose GPU (GP-GPU) for parallel computing would definitely force a re-evolution of embedded real-time systems. The new capability of these hardware would boost the computation for ten times or even hundred times faster, but as a consequence the interactions between heterogeneous systems would be more complicated and require a high inter-communication bandwidth. These new architecture enable embedded systems with higher throughput, but also put challenges for timing verification.

For these reasons, real-time systems need to be reinvented in a way that will have flexibilities both in task scheduling and timing verification. Current reserach on Mixed-Criticality and Feedback Scheduling gives a good starting point, but in order to fit novel applications such as self-driving, more effects still need to be made. I hope real-time research will glow more and play its vital role.
