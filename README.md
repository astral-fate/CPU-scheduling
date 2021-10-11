# CPU-scheduling

CHAPTER OBJECTIVES
• Describe various CPU scheduling algorithms.
two classes of policies:
1.	nonpreemptive algorithms: algorithms allow a process to run to completion once it obtains the processor

2.	preemptive algorithms: preemptive algorithms use the interval timer and scheduler to interrupt a running process to real-locate the CPU to a higher-priority ready process.

• Assess CPU scheduling algorithms based on scheduling criteria. 


• Explain the issues related to multiprocessor and multicore scheduling. 
indefinite blocking, or starvation
scheduling issues

• Describe various real-time scheduling algorithms. 

Soft real-time systems/ provide no guarantee as to when a critical real-time process will be scheduled. They guarantee only that the process will be given preference over noncritical processes.

hard real-time systems/ have stricter requirements. A task must be serviced by its deadline; service after the deadline has expired is the same as no service at all.

• Describe the scheduling algorithms used in the Windows, Linux, and Solaris operating systems. 

Dispatcher/ The Windows scheduler ensures that the highest-priority thread will always run. The portion of the Windows kernel that handles scheduling is called the dispatcher.

scheduling classes/ scheduling in the Linux system is based on scheduling classes. Each class is assigned a specific priority. By using different scheduling classes, the kernel can accommodate different scheduling algorithms based on the needs of the system and its processes. 


• Apply modeling and simulations to evaluate CPU scheduling algorithms.
 
Deterministic Modeling => analytic evaluation.
Queueing Models => queueing-network analysis
Simulations => race files


• Design a program that implements several different CPU scheduling algorithms

scheduling classes/ scheduling in the Linux system is based on scheduling classes. Each class is assigned a specific priority. By using different scheduling classes, the kernel can accommodate different scheduling algorithms based on the needs of the system and its processes





















Cycle/ process execution consists of a cycle of CPU execution and I/O wait

CPU burst/ Process execution begins with a CPU burst.

I/O burst/ Process execution continues with a CPU burst.

CPU scheduler/ The selection process is carried out by the CPU scheduler



![image](https://user-images.githubusercontent.com/63984422/136819759-07093d7f-5335-4ed6-9d76-43e456299cb2.png)



nonpreemptive or cooperative/ When scheduling takes place only under circumstances 1 and 4, we say that the scheduling scheme is nonpreemptive or cooperative.

Preemptive/ when a scheduling doesn't take place only under circumstances 1 and 4

Dispatcher/ the dispatcher is the module that gives control of the CPU’s core to the process selected by the CPU scheduler.

e dispatch latency/ The time it takes for the dispatcher to stop one process and start another running is known as the dispatch latency

throughput/ If the CPU is busy executing processes, then work is being done. One measure of work is the number of processes that are completed per time unit, called throughput.

first-come first-serve (FCFS)/ By far the simplest CPU-scheduling algorithm is the first-come first-serve (FCFS) scheduling algorithm.

Gantt chart/ If the processes arrive in the order P1, P2, P3, and are served in FCFS order, we get the result shown in the following Gantt chart, which is a bar chart that illustrates a particular schedule, including the start and finish times of each of the participating processes

convoy effect/ There is a convoy effect as all the other processes wait for the one big process to get off the CPU.

shortest-job-firs (SJF)/ different approach to CPU scheduling is the shortest-job-firs (SJF) scheduling algorithm.

exponential average/ the next CPU burst is generally predicted as an exponential average of the measured lengths of previous CPU bursts.

shortest-remainingtime-firs scheduling/ SJF algorithm will preempt the currently executing process, whereas a nonpreemptive SJF algorithm will allow the currently running process to finish its CPU burst


round-robin (RR)/ The round-robin (RR) scheduling algorithm is similar to FCFS scheduling, but preemption is added to enable the system to switch between processes.

time quantum or time slice/ is defined. A time quantum is generally from 10 to 100 milliseconds in length.

priority-scheduling/ The SJF algorithm is a special case of the general priority-scheduling algorithm.

indefinite blocking, or starvation/ A major problem with priority scheduling algorithms is indefinit blocking, or starvation. A process that is ready to run but waiting for the CPU can be considered blocked.

Aging/ A solution to the problem of indefinite blockage of low-priority processes is aging

multilevel queue/ scheduling simply schedules the process in the highest-priority queue

foreground/ (interactive) processes

background/ (batch) processes.

multilevel feedback queue /  scheduling algorithm, in contrast, allows a process to move between queues.
processcontention scope (PCS) / the scheme of e distinction between user-level and kernel-level threads lies in how they are scheduled. On systems implementing the many-to-one and many-to-many models, the thread library schedules userlevel threads to run on an available LWP.

system-contention scope (SCS)/ To decide which kernel-level thread to schedule onto a CPU, the kernel uses system-contention scope (SCS).

load sharing/ If multiple CPUs are available, load sharing, where multiple threads may run in parallel, becomes possible, however scheduling issues become correspondingly more complex.

Multiprocessor/ systems that provided multiple physical processors, where each processor contained one single-core CPU.

a symmetric multiprocessing/ one core accesses the system data structures, reducing the need for data sharing.

s symmetric multiprocessing (SMP)/ The standard approach for supporting multiprocessors is symmetric multiprocessing (SMP), where each processor is self-scheduling.

multicore processor/ However, most contemporary computer hardware now places multiple computing cores on the same physical chip, resulting in a multicore processor

memory stall/ Researchers have discovered that when a processor accesses memory, it spends a significant amount of time waiting for the data to become available. This situation, known as a memory stall, occurs primarily because modern processors operate at much faster speeds than memory. However, a memory stall can also occur because of a cache miss.

hardware threads/ are assigned to each core. That way, if one hardware thread stalls while waiting for memory, the core can switch to another thread.

chip multithreading (CMT)/ appears as a logical CPU that is available to run a software thread.

hyper-threading - simultaneous multithreading/ to describe assigning multiple hardware threads to a single processing core. 

coarse-grained and fine-graine multithreading/ two ways to multithread a processing core

Load balancing/ attempts to keep the workload evenly distributed across all processors in an SMP system.

There are two general approaches to load balancing:

push migration/ a specific task periodically checks the load on each processor and—if it finds an imbalance—evenly distributes the load by moving (or pushing) threads from overloaded to idle or less-busy processors.

pull migration/ occurs when an idle processor pulls a waiting task from a busy processor.

processor affinity/ process has an affinity for the processor on which it is currently running.

soft affinity/ processor affinity takes several forms. When an operating system has a policy of attempting to keep a process running on the same processor—but not guaranteeing that it will do so.

hard affinity/ some systems provide system calls that support hard affinit, thereby allowing a process to specify a subset of processors on which it can run.

heterogeneous multiprocessing (HMP)/ a systems that designed using cores that run the same instruction set, yet vary in terms of their clock speed and power management, including the ability to adjust the power consumption of a core to the point of idling the core.

big.LITTLE/ For ARM processors that support it, this type of architecture is known as big.LITTLE where higher-peformance big cores are combined with energy efficient LITTLE cores. Big cores consume greater energy and therefore should only be used for short periods of time. Likewise, little cores use less energy and can therefore be used for longer periods.


5.6 Real-Time CPU Scheduling:

Soft real-time systems/ provide no guarantee as to when a critical real-time process will be scheduled. They guarantee only that the process will be given preference over noncritical processes.

hard real-time systems/ have stricter requirements. A task must be serviced by its deadline; service after the deadline has expired is the same as no service at all.

event latency/ When an event occurs, the system must respond to and service it as quickly as possible.

interrupt latency/ refers to the period from the arrival of an interrupt at the CPU to the start of the routine that services the interrupt.

dispatch latency/ The amount of time required for the scheduling dispatcher to stop one process and start another is known as dispatch latency.

conflict phase/ The conflic phase of dispatch latency has two components:
 1. Preemption of any process running in the kernel
 2. Release by low-priority processes of resources needed by a high-priority process 
Following the conflict phase, the dispatch phase schedules the high-priority process onto an available CPU

Periodic/ That is, they require the CPU at constant intervals (periods). Once a periodic process has acquired the CPU, it has a fixed processing

Rate/ of a periodic task is 1/p

admission-control algorithm/ the scheduler does one of two things. It either admits the process, guaranteeing that the process will complete on time, or rejects the request as impossible if it cannot guarantee that the task will be serviced by its deadline.

rate-monotonic/ scheduling algorithm schedules periodic tasks using a static priority policy with preemption.

Earliest -deadline-firs (EDF)/ scheduling assigns priorities dynamically according to deadline. The earlier the deadline, the higher the priority; the later the deadline, the lower the priority.

Proportional share/ schedulers operate by allocating T shares among all applications


scheduling classes/ scheduling in the Linux system is based on scheduling classes. Each class is assigned a specific priority. By using different scheduling classes, the kernel can accommodate different scheduling algorithms based on the needs of the system and its processes. 

nice value/ assigned to each task. Nice values range from −20 to +19, where a numerically lower nice value indicates a higher relative priority.

targeted latency/ CFS doesn’t use discrete values of time slices and instead identifies a targeted latency, which is an interval of time during which every runnable task should run at least once.

virtual run time/ The CFS scheduler records how long each task has run by maintaining the virtual run time of each task using the per-task variable vruntime.

scheduling domain/ A scheduling domain is a set of CPU cores that can be balanced against one another.

NUMA node/ a domain that share a level 3 (L3) cache, and are therefore organized into a processor-level domain

Dispatcher/ The Windows scheduler ensures that the highest-priority thread will always run. The portion of the Windows kernel that handles scheduling is called the dispatcher.





Priorities are divided into two classes:

variable class/ contains threads having priorities from 1 to 15

real-time class/ contains threads with priorities ranging from 16 to 31. (There is also a thread running at priority 0 that is used for memory management.)

idle thread/ n. If no ready thread is found, the dispatcher will execute a special thread called the idle thread.

foreground process/ that is currently selected on the screen

background processes/ that are not currently selected.

user-mode scheduling (UMS)/ s 7 introduced user-mode scheduling (UMS), which allows applications to create and manage threads independently of the kernel.

fiber/ Earlier versions of Windows provided a similar feature known as fiber, which allowed several user-mode threads (fibers) to be mapped to a single kernel thread.

Concurrency Runtime (ConcRT)/ schedulers come from programming language libraries that build on top of UMS. For example, Microsoft provides Concurrency Runtime (ConcRT), a concurrent programming framework for C++ that is designed for task-based parallelism on multicore processors. ConcRT provides a user-mode scheduler together with facilities for decomposing programs into tasks, which can then be scheduled on the available processing cores.

SMT sets/ One technique used by Windows is to create sets of logical processors (known as SMT sets). On a hyper-threaded SMT system, hardware threads belonging to the same CPU core would also belong to the same SMT set.

ideal processor/ to distribute loads across different logical processors, each thread is assigned an ideal processor, which is a number representing a thread’s preferred processor.

CPU shares/ the fair-share class uses CPU shares instead of priorities to make scheduling decisions
Project/ CPU shares indicate entitlement to available CPU resources and are allocated to a set of processes (known as a project).

5.8.1 Deterministic Modeling
class of evaluation methods:

analytic evaluation/ uses the given algorithm and the system workload to produce a formula or number to evaluate the performance of the algorithm for that workload.

Deterministic Modeling

Deterministic modeling/ deterministic modeling is one type of analytic evaluation. This method takes a particular predetermined workload and defines the performance of each algorithm for that workload
Queueing Models
queueing-network analysis/ the computer system is described as a network of servers. Each server has a queue of waiting processes. The CPU is a server with its ready queue, as is the I/O system with its device queues. Knowing arrival rates and service rates, we can compute utilization, average queue length, average wait time, and so on. This area of study is called queueing-network analysis.

Little’s formula/  n = λ × W. This equation, known as Little’s formula, is particularly useful because it is valid for any scheduling algorithm and arrival distribution. For example, n could be the number of customers in a store.
Simulations
Trace files/ distribution-driven simulation may be inaccurate, however, because of relationships between successive events in the real system. The frequency distribution indicates only how many instances of each event occur; it does not indicate anything about the order of their occurrence. To correct this problem, we can use trace files. We create a trace by monitoring the real system and recording the sequence of actual events.




Implementation
Regression testing/ confirms that the changes haven’t made anything worse, and haven’t caused new bugs or caused old bugs to be recreated

lottery scheduling/ one technique for implementing lottery scheduling works by assigning processes lottery tickets, which are used for allocating CPU time. Whenever a scheduling decision has to be made, a lottery ticket is chosen at random, and the process holding that ticket gets the CPU.
