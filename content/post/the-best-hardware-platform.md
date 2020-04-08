---
title: "What is the BEST Hardware Platform Means to Me"
date: "2018-06-29T00:00:46+01:00"
description: "Example article description"
draft: false

#thumbnail: "img/placeholder.jpg" # Optional, thumbnail
#lead: "Example lead - highlighted near the title"
disable_comments: false # Optional, disable Disqus comments if true
authorbox: true # Optional, enable authorbox for specific post
toc: false # Optional, enable Table of Contents for specific post
mathjax: false # Optional, enable MathJax for specific post
categories:
  - "Embedded Systems"
tags:
  - "Microcontrollers"
#menu: main # Optional, add page to a menu. Options: main, side, footer
---

Last week I tried to make my new *Intel Galileo* running a basic 14 x 7 LED Matrix program which was working perfectly on my old *Arduino UNO*. This Intel powered opensource platform has a CPU frequency of 400MHz while the Arduino only got 16MHz. The interesting thing I found is, after I spent 3 hours to port the program to Galileo and executed it with full of expectation, the program turned out to work crappy: the LED matrix looked unstable and each pixel had a different luminance.

I expected the Galileo, which has 20 times more computational power, should have an brilliant performance and blows my Arduino two streets away. But the thing is, is it really appropriate to run a real time program on a Linux based platform? And is it fair enough to compare two platforms in one certain application?

The answer is NO, and this is exactly the motivation for me to write this article. During the last year, I had collected and played enormous platforms, either for using in my project or simply explore the features of a new platform. During this process, I realized that tools are just tools and there is no BEST platform exists. To make it clear, I will compare some of the platforms I got in hand and analysis their own advantages and disadvantages, and finally make a conclusion.

## 1. Embedded Linux Platforms

Well, apart from the aforementioned *Intel Galileo*, I got the popular *Raspberry PI* and less known *pcDuino* :

![DSC05191_out](/assets/DSC05191_out.jpg)
**Figure 1. Raspberry PI Model B**

![DSC05195_out](/assets/DSC05195_out.jpg)
**Figure 2. pcDuino version 2**

Generally speaking, these two platforms have a similar performance and functions: both are working at a high frequency, both running Linux operating system and all of them have some kind of GPIO extensions and USB connections. The Raspberry PI has a large community and no matter what problem you encountered, from running a program in desktop environment to compiling the Linux Kernel, you can find your answer. On the other hand, the pcDuino is not well supported and also not even well documented. So why I bought another Linux single board computer when I already got one? The answer is the additional Arduino connectivity of the pcDuino.

The pcDuino can seemless ‘run’ Arduino sketch locally without the need to adhere another Arduino board. Is this convenience really worth 60 pounds? Well, I think so. This design eliminates the overhead of communicating with additional hardware through serial and makes my life easier to develop more complex project where the need of hardware functions like GPIO / ADC / DAC is an essential. Apart form this aspect, I couldn’t find other difference between these two platforms, and it is also for this reason that I decided to buy one more Linux platform.

## 2. Visual Sensors

I am pretty new to computer vision and I only started to investigate different camera since the beginning of this year. What I got so far are two normal web cameras, two *PS Eye* cameras for Playstation 3 and a *Kinect* from Microsoft:

![DSC05200_out2](/assets/DSC05200_out2.jpg)
**Figure 3. My Collection of Cameras and Visual Sensors**

Among them, the *Kinect* is a star which is being used by hundreds of institutions and researchers in recent years. It is actually a stereo camera which can give you depth image of the scenario. What I have done so far is simply to configure the SDK and run some examples on *Processing*, a Java programming library for interactive user interface. It is a perfect sensor for robotics and can be used in applications such as V-SLAM, 3D reconstruction and manipulator as what has been done with the Boris, the newest robot invented by Birmingham University. The only thing that prohibits me from using it further, is the complex toolchain that it comes with. As first released only for XBox 360, it is not well support by PCs and you have to use opensource packages like *OpenNI* and the driver from *PrimeSense* to make it work.

Another idea to play with stereo vision is to use a pair of monocular cameras and I found the Sony PS3 Eye is an ideal platform for me. It is cheap (8 pounds each), fast (60 fps @ 640 x 480) and fairly easy to use. You can simply buy a SDK from the company *Code Laboratories* and you can simply use OpenCV like what you have done with other web cameras. The adjustment and configuration of two separate cameras are tricky but it is a good idea for researchers who want to have a feeling of basic principles about stereo vision. What really interested me about this camera is it is really easy to use and can also achieve a competitive frame rate compared to these professional industry cameras. It is indeed a good platform for fast object tracking, but the thing is, it is not general and you should buy a SDK before use. So if you want to make it a product for customs, it would be problematic for the software license. So sometimes we may prefer to use off-the-shelf web cameras.

If you tried different cameras, you may find there is even difference between web cameras. I bought this HP HD2300 after I got my previous Logitech C270. Why? Simply because it has a higher and crisp resolution and it has a better white balance performance which is important in vision systems for detecting color features. But why I still keep & use the Logitech C270? Well, for CPU with limited computational power (such as the Raspberry PI), higher resolution doesn’t mean higher performance but resulted in lags and failures.

## 3. Microcontrollers

I love microcontrollers, and as the natural of my job I have to deal with them a lot. I have some good platforms in this category, majorly Arduinos and STM32 development boards.

![DSC05202_out](/assets/DSC05202_out.jpg)
**Figure 4. Microcontrollers I got in my personal lab (AVRs)**

![DSC05208_out](/assets/DSC05208_out.jpg)
**Figure 5. Microcontrollers I got in my personal lab (Cortex-M3 / M4)**

For me, Arduino will do most of the job for amateur projects. Only in some cases I need to use STM32, especially when I need high performance, GUI support and require to use driver that are already written using the STM32 library.

However, Arduino is very good for fast prototyping. For a simple project, I can make it run within 10 minutes. Everything is there, IO library, device drives, and lots of tutorial and code on the Internet. The drawback of Arduino is its low performance: with a 16MHz CPU, you can't do as much as STM32 which has 72MHz and a floating point unit.

## Conclusion

As you should be able to guess now, there is no best platform. Everything has its pros and cons. Sometimes you want it to be fast and solid, but sometimes you just want it easy without too much complexity. You should always research which platform is good for your purpose. Just as I mentioned in the introduction: how could a 400MHz super power Intel chip be beaten by a 16MHz Arduino? The answer is obvious: it just doesn't fit.
