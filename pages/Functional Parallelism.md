## Short Note
---
In this model, program is written using functions calls and each function works as a worker or actor which can communicate with other function similar to reactive or event-driven. It uses the atomic behavior of the function for parallelism. They copy the given parameter so they are the ones who owns it. As they are not blocked by each other they can be executed independently. So, they can be executed in multiple CPUs.

There is an overhead to coordinate functions in different CPUs. As most of the applications run multiple tasks which uses multiple CPUs, its better not to disturb them. 
