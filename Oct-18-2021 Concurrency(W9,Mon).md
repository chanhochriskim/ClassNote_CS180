# Concurrency
## Time Slicing 
- In early days, one program ran at a time
- Along came windowed ooperating systems 
- Giving illusion of multiple programs running at a time 
- Email tool, web browser, text editor 
- 1 second = 1000 ms.
- *Time slicing* running each progarm a few hundred ms.
- Humans are so slow that it appeared that all programs were running simultaneusly. 

## Mobile Devices 
- Illusion worked well as programs became more and more complex.
- Simply make the CPU run faster.
- Along came mobile devices -- laptops and phones. 
- run on batteries. 
- As the CPU runs faster battery runs down quicker and gets very hot. 

## Multiple Cores 
- How about putting 2 or more CPUs (cores) on same chip?
- If run 2 cores at half speed, same as 1 core at full speed.
- Slower cores consume less battery and generate less heat
- Now most laptops and phones have 4 or more cores.
- If you have 4 apps running, they may actually be running simultaenously.
- What if you have more than 4?
	- Time slicing is alive and well -- some apps are in a queue waiting to get a core.
## Threads 
- multiple cores can even be used to speed up one program. 
- a program can have more than one part (thread) running simultaneously.
- What if a database is spread over 3 files? 
- Program runs (approx) 3 times faster
## Sequential vs Concurrent
-Sequential:
	- A single "thread of execution" weaves its way through your program.
	- A single PC identifies the current instruction being executed.
- Concurrent:
	- Multiple "threads of execution" are running simultaneously through your program. 
	- Multiple PCs are active, one for each thread.
## Java Threads
 - Thread class with run() method 
 - import java.lang.*;
 - Allows creation and manipulation of threads
	 - Thread t = new Thread();
- *three* very important methods:
	- t.start() start the thread referenced by t
	- t.join() join with the running thread t 
	- t.run() called by start() in a different thread
- *NOTE* Your code does not call run() directly; instead, the start() method calls run() as part of the new thread sequence. 
## How to creat threads
 - Create a class that implements the *Runnable* iterface 
## Using Concurrent Processing 
- How do you break down a large problem into pieces?
- Need to decompose the problem into pieces 
- Two approaches to decomposition 
	- By the tasks to be done
	- By the data to be proceesed
## Task Decomposition 
- Split task into multiple subtasks
- Each subtask runs different code 
- Each subtask runs on its own core (processor) 
- Primary benefit: responsiveness 
	- GUI is one task 
	- Background computatino a different task 
	- GUI has its own core, so is always responsive 
## Domain Decomposition 
- Domain:
	- Input examined by the problem
= Divide domain into pieces (subdomians)
-Each subtask runs the 
	- same code but
	- on different input
- Each subdomain is given to a task running on a different core.
- Primary benefit: raw speed 
## Unpredictibility in Thread Execution 
- Thread execution may be interrupted.
	- "Time slicing" of threads prevents one thread from "hogging" the CPU
	- higher priority activities may interrupt the thread: e.g. I/O 
- Multiple threads do nto always proceed at the same rate 
- Coordination of multiple threads a challenge 
- Java provides low-level and high-level tools to deal with~~.~~fdf
- 