## Overview
---
A concurrency model specifies how threads complete the task they are given.

## Thread State
---
### Shared State and Separate State
Thread state is an important aspect of Concurrency Model. Are they separate from each other and can't share object between them? (**Separate State**) Or, Are they able to share objects between themselves? (**Shared State**) 
### Pros and cons of both types of thread state
Shared State can cause **deadlock** and **race condition** which depends on how threads use and access shared objects.

Separate state share immutable objects or copies of an object. It makes easier to write some parts of the program as surely no other thread is going to write in this object. It also solves the problems created by the Shared State. However, it gets harder to design the application in the big picture.
## Models
---
1. [[Parallel Workers Model]]
2. [[Assembly Line Model]]
3. [[Functional Parallelism]] 
