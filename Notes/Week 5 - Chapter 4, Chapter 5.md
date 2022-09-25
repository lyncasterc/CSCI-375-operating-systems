# Chapter 4
## 4.1
- <strong><u>thread</u></strong> - basic unit of CPU utilization 
	- has an ID, a program counter, registers, stack.
	- a traditional process has one thread
- Most modern applications are multithreaded
	- separate tasks within an app can be implemented by multiple threads
	- Kernels are generally multithreaded

## 4.2 Multicore programming
- are challenges for programmers bc of:
	- testing and debugging
	- dividing actives 
	- data dependencies
- <strong><u>Parallelism</u></strong> - system performing more than one task at the same time.
	- <strong><u>data parall.</u></strong> - spreading out data for a single operation across multiple cores.
	- <strong><u>task parall.</u></strong> - distributing threads (tasks) across core (each thread doing a different task)
- <strong><u>Concurrency</u></strong> - supports more than one task making progress (apparently by switching between tasks).
	- single core with a scheduler

## 4.3 Multithreading models
- <strong><u>user threads</u></strong> - threads running in user mode without kernel support
- <strong><u>kerrnel threads</u></strong> - threads running in kernel mode, managed directly by the OS
- <strong><u>many to one</u></strong>
	- many <strong>user threads</strong> mapped to single kernel thread,
	- one thread blocking causes all to block
	- multiple threads can not run in parallel bc only one thread can be in kernel at a time
	- ![[Screen Shot 2022-09-24 at 21.21.13.png]]
- <strong><u>one to one</u></strong>
	- Each user thread maps to one kernel thread
	- provides more concurrency
	- multiple threads can run in parallel
- <strong><u>many to many</u></strong>
	- many user threads mapped to many kernel threads

## 4.5 Implicit Threading
- <strong><u> Implicit Threading</u></strong>
	- transfers the management of thread creation from developers to the compilers
- <strong><u>thread pool</u></strong> - a number of threads set side in a "pool" waiting for work
	- slightly faster than having to create a new thread


# Chapter 5
- <strong><u>CPU scheduler</u></strong>
	- <strong><u>short term scheduler</u></strong> - selects from processes in the ready queue and allocates CPU to one of them.
	- CPU scheduling decisions happen when:
		- process switches from running to waiting or vice-versa
		- process switches from running to ready, or waiting to ready
		- process terminates
- <strong><u>dispatcher</u></strong> - gives control of CPU to the process selected by the short term scheduler
	- <strong><u>dispatch latency</u></strong> - time it takes for dispatcher to stop process and run another
- <strong><u>Scheduling Algs</u></strong>
	-