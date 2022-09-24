# 9/23 Lecture Notes
# Chapter 4
- Most modern applications are multithreaded
	- separate tasks within an app can be implemented by multiple threads
	- Kernels are generally multithreaded
## Multicore programming
- are challenges for programmers bc of:
	- testing and debugging
	- dividing actives 
	- data dependencies
- <strong><u>Parallelism</u></strong> - system performing more than one task at the same time.
	- <strong><u>data parall.</u></strong> - spreading out data for a single operation across multiple cores.
	- <strong><u>task parall.</u></strong> - distributing threads across core (each thread doing a different task)
- <strong><u>Concurrency</u></strong> - supports more than one task making progress
	- single core with a scheduler
## Multihreading models
- <strong><u>many to one</u></strong>
	- many <strong>user threads</strong> mapped to single kernal thread,
	- one thread blocking causes all to block
	- multiple threads can not run in parallel bc only one thread can be in kernel at a tone
- <strong><u>one to one</u></strong>
	- Each user thread maps to one kernel thread
- <strong><u>many to many</u></strong>
	- many user threads mapped to many kernel threads

- <strong><u> Implicit Threading</u></strong>
	- transfers the management of thread creation from developers to the compilers
- <strong><u>thread pool</u></strong> - a number of threads set side in a "pool" waiting for work


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