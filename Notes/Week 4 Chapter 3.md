# 9/16 Lecture Notes
## 3.1 Process Concept
- <strong><u>job</u></strong> -  set of commands executed by batch system
	- basically interchangeable with process
- <strong><u>Process</u></strong> - program loaded into memory
	- <strong><u>program counter</u></strong> - CPU register that indicate location in main memory of next instruction to load/execute.
		- The value of this is the status of the current activity of a process.
	- <strong>memory layout of process: </strong>
		- <strong>text section</strong> - executable code
		- <strong>data section</strong> - global variables
		- <strong>heap section</strong> - dynamically allocated memory
		- <strong>stack section</strong> - temp data storage when invoking functions
- <strong><u>Process States</u></strong> - processes have five states
	- <strong>new</strong> - process being created
	- <strong>running</strong> - instructions are being executed
	- <strong>waiting</strong> - waiting for event to occur
	- <strong>ready</strong> - waiting to be assigned a processor 
	- <strong>terminated</strong>.  - finished exec.
- <strong><u>Batch Systems</u></strong> - used for computationally expensive jobs.
- <strong><u>Process Control Block (PCB)</u></strong> - contains info associated with each process
	- registers
	- process state
	- IO info
	- etc
- <strong><u>Process Scheduling</u></strong> - desire is to max. CPU utilization
	- maintains queues of processes
		- <strong>job queue</strong> - all processes
		- <strong>ready queue</strong> - all processes in memory
		- <strong>device queues</strong> - all processes waiting for IO device 

## 3.2 Process Scheduling
- <strong><u>process scheduler</u></strong> - selects available process to be executed.
- <strong><u>degree of multiprogramming</u></strong> - number of processes currently in memory.
- <strong><u>queues</u></strong>
	- <strong><u>ready queue</u></strong> - for processes ready and waiting to be executed.
	- <strong><u>wait queue</u></strong> - processes waiting for an event .
	- <strong><u>job queue</u></strong> -  set of all processes in the system
	- <strong><u>device queue</u></strong> - set of processes waiting for an IO device
- <strong><u>CPU scheduling</u></strong>
	- <strong><u>Short Term Scheduler (CPU Scheduler)</u></strong> - selects the next process among the ready queue to be executed and allocated a CPU core.
	- <strong><u>Long Term Scheduler</u></strong> - selects next process to go in queue.
- Processes are either
	- <strong><u>IO Bound Process</u></strong> - more IO than computation, many short CPU bursts
	- <strong><u>CPU bound</u></strong> - does more computation, fewer but longer CPU bursts

 <strong><u>Context Switch</u></strong> - when CPU switches to other process, systems must save the current context and then load another
 - <strong><u>context</u></strong> - describes the state of execution of process, registers, heap, stack (AKA the context is represented in PCB).

## 3.3 Operations on Processes
- <strong>Process creation</strong>
	- <strong><u>parent</u></strong> - a process that creates another process
	- <strong><u>children</u></strong> - a process that was created by another process.
		- can either receive resources (CPU, memory, IO devices) from the OS or be constrained to a subset of its parent's resources
		- parent either waits for child to execute or executes concurrently
		- can either be a duplicate of parent or have a new program loaded into it
	- <strong><u>pid</u></strong> - process identifier, unique int that identifies a process  in the sytem.
- `fork()` - command to create process in UNIX, `CreateProcess` in Windows
- <strong>Process Termination</strong>
	- process finishes last statement and requests to be deleted with `exit()` call.
		- process returns a status value (int) to parent via `wait()`
		- if parent does not call `wait()`, child becomes  a <strong><u>orphan</u></strong>
		- <strong><u>zombie</u></strong> - a process becomes this during the intermediary state of being terminated but parent not yet calling `wait()`
	- parent processes can also terminate it's child processes when:
		- child exceeds usage of resources
		- child is not longer required
		- parent is terminating (if the child process can not run w/o parent)

## 3.4 Interprocess Communication
- <strong><u>independent processes</u></strong> - does not share data with other processes.
- <strong><u>cooperating processes</u></strong> - can be affecting or affect other executing processes. 
	- several apps may want the same data
	- for computation speedup with task broken into smaller ones.
- Two models of <strong>IPC (interprocess communication)</strong>
	- <strong><u>Shared memory</u></strong> - sharing a section memory together
		- typically faster
	- <strong><u>Message passing</u></strong> - passing information for a message queue (like a mailbox)
		- better for smaller exchanges of data.
		- easier to implement

## 3.5 IPC in Shared Memory Systems
- <strong><u>producer - consumer paradigm/problem</u></strong>
	- <strong><u>producer</u></strong> - process that produces information that<strong> consumer </strong>processes consumes. (compilers produce assembly code  consumed by assembler). Think the client-server model. Server is the producer, client is the consumer.
	- for processes to run concurrently, you need a buffer filled by the producer and emptied by consumer. Buffer is stored in area of memory that both can access.
		- <strong><u>unbounded buffer</u></strong> - no size limit.
		- <strong><u>bounded buffer</u></strong> - fixed buffer size. 

## 3.6 IPC in Message Passing System
- message-passing system provides at least two ops: `send(message)` and `receive(message)`.
- messages can be fixed or variable in size.
- <strong>naming</strong> - processes that communicate need a way to refer to each other.
	- <strong><u>direct communication</u></strong> - processes refer to each other explicitly. 
		- `send(P, message)` - send message to process P
		- `receive(Q, message)` - receive message from process Q (symmetric - both processes must name each other to send and receive)
		- `receive(id, message)` - receive a message from any process (asymmetric).
	- <strong><u>indirect communication</u></strong> - messages sent and received from ports (mailboxes)
		- each message has a unique id
		- `send(A, message)` - send a message to mailbox A
		- `receive(A, message)` - receive a message from mailbox A
		- both processes have to share a mailbox
		
- <strong>synchronization</strong>
	- message passing can be<strong> sync (blocking)</strong> or <strong> async (non-blocking)</strong>
	- <strong>blocking</strong>
		- the process sending is blocked until message is received
		- receiver blocks until message is available
	- <strong>nonblocking</strong>
		- sending process sends message and resumes operation
		- receiver retrieves message or null.
