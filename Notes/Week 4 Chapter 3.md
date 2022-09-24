# 9/16 Lecture Notes
## 3.1 Process Concept
- <strong><u>job</u></strong> -  set of commands executed by batch system
	- basically interchangeable with process
- <strong><u>Process</u></strong> - program loaded into memory
	- <strong><u>program counter</u></strong> - CPU register that indicate location in main memory of next instruction to load/execute.
		- The value of this is the status of the current activity of a process.
	- <strong>memory layout: </strong>
		- <strong>text section</strong>
		- <strong>data section</strong>
		- <strong>heap section</strong>
		- <strong>stack section</strong>
- <strong><u>Batch Systems</u></strong> - used for computationally  expensive jobs.
- <strong>Process States</strong> - processes have five states
	- <strong>new</strong> - process being created
	- <strong>running</strong> - instructions executed
	- <strong>waiting</strong> - waiting for event to occur
	- <strong>ready</strong> - waiting to be assigned a processor 
	- <strong>terminated</strong>.  - finished exec.
- <strong><u>Process Control Block (PCB)</u></strong> - info associated with each process
	- registers
	- process state
	- IO info
	- ...
- <strong><u>Process Scheduling</u></strong> - desire is to max. CPU utilization
	- maintains queues of processes
		- <strong>job queue</strong> - all processes
		- <strong>ready queue</strong> - all processes in memory
		- <strong>device queues</strong> - all processes waiting for IO device 

## Schedulers
- <strong><u>Short Term Scheduler</u></strong> - selects the next process to be exec.
- <strong><u>Long Term Scheduler</u></strong> - selects next process to go in queue.
- Processes are either
	- <strong><u>IO Bound Process</u></strong> - more IO than computation.
	- <strong><u>CPU bound</u></strong> - does more computation.

## Context Switch
- when CPU switches to other process, system must save state of old process and load saved state the the new process.


## Interprocess Communication
- Process can be <strong>independent</strong> or <strong>cooperating</strong>
	- Independent processes cannot be affected by exec. of other process but cooperating processes can.

- Two models
	- <strong><u>Shared memory</u></strong>
	- <strong><u>Message passing</u></strong>
	-


# Chapter 3 Reading Notes