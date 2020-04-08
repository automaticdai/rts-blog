---
title: "The Limitations of Classical PID Controller and Its Advanced Derivations"
date: "2014-03-01T01:54:46+01:00"
description: "Example article description"
draft: false

#thumbnail: "img/placeholder.jpg" # Optional, thumbnail
#lead: "Example lead - highlighted near the title"
disable_comments: false # Optional, disable Disqus comments if true
authorbox: true # Optional, enable authorbox for specific post
toc: false # Optional, enable Table of Contents for specific post
mathjax: true # Optional, enable MathJax for specific post
categories:
  - "Control Systems"
tags:
  - "PID Control"
#menu: main # Optional, add page to a menu. Options: main, side, footer
---


> This was one of a course work during my master at the University of Sheffield.

Since founded by N. Weiner in 1947, the control theory has been evolved for more than 60 years and is still full of challenges and opportunities. The most important principle of the control theory, in my opinion, is the feedback mechanism. Without feedback and closed-loop, almost no algorithm and control technique can be implied. The idea of feedback is that by comparing the reference input and the actual output, an error signal can be obtained and then can be used by the controller to trace and eliminate the difference between the input and the output. Apart from Watt’s steam engine, one could say that the first formally implication of (negative) feedback is the amplifier invented by H.S. Black. It is a genius idea when first came out in 1927 and was proved to be an extremely useful way to solve electronic and control problems. The idea of output feedback has also been extended to state feedback and error feedback to achieve state control and estimation in more advanced control techniques.

Classical control is the foundation of control theory and it is more concentrated on analysing the stability and performance of a controlled plant. However, only linear and SISO systems have been discussed in classical control theory. Although traditional control techniques such as PID controller are still widely used in industry, they cannot handle more complex engineering scenarios such as aerospace, chemistry and biology. Another problem of classical control is that all parameters are designed and tuned based on the current system model, in which case the system will be more vulnerable to further disturbance and parameters varying.

In order to solve these problems of classical PID controller which mentioned before, more advanced approaches have been derived nowadays. If using classical approach to control a MIMO system, one should divide the system into different modes and control each mode separately. However if the system inputs and outputs are coupled with each other, it cannot be decoupled and this method will not be practicable anymore. Here comes the state-space method, which solved the limitation of classical control by using state variables. The advantage of state-space is that it can be represented by matrices and such is very computer-friendly. State-space representation is actually defined in time domain instead of frequency domain and every state can have some extend of physical meaning which gives some clues about what is happening inside a controlled plant. One milestone which makes the state-space method more practicable is the invention of Kalman filter. Kalman filter uses a series of history measurements in the presence of noise to estimate the current state of the system. Kalman filter can work as a state estimator or simply a special filter which uses the physical system model to remove the process and the measurement noise.

Optimal control method such as MPC and LQR is another derivation of classical control. In most circumstances, there are more than one possible control inputs which can drive the system to work properly, but we need is to find the optimal one. Optimal control actually transforms the control problem into an optimal problem which tries to minimise an objective function to get the best outcome. Another advantage of optimal control is that it can take constraints into consideration. One defect of PID controller is that it cannot handle system constraints like actuator saturation or output limitation. In the optimal case control, design a controller with constraints could be feasible.

It is also known that no system is constant and some parameters are likely to vary with time or to the working condition. In classical control, the controller is designed just for the current system model and thus may loss performance or even be unstable due to the system change and uncertainties. In such aspect, adaptive control or robust control may be more applicable. Both adaptive control and robust control are designed to cope with uncertainties. The difference is that adaptive control identifies the system model and changes its parameters in real-time, but robust control fixed its parameters after deployed to the plant. For the truth that adaptive control has to calculate the system model every few periods, it needs much more computational time. What’s more, since the control parameters in the adaptive controller are changing every time, it may be difficult to prove its stability.  On the other hand, the gain of robust controller has already been designed before applied to the system, so it doesn’t need to do additional calculation during the operation. Since robust controller is globally optimised and especially designed to handle uncertainties, it may not have a performance as good as other controllers. But since the real control problems are always not ideal, it is meaningful to take uncertainties and disturbance into the system model.

Some more advanced control techniques such as neural network and expert control are being discussed today. In my opinion, these new approaches have the potential to be the next generation of control theory. With the developing of computer science, it is now possible to model extremely complex networks. This kind of controller can actually take all the possible system states and its corresponding solutions into a database and each time just search for the best solution according to the current system data.  New techniques such as machine learning can also be absorbed into the controller and make the controller more flexible which can handle different control problems using a same configuration.

However, no matter how powerful the control method is, there are rarely situations where we do not need to make trade-offs. As human-beings, we always need to make decisions and balance the income and the expense. Being too greedy is like giving an infinite gain to a helicopter, which may work at the beginning but will suddenly crash whenever there is any disturbance. So push yourself while keep in mind that you have limitation. Take it easy, be adaptive to the environment and always try to get the optimal solution of your life.

## REFERENCES

1. R.C. Dorf & R.H. Bishop, Modern Control Systems (Twelfth Edition), Pearson, USA.
2. Wikipedia, Harold Stephen Black. Available at: http://en.wikipedia.org/wiki/Harold_Stephen_Black. Last accessed 26th Mar 2014
3. E.F. Camacho and C. Bordons, *Modern Predictive Control*, Springer, London, 2003
