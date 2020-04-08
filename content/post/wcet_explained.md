---
title: "Worst-case Execution Time Explained"
date: "2020-03-29T01:54:46+01:00"
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
  - "WCET"
  - "Scheduling"
#menu: main # Optional, add page to a menu. Options: main, side, footer
---


*Worst-case Execution Time*, or **WCET**, refers to the upper bound on the execution time of a piece of program. In hard real-time systems, where the timing constraints are stringent, WCETs are needed for the purpose of validation to show that the scheduler can safely schedule the designed system even under extreme conditions.

Current research on WCET provide two approaches: static analysis and measurement-based analysis. Static method uses only the source code or the assembly code as its input and calculate the WCET based on an abstract model of the processor. While for measurement-based method, the execution time of each basic block is measured and the results by many experiments are then combined to calculate an execution bound.

One of the major problems of deriving such an upper bound is to find a worst-case path that leads to the worst-case execution time. This is difficult due to the fact that modern processor architecture is designed in a way that its timing properties can be poorly predicted before run-time. The advanced features of modern processors, e.g., caches, pipelines, branch prediction, make the execution time of the program not only depend on the input data (*data-dependence*) but also based on the current context of the processor (*context-dependence*), e.g., which data is in the D-Cache and which instructions are in the I-Cache or being fetched by the pipeline. To overcome the problem, static analysis use an abstract model of the processor, which is conservative in terms of timing, to give a pessimistic but safe bound.


## References

[1] Reinhard Wilhelm, Jakob Engblom, Andreas Ermedahl, Niklas Holsti, Stephan Thesing, David Whalley, Guillem Bernat, Christian Ferdinand, Reinhold Heckmann, Tulika Mitra, et al. The worst-case execution-time problem overview of methods and survey of tools. *ACM Transactions on Embedded Computing Systems (TECS)*, 7(3):36, 2008.
