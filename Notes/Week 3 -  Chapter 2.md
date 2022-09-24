<strong><u>OS Services</u></strong> - OS provides services like:
- <strong>UI</strong> - GUIs, touch screen, CLI
- <strong>Program execution</strong> - loading & executing programs in memory.
- <strong>IO Operations</strong>
- <strong>File-sytem manipulation</strong> - creating, deleting, searching for files and dirs.

# 2.2 User & OS Interface
- <strong><u>Command interpreters</u></strong> - get and execute user given commands

# 2.3 System Call
 - <strong><u>System call</u></strong> - software triggered interrupt that allows process to request kernel service.
	 - usually written in C, C++
- <strong><u>API</u></strong> - set of commands, functions, tools that are exposed for use by developers/programmers.
	- <strong>Windows</strong>: Windows API
	- <strong>macOS, Linux, UNIX</strong> - POSIX API
	- <strong>JVM</strong> - Java API
	- <strong>Passing params to OS</strong>
		- Pass params to register (memory on the CPU)
		- store params in a block or table in memory and pass the address.
		- Popped/pushed onto a stack
- <strong>Types of System Calls</strong>
	- <strong>Process Control</strong>
		- creates and ends (or aborts) processes
		- loads, execute processes
		- get and set attrs
		- allocate and free up memory
	- <strong>File management</strong>
		- create and read files
		- open and close files
		- read, write and reposition files
		- get and set file attrs
	- <strong>Device Management</strong>
		- request and release device
		- read, write and reposition
		- get and set attrs
		- attach or detach devices
		- a <strong><u>device</u></strong> are the resources controlled by OS
			- can be hardware like drives, or software abstractions like files
	- <strong>Information maintenance</strong>
		- get time or date, set time or date
		- get system data, set system data
		- get/set process, file, or device attributes
	- <strong>Communications</strong>
		- Sometimes processes need to share information between each other.
		- <strong>services</strong>: 
			- create, delete communication connection
			- send, receive messages
			- transfer status information
			- attach or detach remote devices
		- <strong>two models of interprocess communications</strong>
			- <strong><u>message-passing model</u></strong> - processes communicate by sharing messages with each other, either directly, or through a "mailbox."
				- connection must be opened between the two.
			- <strong><u>shared-memory model</u></strong> - use system calls to create and gain access to regions of memory owned by other processes.

	- <strong>Protection</strong>
	  - get/set file permissions

# 2.5 Linkers/Loaders
- <strong>Process of executing program</strong>
	- source program (ex: main.c) is compiled into a <strong><u>relocatable object files</u></strong> - files that can be loaded into physical memory.
	- <strong><u>linker</u></strong> - takes the object files and combines into single binary executable file.
	- <strong><u>loader</u></strong> - loads the binary executable into memory, to run on a CPU core.

# 2.8 OS Structure
- <strong><u>Monolithic</u></strong> - no structure, <strong>tightly coupled</strong>
	- all of kernel functionality placed into single file
	- hard to expand on in the future but it has a performance advantage
- <strong><u>Layered approach</u></strong>
	- is a <strong><u>loosely coupled</u></strong> 
	- divided into smaller components with specific/limited functionality.
	- changes to a component only affect that component.
	- <strong><u>layered approached</u></strong>
		- method of making kernel modular.
		- broken into layers. <strong>Layer N</strong> - user interface. <strong>Layer O</strong> - hardware.
- <strong><u>Microkernels</u></strong> - removing nonessential components into user level programs.
	- results in smaller kernels
	- provides minimal services for processes/memory management
	- provides communication from client program to services in user space through message passing.
- <strong><u>loadable kernel modules (LKMs)</u></strong> -kernel has a set number of compoments and can link in additional ones through modules 