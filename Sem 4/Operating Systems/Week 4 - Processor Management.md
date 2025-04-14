
# Terms

**Process:** 
An active entity that requires a set of resources, including a processor and special register to perform it functions, which called **tasks**

**Thread:**
A portion of process that run independently

**Processor:**
also known as CPU, part that performs the calculations and executes programs

---
# Process Scheduler VS Job Scheduler

**Job Scheduler**
- Job Scheduler is a more higher scheduling
- It choose which job to start to efficiently use the memory
- Selecting jobs from a queue of incoming jobs and put them in process queue

**Process Scheduler**
- Process Scheduler start inside a job 
- Process Scheduler takes over after a job has been placed and ready queue by the job scheduler
- Low level scheduler that assigns the CPU executions
- Determines which jobs are using the CPU, when, and how long
- Other Responsibilities for Process Scheduler:
	- Decides Interrupt
	- Determines a job finished should be terminated

---
# Process Scheduler

General tendencies that can be exploited when selecting a scheduling algo
- I/O bound jobs 
- CPU bound jobs

In a highly interactive environment, third layer processor -> **Middle level scheduler**
- Removes actives job when system overloaded
- to reduce degree of multi-programming 
- allow job to complete faster

**Job and Process status**
Five states: 
- Hold
- Ready
- Running
- Waiting
- Finished

---

# Transitions

| Transition          | Initiated by..                                                                     |
| ------------------- | ---------------------------------------------------------------------------------- |
| HOLD to READY       | Job Scheduler - Check available memory                                             |
| READY to RUNNING    | Process Scheduler - according to predefined algorithm                              |
| RUNNING to READY    | Process Scheduler - time limit or Criteria e.g. interrupt                          |
| RUNNING to WAITING  | Process Scheduler - cuz of instruction such as READ, WRITE or I/O request          |
| WAITING to READY    | Process Scheduler - signal from I/O device Mgr that indicate I/O request satisfied |
| RUNNING to FINISHED | Process / Job Scheduler - job done or there is error                               |

---

# Process Control Block

Visual Presentation of basic info
- What it is
- Where it going
- How much completed
- Where it stored
- How much resource it use

**Content of each PCB**
+-----------------------------+
| Process Identification          |
+-----------------------------+
| Process Status                     |
+-----------------------------+
| Process state:                      |             
|   - Process Status Word      |
|   - Register Content            |
|   - Main Memory                |
|   - Resources                      |
|   - Process Priority              |
+-----------------------------+
| Accounting                         |
+-----------------------------+

- PCB is created when job is accepted and updated as job progress

---
# Process Scheduling Policy

- Use in a multiprogramming env
- OS need to resolve 3 limitations
	1. Finite number of resources
	2. Resources allocated cannot be shared
	3. Certain resources requires operator intervention

What is good process scheduling policy?
- Maximize throughput
- Minimize response time
- Minimize turnaround time
- Minimize waiting time
- Maximize CPU efficiency
- Ensure Fairness

- Criteria may contradict one another
- Must determine which criteria is the most important for a specific system

---
# Process Scheduling Algorithm
- Process Scheduler relies on a process scheduling algo to allocate the CPU

**6 Process Scheduling algorithms:**
1. First Come, First Serve
2. Shortest Job Next
3. Priority Scheduling
4. Shortest Remaining Time
5. Round Robin
6. Multi Level Queues

---
# First Come First Serve (FCFS)
- Good for batch systems but unacceptable for interactive systems
- High average turnaround time based on job enter and are seldom minimized

---
# Shortest Job Next

- Handle job based on length of their cpu cycle times
- Easiest to implement in batch environment
- SJN only optimal when all jobs are available at the same time and CPU estimates are available and accurate

---
# Priority Scheduling

- Gives preferential treatment to important jobs
- Allows programs with the highest priority first and cannot be interrupted until cycle complete
- priorities assigned by system admin using characteristic, lol hierarchy stuff
- In commercial env, users can purchase higher priority , p2w

---
# Shortest Remaining Time

- Preemptive ver of SJN
- Complete the shortest job at any time
- Need more overhead because OS has to monitor Queue all the time to perform context switching
- SRT is faster than SJN
- when preempted, the current job info must be save into PCB to continue later
- Context switch still takes time and might diminish the advantage of SRT

---
# Round Robin

- Is not based on job characteristics
- slice of time is given to each job to ensure CPU is shared among all active jobs
- no job monopolize the CPU
- a time slice TIME QUANTUM
- jobs are place in READY queue using FCFS scheme

Process Scheduler:
- Select the first job at the front
- set timer
- allocate cpu to the job
- If job not finished at the allocated time, info saved to PCB, and putted back to READY queue

- Its efficiency depends on size of time quantum and in relations to the average CPU
	- if time quantum too large it just become FCFS
	- if it too small, switching might slows down the job execution and increase overhead dramatically
- Rules of thumb for quantum size:
	- enough to allow 80% of the CPU cycle to run to completion
	- 100 times longer than time required to perform switching context

---
# Multiple-Level Queues

- Not a separate scheduling algo, instead works in conjunction with other schemes
- Examples:
	- Priority-based systems with different queues for each priority level
	- Separate the batch jobs and interactive jobs
- why use one when u can use more than one algorithm lol

- Issues:
	- Every job priority is more than black and white
	- Each job is important depends on who you ask
	- To ensure fairness, juggle between priorities, queues and switching

**Case 1: No movement between queues**
- CPU allocated using FCFS to high-priority job only
- After that only allocate to low-priority queue

**Case 2: Movement between queues**
- Policy adjust priorities assigned to each job
- High-priority jobs are treated normally but when time quantum expires, move to lower queue
- Job priority may change, e.g ada request I/O

**Case 3: Variable time quantum per queue**
- Time quantum increase between each queue

**Case 4: Aging**
- Ensure lower-level queues will complete the execution
- OS keep track waiting time
- When waiting time exceed a limit, job got put into high priority