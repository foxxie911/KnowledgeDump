First java concurrency model assumed multiple threads running within the same application might also share objects. This type of concurrency is called **Shared State Concurrency Model".

Later **Shared Nothing** and **Separate State** types of concurrency gained popularity because of the problems caused by the Shared State Concurrency type. This new type of concurrency assumes that threads don't share data or objects. 

New separate state state platforms and toolkits are:
1. Netty
2. Vert.x
3. Play/Akka
4. Obit

> [!todo]
> Non-blocking tools (LMax Disrupter) and non-blocking algorithms.


### See More
1. [[Multithreading]]
2. [[Concurrency Models]]