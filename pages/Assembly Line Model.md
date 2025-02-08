## Overview
---
In this model, workers perform one part of the full job. It is similar to the factory workers in the production line. 
![[Pasted image 20250207213229.png | 300]]
As, I/O is a time consuming job, one worker does not wait for this type of time-consuming program to finish. They move the control to the next worker. The workers do as much as they can do until they hit an I/O or another time consuming operation. Then, the other worker too start doing the as much job as it can do until it also hits an I/O type time consuming operation. As a result, the I/O operations in this model becomes non-blocking.
![[Pasted image 20250207213901.png | 300]]
It is common that there might be multiple Assembly Line for the application. And worker from one assembly line is communicating with the worker from another assembly line (such as, worker sending data to worker at log assembly line). So the picture should look something like this,
![[Pasted image 20250207215232.png | 300]]
### Example
These are sometimes called Reactive Systems, or Event-driven Systems. The system reacts to the event occurring in the system or from the outside world or emitted by the other worker from other line. Some popular reactive and event-driven systems are:
1. Akka
2. Vert.x
3. Node.JS
## Types of Assembly Line Model
---
There are two types of reactive, assembly line or event-driven model.
4. Actor
5. Channel
In Actor model, each worker is called an actor. A actor can directly send messages to other actor. The sending process is done asynchronously. Each can be used to initialize one or more separate assembly lines. So, the visual representation of this model looks more like graph.
![[Pasted image 20250207221117.png | 300]]
In the Channel Model, Workers do not directly communicate with each other. They can publish their message to different channels and other workers can subscribe (listen) to the channel. Here, the publisher workers do not have any idea on the subscriber workers.
![[Pasted image 20250207222532.png | 450]]
## Advantages of Assembly Line
---
There's **no shared state** among the workers. They do not share the data. When one worker is working on a data, it is sure that no other worker is accessing that data. 

As a result, the worker can save the data in memory and only write to the external permanent memory when necessary. This makes the workers **Stateful** and the workers become faster than stateless workers.

This model can tell the state of the system at any given time as Job ordering is possible in this model.
## Disadvantages of Assembly Line
---
Each job in this model is spread out to multiple workers. It gets harder to keep track of the code executing for a particular job especially when the workers of a job is sharing data or messages with workers of other jobs. 

 It may also be harder to write the code. Worker code is sometimes written as callback handlers. Having code with many nested callback handlers may result in what some developer call **Callback Hell**. Callback hell simply means that it gets hard to track what the code is really doing across all the callbacks, as well as making sure that each callback has access to the data it needs.