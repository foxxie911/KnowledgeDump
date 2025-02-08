## Overview

In this model, incoming jobs are assigned to different workers or threads. Each worker completes the job from start to end. All the threads run in parallel. This is the most common model in Java application though the landscape is changing rapidly.

![[Pasted image 20250205133808.png | 320]]
## Advantages of Parallel Threads

Parallel Workers model is easy to understand. To increase the parallelism level one just needs to increase the number of workers or threads.
## Disadvantages of Parallel Threads

Parallel Workers is Shared State model so they have all the problems associated with Shared State threads like race condition and deadlock. By trying to avoid these programs lost part of parallelism because it serializes the execution of threads.

![[Pasted image 20250205122621.png | 500]]

Many concurrent data structures are **blocking** meaning a certain amount of threads can access them leading high contention and low parallelism. There are **non-blocking data structures**  that increases performance but they are harder to implement.

There is another alternative namely **Persistent Data Structure** which saves the previous version of itself. While multiple threads accessing the objects of this data structure and one thread modifies it, the modifying thread gets referenced to the new modified version while other threads stays connected to the old version making the whole system consistent. But these data structures do not perform well in real scenarios. They implement the versioning using linked list and modern CPU are not optimized to access linked list object from memory rather they are optimized to access sequential memory. 

**Stateless Workers** are the workers or threads that does not keep track of the state of necessary objects internally. So, they must re-read the state of the object from memory or the database every time they need them. This makes the whole process slow. 

In this model, it is impossible to tell the state of the system at any given time because there is no way of telling which thread is going to execute first. It is harder (if not impossible) to make one task finish before the another task. It makes the whole system non-deterministic. It does not necessarily cause any problem, just make the system harder to track and control.