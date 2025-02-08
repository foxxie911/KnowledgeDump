## Overview

A concurrency model specifies how threads complete the task they are given.

## Thread State
### Shared State and Separate State

Thread state is an important aspect of Concurrency Model. Are they separate from each other and can't share object between them? (**Separate State**) Or, Are they able to share objects between themselves? (**Shared State**) 

### Pros and cons of both types of thread state

Shared State can cause **deadlock** and **race condition** which depends on how threads use and access shared objects.

Separate state share immutable objects or copies of an object. It makes easier to write some parts of the program as surely no other thread is going to write in this object. It also solves the problems created by the Shared State. However, it gets harder to design the application in the big picture.

## Models
### Parallel Workers (Parallel Threads)

In this model, incoming jobs are assigned to different workers or threads. Each worker completes the job from start to end. All the threads run in parallel. This is the most common model in Java application though the landscape is changing rapidly.

![[Pasted image 20250205133808.png]]
#### Advantages of Parallel Threads

Parallel Workers model is easy to understand. To increase the parallelism level one just needs to increase the number of workers or threads.
#### Disadvantages of Parallel Threads

Parallel Workers is Shared State model so they have all the problems associated with Shared State threads like race condition and deadlock. By trying to avoid these programs lost part of parallelism because it serializes the execution of threads.

![[Pasted image 20250205122621.png]]

Many concurrent data structures are **blocking** meaning a certain amount of threads can access them leading high contention and low parallelism. There are **non-blocking data structures**  that increases performance but they are harder to implement.

There is another alternative namely **Persistent Data Structure** which saves the previous version of itself. While multiple threads accessing the objects of this data structure and one thread modifies it, the modifying thread gets referenced to the new modified version while other threads stays connected to the old version making the whole system consistent. But these data structures do not perform well in real scenarios. They implement the versioning using linked list and modern CPU are not optimized to access linked list object from memory rather they are optimized to access sequential memory. 

**Stateless Workers** are the workers or threads that does not keep track of the state of necessary objects internally. So, they must re-read the state of the object from memory or the database every time they need them. This makes the whole process slow. 

In this model, it is impossible to tell the state of the system at any given time because there is no way of telling which thread is going to execute first. It is harder (if not impossible) to make one task finish before the another task. It makes the whole system non-deterministic. It does not necessarily cause any problem, just make the system harder to track and control.

### Assembly Line (Event-driven system or reactive system)

In this model, workers perform one part of the full job. It is similar to the factory workers in the production line. 

![[Pasted image 20250207213229.png]]

As, I/O is a time consuming job, one worker does not wait for this type of time-consuming program to finish. They move the control to the next worker. The workers do as much as they can do until they hit an I/O or another time consuming operation. Then, the other worker too start doing the as much job as it can do until it also hits an I/O type time consuming operation. As a result, the I/O operations in this model becomes non-blocking.

![[Pasted image 20250207213901.png]]

It is common that there might be multiple Assembly Line for the application. And worker from one assembly line is communicating with the worker from another assembly line (such as, worker sending data to worker at log assembly line). So the picture should look something like this,

![[Pasted image 20250207215232.png]]

#### Example

These are sometimes called Reactive Systems, or Event-driven Systems. The system reacts to the event occurring in the system or from the outside world or emitted by the other worker from other line. Some popular reactive and event-driven systems are:
1. Akka
2. Vert.x
3. Node.JS

#### Type

There are two types of reactive, assembly line or event-driven model.
1. Actor
2. Channel

In Actor model, each worker is called an actor. A actor can directly send messages to other actor. The sending process is done asynchronously. Each can be used to initialize one or more separate assembly lines. So, the visual representation of this model looks more like graph.

![[Pasted image 20250207221117.png]]

In the Channel Model, Workers do not directly communicate with each other. They can publish their message to different channels and other workers can subscribe (listen) to the channel. Here, the publisher workers do not have any idea on the subscriber workers.

![[Pasted image 20250207222532.png]]

#### Advantages of Assembly Line

There's **no shared state** among the workers. They do not share the data. When one worker is working on a data, it is sure that no other worker is accessing that data. 

As a result, the worker can save the data in memory and only write to the external permanent memory when necessary. This makes the workers **Stateful** and the workers become faster than stateless workers.

This model can tell the state of the system at any given time as Job ordering is possible in this model.

#### Disadvantages of Assembly Line

Each job in this model is spread out to multiple workers. It gets harder to keep track of the code executing for a particular job especially when the workers of a job is sharing data or messages with workers of other jobs. 

 It may also be harder to write the code. Worker code is sometimes written as callback handlers. Having code with many nested callback handlers may result in what some developer call **Callback Hell**. Callback hell simply means that it gets hard to track what the code is really doing across all the callbacks, as well as making sure that each callback has access to the data it needs.

### Functional Parallelism

In this model, program is written using functions calls and each function works as a worker or actor which can communicate with other function similar to reactive or event-driven. It uses the atomic behavior of the function for parallelism. They copy the given parameter so they are the ones who owns it. As they are not blocked by each other they can be executed independently. So, they can be executed in multiple CPUs.

There is an overhead to coordinate functions in different CPUs. As most of the applications run multiple tasks which uses multiple CPUs, its better not to disturb them. 