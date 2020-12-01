---
title: Build a Deep Learning Workstation with Ubuntu 20.04
date: "2020-11-30T00:00:00Z"

reading_time: true  # Show estimated reading time?
share: false  # Show social sharing links?
profile: true  # Show author profile?
comments: true  # Show comments?

# Optional header image (relative to `static/img/` folder).
header:
  caption: ""
  image: ""
---

It has been a few months that I have not updated my web. I think it is a good time to write something just to wake up the sleeping self. This article describes my recent computer build for machine learning in a $2,000 range. Keep in mind, a custom computer build is not for everyone. If you do not have high demand for specific hardwares, there are some great services in lower prices, like Amazon AWS, Azure, and Google Cloud.      
# Hardware

The choice of hardwares depends on your needs. The tasks that I am working on are GPU-heavy. As I will only need CPU to generate some simulation dependency and preprocess data, a high-end CPU and large amount memory is not essential for me.     

There are eight componenets to a build that you must consider: CPU, GPU, memory, storage motherboard, power, case, and CPU cooler (optional). The first four are the most important to your build and should cost 80% of your budget. 
## CPU

I have a Intel i5-9600K Processor with 6 cores and up to 4.6 GHz Turbo unlocked. If you are running a single GPU, then any CPU would work. If there are multiple GPUs, then:    
1) the CPU frequency is not very important. As the frequency of modern CPUs are generally high enough, it is unlikely to be the bottleneck of performance.    
2) the number of cores in CPU should exceed the number of GPUs. Ideally, CPU cores should be twice as many as GPUs. Let's say a user works with two RTX2020 Tis, then an Intel I3 8100 with 4 cores is sufficient. If 8100 does not meet the needs, then an Intel I5 8400 with 6 cores should work fine as the user may not only use this computer for deep learning.
3) overclock is not needed in deep learning. I chose a processor with overclocking is because I occasionally run some simulations locally. If you only plan for deep learning, get a CPU without overclocking with a way lower price.    
## GPU

GPU is the heart of deep learning applications - the improvement in computational speed is HUGE! I assume you are building or updating your system for deep learning, then you should get a NVIDIA card since NVIDIA has invested a long time optimizing their GPU for artificial intelligence purpose. GTX 1070, GTX 1080, GTX 1080, and GTX 1080 Ti are fair choices for good cost/performance balance. If you want better performance, I will recommand NVIDIA 20 series.     

In general, it is hard to decide the right number of GPUs. It is sensible to start with one GPU and gradually get more on demand. When you get multiple GPUs, another problem yielded is cooling. If your GPUs are stuck in PCIe slots that are next to each other, you should consider a blower-style fans. If you ran into overheating issues, your GPUs will become slower very fast.     
## Motherboard

First of all, your motherboard should have enough PCIe ports for multiple GPUs. Keep in mind that most GPUs have a width of two PCIe slots, so make sure your motherboard has enough space to accomodate multiple GPUs. I am getting a Z390 since it supports CPU overclocking. Again, as I said in section of CPU, overclocking is not needed for deep learning, you may choose Z370 for a cheaper price.    
## RAM

The RAM does not affect the deep learning performance. However, you should have enough memory to work with GPUs comfortably. This means that the size of RAM should match the biggest your biggest GPU. For example, if you have a RTX 2080Ti that has 11G of memory, you should at least have 11G of RAM.     
## Storage

The ideal setup is to have a large and slow hard drive for datasets and a SSD for profuctivity. The hard drive is rarely a bottleneck for deep learning, however, programs start and respond more quickly with an SSD.    
## Power

Generally, you want a power that is sufficient for current use and future accomondations of all your future GPUs. You can calculate the required watts by adding up the watts of your CPU and GPUs with an additinal 10% of watts for other componenets and buffer.    
## Case

When you select your case, your case should have enough space for full-length GPUs. Check its dimensions and specifications to make sure it would accomodate your setup. It is also a cool thing to have a case with LEDs!
## Cooler