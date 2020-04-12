---
title: "Worst-case Execution Time Explained"
date: "2020-04-08T17:20:46+01:00"
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
  - "WCET"
#menu: main # Optional, add page to a menu. Options: main, side, footer
---

*Worst-case Execution Time (WCET)*, refers to the upper bound on the execution time of a piece of program. In hard real-time systems, where the timing requirement is stringent, WCET is needed for the purpose of validation to show that the scheduler can safely schedule the designed system even under extreme conditions.

Current research on WCET provide two approaches: (1) static analysis and (2) measurement-based analysis. Static method uses only the source code or the assembly code as its input and calculate the WCET based on an abstract model of the processor. While for measurement-based method, the execution time of each basic block is measured and the results by many experiments are then combined to calculate an execution bound.

Static analysis uses an abstract model of the processor, which is conservative in terms of timing, to give a pessimistic but safe bound. However it is not always possible to precisely model the processor and the program. This is due to the fact that modern processor architecture is designed in a way that its timing properties can be poorly predicted before run-time. The advanced features of modern processors, e.g., caches, pipelines, branch prediction, make the execution time of the program not only depend on the input data (*data-dependence*) but also based on the current context of the processor (*context-dependence*), e.g., which data is in the D-Cache and which instructions are in the I-Cache or being fetched by the pipeline.

Measurement-based approach takes the other path: it derives or estimats the actual worst-case by observing the system for a long time. One of the major problems of finding WCET using measurement-based method is the worst-case path that leads to the worst-case execution time might not happen during the period of observation. This can be compensated by inserting test anchors in the program for tracing, so the confidence of the worst-case is improved.

The argument between whether static analysis or measurement-based WCET is still ongoing. In my opinion, in no cases should we trust the WCET with over confidence. We should always keep in mind the WCET can be deficient or be too conservative and mechanisms need to be developed to handle the situation when the WCET assumption is violated without casuing the system to fail.


## References

1. Reinhard Wilhelm, Jakob Engblom, Andreas Ermedahl, Niklas Holsti, Stephan Thesing, David Whalley, Guillem Bernat, Christian Ferdinand, Reinhold Heckmann, Tulika Mitra, et al. The worst-case execution-time problem overview of methods and survey of tools. *ACM Transactions on Embedded Computing Systems (TECS)*, 7(3):36, 2008.
