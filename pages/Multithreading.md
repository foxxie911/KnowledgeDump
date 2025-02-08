---
category: "[[Technology]]"
---
## Overview

Multi-threading is like running parts of application in different CPU. A **thread** is like a CPU.

It is a virtual CPU though. Under the hood, single CPU is sharing it's resources among threads. Most popular is time sharing where CPU allocates time for each of the processes alternating between them. It happens so fast that we think that it is doing tasks simultaneously. It is possible to run threads in different cores in multi-core CPU.

![[Pasted image 20250131190656.png]]
### Benefits

1. Better CPU utilization
2. Simpler program design in some cases
3. Better user experience for responsiveness
4. Better user experience for fairness

Multi-threading is harder than multi-tasking because parts of program are reading and writing from the same memory location simultaneously.

Multi-threading comes with a cost. Multi-threading should be done only when the gained values are greater than the cost. If there is no idea whether should use multi-threading than it is necessary to do performance measurements and responsiveness rather than assuming. 

### Costs

1. More complex design
2. Context Switching Overhead -> While switching from one thread to another, the CPU needs to save the local data, pointers, state of the current thread before executing another thread ( called Context Switch) which creates overhead.
3. Increased Resource Consumption -> Each thread itself takes CPU resources and memory.

### More
1. [[Concurrency Models]]