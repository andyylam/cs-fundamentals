# Operating Systems

### Difference between kernel and OS

The kernel is part of the operating system and closer to the hardware it provides low level services like:

    device driver
    process management
    memory management
    system calls

An operating system also includes applications like the user interface (shell, gui, tools, and services).

## Process Abstraction

Process/task/job is a dynamic abstraction for executing program, where information required to describe a running program is contained. The information includes three components:
  - Memory context
  - Hardware context
  - OS context

Memory Context
- Text section (instructions)
- Data section (global variables)
- Stack (memory for function calls)
- Heap (dynamically allocated memory)

### System Calls

System calls are Application Program Interface(API) to OS, which provides ways of calling facilities/services in kernel.

### Process Creation

`fork()` is the main way to create a new process. It returns:
- PID of the newly created process for parent process, or 0 for child process

The behaviour of fork() is to create a new process called child process, which is a duplicate of the current executable image. The data in child is a copy of the parent, thus not shared. The only difference between the parent and child process are 
- Process ID(PID)
- Parent ID(PPID)
- fork() return value

### Process Termination

The UNIX convention is to `exit()` with a status 0 if the termination is normal, and non-zero if the execution is problematic

### Process Scheduling

There are two main types of process behavior:
- CPU bound
- IO bound

There are two types of scheduling policies:
- Non-preemptive: Process stays on the CPU until it finishes or is blocked.
- Preemptive: Process is given a time quota to run.

Non-preemptive scheduling algorithms:
- FCFS
- Shortest Job First

Preemptive scheduling algorithms:
- Round robin
- Priority scheduling
- Multi-level feedback queue (MLFQ)

### Threads 

A thread is an entity within a process that can be scheduled for execution. All threads of a process run in a shared memory space. Threads are way to improve application interactivity through parallelism. 

### Interprocess Communication

1. Shared Memory 
  - Shared memory is memory that may be simultaneously accessed by multiple programs with an intent to provide communication among them. Shared memory is an efficient means of passing data between programs. However, race conditions may occur if memory accesses are not handled properly. 

2. Message Passing
  - Processes communicate with each other by exchanging messages. This is done through system calls that help `send` and `receive`.  The send, receive, and reply operations may be synchronous or asynchronous. 

3. Unix Pipes
  - A pipeline is a mechanism for inter-process communication using message passing. 
  - A pipeline is a set of processes chained together by their standard streams, so that the output text of each process (stdout) is passed directly as input (stdin) to the next one. 

### Synchronisation 

- Busy waiting
- Semaphores

## Memory Abstraction