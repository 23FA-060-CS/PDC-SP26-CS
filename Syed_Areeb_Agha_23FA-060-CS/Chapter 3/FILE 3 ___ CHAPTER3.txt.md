```
# Chapter 3 - Using Pipes with Multiprocessing (Process Based Parallelism)
```

```
FILE--1 communicating_with_pipe.txt
```

## `## What Does It Do` 

```
This program demonstrates inter-process communication (IPC) using Python's
multiprocessing module.
```

```
It creates two processes connected through pipes. One process generates numbers
from 0 to 9, and the second process receives those numbers, squares them, and
sends the results back through another pipe. The main process prints the final
output.
```

## `## How To Run` 

```
Make sure Python 3 is installed. Then run:
```

```
    python filename.py
```

## `## Key Concepts Covered` 

- `Multiprocessing in Python` 

- `Process creation using multiprocessing.Process` 

- `Inter-Process Communication (IPC)` 

- `Pipes for communication between processes` 

- `Producer-Consumer pattern` 

- `Sending and receiving data between processes` 

## `## Advantages` 

- `Simple and effective IPC mechanism` 

- `Improves performance using parallel execution` 

- `Good example of process-based parallelism` 

- `Useful for CPU-intensive tasks` 

## `## Disadvantages` 

- `Pipes are not scalable for large systems` 

- `Debugging multiprocessing code is difficult` 

- `Requires proper closing of pipes` 

- `Not suitable for complex communication systems` 

## `## Expected Output` 

```
0
1
4
9
16
25
36
49
64
81
End
```

## `## Output Explanation` 

- `First process generates numbers from 0 to 9` 

- `Second process receives numbers and squares them` 

- `Results are passed through a second pipe` 

- `Main process prints values until EOFError occurs` 

## `## Notes` 

- `Always close pipes properly to avoid deadlocks` 

- `EOFError is used to stop reading from pipe` 

- `Processes run independently in parallel` 

```
FILE 2 -- communicating_with_queue.txt
```

```
# Chapter 3 - Producer Consumer using multiprocessing Queue
```

## `## What Does It Do` 

```
This program demonstrates the Producer-Consumer problem using Python
multiprocessing.
```

```
A producer process generates random numbers and puts them into a shared queue,
while a consumer process retrieves and processes those items from the queue.
```

## `## How To Run` 

```
Make sure Python 3 is installed. Then run:
```

```
    python filename.py
```

## `## Key Concepts Covered` 

- `Multiprocessing in Python` 

- `Process class inheritance` 

- `Queue for inter-process communication` 

- `Producer-Consumer problem` 

- `Random number generation` 

- `Process synchronization basics` 

## `## Advantages` 

- `Demonstrates real-world producer-consumer model` 

- `Queue ensures safe communication between processes` 

- `Easy way to handle shared data` 

- `Useful for parallel task handling` 

## `## Disadvantages` 

- `Consumer may wait if queue is empty` 

- `Producer and consumer speed mismatch can cause inefficiency` 

- `No advanced synchronization control` 

- `Uses infinite loop logic in consumer` 

## `## Expected Output` 

```
Process Producer : item X appended to queue Process-X
The size of queue is Y
the queue is empty
Process Consumer : item X popped from by Process-X
```

```
(Values will vary because random numbers are used)
```

## `## Output Explanation` 

- `Producer generates random numbers (0–256)` 

- `Items are placed into a shared queue` 

- `Consumer reads items from queue` 

- `Consumer stops when queue becomes empty` 

## `## Notes` 

- `Queue is thread/process-safe in multiprocessing` 

- `random values make output different every run` 

- `sleep() is used to simulate real processing delay` 

```
FILE 3 -- killing_processes.txt
```

```
# Chapter 3 - Process Lifecycle using multiprocessing
```

## `## What Does It Do` 

```
This program demonstrates the lifecycle of a process in Python using the
multiprocessing module.
```

```
It creates a process, starts it, terminates it, and then joins it while showing
```

```
its state at each step.
```

## `## How To Run` 

```
Make sure Python 3 is installed. Then run:
```

```
    python filename.py
```

## `## Key Concepts Covered` 

```
- Process creation using multiprocessing.Process
```

```
- Process states (new, running, terminated, joined)
```

```
- Process start and termination
```

```
- Checking process status using is_alive()
```

```
- Process synchronization using join()
```

```
- Process exit codes
```

## `## Advantages` 

```
- Helps understand process lifecycle clearly
```

```
- Useful for learning process control in multiprocessing
```

```
- Demonstrates process state monitoring
```

```
- Shows how to terminate processes manually
```

## `## Disadvantages` 

```
- Terminating processes abruptly may cause incomplete execution
```

```
- Not suitable for production-level process handling
```

```
- No error handling included
```

- `Can lead to unsafe shutdown if misused` 

## `## Expected Output` 

```
Process before execution: <Process ...> False
Process running: <Process ...> True
Process terminated: <Process ...> False
Process joined: <Process ...> False
Process exit code: -15
```

## `## Output Explanation` 

- `Process is created but not running initially` 

- `After start(), process becomes active` 

```
- terminate() stops the process immediately
```

```
- join() waits for process cleanup
```

```
- exitcode shows termination status
```

## `## Notes` 

```
- terminate() stops process forcefully
```

```
- join() ensures cleanup after termination
```

```
- is_alive() checks current process state
```

```
FILE 4--- myFunc.txt
```

```
# Chapter 3 - Simple Function Execution in Multiprocessing
```

## `## What Does It Do` 

```
This program defines a simple function that prints values based on the input
parameter.
```

```
It is typically used in multiprocessing examples to demonstrate how a function
behaves when executed in separate processes.
```

## `## How To Run` 

```
Make sure Python 3 is installed. Then run:
```

```
    python filename.py
```

```
## Key Concepts Covered
```

- `Function definition in Python` 

- `Loop execution inside functions` 

- `Basic idea of process target functions` 

- `Parameter passing to functions in multiprocessing context` 

## `## Advantages` 

- `Simple and easy to understand` 

- `Helps understand how functions behave in parallel execution` 

- `Useful as a base function for multiprocessing examples` 

- `Lightweight and fast execution` 

## `## Disadvantages` 

- `Does not implement actual multiprocessing itself` 

- `No process management included` 

- `No return value handling in multiprocessing context` 

- `Very basic functionality only` 

## `## Expected Output` 

```
calling myFunc from process n°: X
output from myFunc is :0
output from myFunc is :1
```

```
...
output from myFunc is :(i-1)
```

## `## Output Explanation` 

- `Function prints the process number passed as argument` 

- `Then prints numbers from 0 to i-1` 

- `Output varies depending on input value` 

## `## Notes` 

- `In multiprocessing, return values are not directly captured` 

- `Function is usually used as a target for Process class` 

```
FILE 5 --- naming_processes.txt
```

```
# Chapter 3 - Named and Default Processes in Multiprocessing
```

## `## What Does It Do` 

```
This program demonstrates how to create multiple processes in Python using the
multiprocessing module.
```

```
It shows the difference between a named process and a default process, and how
both run concurrently.
```

## `## How To Run` 

```
Make sure Python 3 is installed. Then run:
```

```
    python filename.py
```

```
## Key Concepts Covered
```

- `Multiprocessing in Python` 

- `Process naming using `name` parameter` 

- `Default process naming` 

- `Concurrent execution of processes` 

- `Using multiprocessing.current_process()` 

- `Process start and join methods` 

## `## Advantages` 

- `Demonstrates concurrent execution clearly` 

- `Shows process naming concept` 

- `Helps understand process identification` 

- `Useful for debugging multiprocessing programs` 

## `## Disadvantages` 

- `No inter-process communication` 

- `No error handling included` 

- `No shared data usage` 

- `Output order is non-deterministic` 

## `## Expected Output` 

```
Starting process name = myFunc process
Starting process name = Process-1
```

```
Exiting process name = myFunc process
Exiting process name = Process-1
```

```
(Note: order may vary due to concurrency)
```

## `## Output Explanation` 

```
- Two processes start simultaneously
```

```
- One process has a custom name
```

```
- Other uses default system-generated name
```

```
- Both processes sleep for 3 seconds and then exit
```

## `## Notes` 

- `Process execution order is not guaranteed` 

```
- join() ensures main program waits for completion
```

- `Naming processes helps in debugging large systems` 

```
FILE 6 --- process_in_subclass.py
```

```
# Chapter 3 - Custom Process Class in Multiprocessing
```

## `## What Does It Do` 

```
This program demonstrates how to create a custom process class by inheriting
from `multiprocessing.Process`.
Each process overrides the `run()` method and executes custom logic when
started.
```

## `## How To Run` 

```
Make sure Python 3 is installed. Then run:
```

```
    python filename.py
```

## `## Key Concepts Covered` 

```
- Multiprocessing in Python
```

```
- Inheriting from multiprocessing.Process
```

```
- Overriding the run() method
```

```
- Process creation using custom classes
```

```
- Process start and join mechanism
```

```
- Sequential process execution in loop
```

## `## Advantages` 

```
- Clean object-oriented approach to multiprocessing
```

```
- Easy to extend process behavior
```

```
- Better structure for large applications
```

- `Helps organize complex process logic` 

## `## Disadvantages` 

```
- Slight overhead due to class structure
```

```
- No parallel speed gain here due to join inside loop
```

```
- No inter-process communication
```

- `Limited functionality in this simple example` 

## `## Expected Output` 

```
called run method in MyProcess-1
```

```
called run method in MyProcess-2
...
```

```
called run method in MyProcess-10
```

## `## Output Explanation` 

- `Each iteration creates a new process` 

- `run() method is automatically executed` 

- `join() ensures each process finishes before next starts` 

- `Processes run one after another (not fully parallel due to join in loop)` 

## `## Notes` 

- `Overriding run() is standard way to define process behavior` 

- `Using join inside loop makes execution sequential` 

- `Without join inside loop, processes would run in parallel` 

```
FILE 7 ---  process_pool.txt
```

## `# Chapter 3 - Using a Process Pool (Multiprocessing Pool)` 

## `## What Does It Do` 

```
This program demonstrates how to use a process pool in Python's multiprocessing
module.
```

```
It distributes a task (squaring numbers) across multiple processes to execute in
parallel and collects the results.
```

## `## How To Run` 

```
Make sure Python 3 is installed. Then run:
```

```
    python filename.py
```

## `## Key Concepts Covered` 

- `Multiprocessing Pool` 

- `Process pool management` 

- `map() function for parallel execution` 

- `Function mapping across multiple inputs` 

- `Parallel computation using multiple CPU cores` 

## `## Advantages` 

- `Efficient parallel processing` 

- `Automatically manages multiple processes` 

- `Faster execution for large datasets` 

- `Simple syntax using pool.map()` 

## `## Disadvantages` 

- `Limited control over individual processes` 

- `Overhead in process creation and management` 

- `Not suitable for very small tasks` 

- `Requires careful handling of pool closure` 

```
## Expected Output
```

```
Pool : [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, ..., 9801]
```

## `## Output Explanation` 

- `Input range is 0 to 99` 

- `Each number is squared using multiple processes` 

- `Results are collected in a list` 

- `Final output is printed as a complete list` 

## `## Notes` 

- `pool.map() distributes tasks automatically` 

- `pool.close() prevents new tasks from being submitted` 

- `pool.join() waits for all processes to finish` 

```
FILE 8 --- processes_barrier.txt
```

```
# Chapter 3 - Barrier and Lock Synchronization in Multiprocessing
```

```
## What Does It Do
```

```
This program demonstrates synchronization between multiple processes using a
Barrier and a Lock.
```

```
Some processes wait for each other using a Barrier before continuing execution,
while others run without synchronization.
```

```
## How To Run
```

```
Make sure Python 3 is installed. Then run:
```

```
    python filename.py
```

```
## Key Concepts Covered
```

```
- Multiprocessing in Python
```

- `Barrier synchronization` 

```
- Lock for safe printing (serialization)
```

```
- Process coordination
```

- `Concurrent execution timing` 

- `Process naming` 

## `## Advantages` 

- `Demonstrates process synchronization clearly` 

```
- Barrier ensures processes reach a common point before continuing
```

- `Lock prevents mixed output in console` 

- `Useful for controlled parallel execution` 

## `## Disadvantages` 

- `Synchronization adds overhead` 

- `Barrier can cause waiting delays` 

- `Complexity increases with more processes` 

- `Not suitable when tasks are independent` 

## `## Expected Output` 

```
process p1 - test_with_barrier ----> 2026-xx-xx xx:xx:xx
process p2 - test_with_barrier ----> 2026-xx-xx xx:xx:xx
process p3 - test_without_barrier ----> 2026-xx-xx xx:xx:xx
process p4 - test_without_barrier ----> 2026-xx-xx xx:xx:xx
```

```
(Note: exact order may vary due to scheduling)
```

## `## Output Explanation` 

```
- p1 and p2 wait at Barrier until both reach synchronizer.wait()
```

```
- After barrier is released, they print synchronized time
```

```
- p3 and p4 run independently without waiting
```

- `Lock ensures clean printing without overlapping output` 

## `## Notes` 

- `Barrier is used when processes must start a step together` 

- `Lock ensures only one process prints at a time` 

- `Time may differ slightly between processes` 

```
FILE 9 ---  run_background_processes.txt
```

## `# Chapter 3 - Daemon vs Non-Daemon Processes in Multiprocessing` 

## `## What Does It Do` 

```
This program demonstrates the difference between daemon and non-daemon processes
in Python multiprocessing.
It creates two processes: one runs as a background (daemon) process and the
other runs normally.
```

```
## How To Run
```

```
Make sure Python 3 is installed. Then run:
```

```
    python filename.py
```

## `## Key Concepts Covered` 

```
- Multiprocessing in Python
```

```
- Daemon processes
```

- `Non-daemon processes` 

```
- Process naming using current_process()
```

- `Background execution` 

- `Process lifecycle behavior` 

## `## Advantages` 

- `Demonstrates background process concept clearly` 

```
- Useful for understanding system-level process behavior
```

```
- Helps learn difference between daemon and normal processes
```

```
- Shows concurrent execution behavior
```

## `## Disadvantages` 

```
- Daemon processes may terminate abruptly
```

```
- No guaranteed completion of daemon process
```

- `No synchronization used` 

- `Output order is unpredictable` 

## `## Expected Output` 

```
Starting background_process
Starting NO_background_process
```

```
---> 0
---> 1
---> 2
---> 3
---> 4
---> 5
---> 6
---> 7
---> 8
---> 9
```

```
Exiting background_process
Exiting NO_background_process
```

```
(Note: daemon process may stop early depending on execution timing)
```

## `## Output Explanation` 

- `background_process runs as daemon (background task)` 

- `NO_background_process runs normally` 

- `Daemon process may terminate when main program exits` 

- `Each process prints its own loop output` 

## `## Notes` 

- `daemon=True means process runs in background` 

- `daemon processes may not complete execution` 

- `Non-daemon processes complete fully before program exit` 

```
FILE 10 --- run_background_processes_no_daemons.txt
```

```
# Chapter 3 - Daemon Flag Set to False in Multiprocessing
```

```
## What Does It Do
```

```
This program demonstrates the behavior of non-daemon processes in Python
multiprocessing.
```

```
Two processes are created and both are explicitly set as non-daemon, meaning
both will complete their execution independently.
```

## `## How To Run` 

```
Make sure Python 3 is installed. Then run:
```

```
    python filename.py
```

## `## Key Concepts Covered` 

- `Multiprocessing in Python` 

- `Process creation using multiprocessing.Process` 

- `Daemon flag (set to False)` 

- `Process naming using current_process()` 

- `Independent process execution` 

- `Concurrent execution` 

## `## Advantages` 

- `Ensures both processes complete execution` 

- `No unexpected termination of processes` 

- `Good for reliable parallel tasks` 

- `Helps understand process lifecycle behavior` 

## `## Disadvantages` 

- `No background/daemon optimization` 

- `Can consume more system resources` 

- `No synchronization between processes` 

- `Output order is not predictable` 

## `## Expected Output` 

```
Starting background_process
Starting NO_background_process
```

```
---> 0
---> 1
---> 2
---> 3
---> 4
---> 5
---> 6
---> 7
---> 8
---> 9
```

```
Exiting background_process
Exiting NO_background_process
```

## `## Output Explanation` 

- `Both processes run as normal (daemon = False)` 

- `Each process executes its own loop` 

- `No process is killed early` 

- `Execution is fully completed before program ends` 

## `## Notes` 

- `daemon=False ensures safe completion` 

- `Both processes run independently` 

- `Output order may still vary due to scheduling` 

```
FILE 11 --- spawning_processes.txt
```

```
# Chapter 3 - Spawning Processes using multiprocessing
```

```
## What Does It Do
```

```
This program demonstrates how to spawn multiple processes dynamically using
Python's multiprocessing module.
```

```
Each process runs the same function with different input values and executes
independently.
```

```
## How To Run
```

```
Make sure Python 3 is installed. Then run:
```

```
    python filename.py
```

```
## Key Concepts Covered
```

```
- Multiprocessing in Python
```

```
- Process spawning
```

```
- Process creation in loops
```

```
- Passing arguments to processes
```

```
- Process start and join methods
- Concurrent execution basics
```

```
## Advantages
```

```
- Simple way to create multiple processes
```

```
- Each process runs independently
```

```
- Easy to pass parameters to processes
```

```
- Useful for parallel task execution
```

```
## Disadvantages
```

```
- join() inside loop makes execution sequential
- No real parallel speed improvement in this example
```

```
- No inter-process communication
```

- `Limited scalability in this structure` 

## `## Expected Output` 

```
calling myFunc from process n°: 0
calling myFunc from process n°: 1
output from myFunc is :0
calling myFunc from process n°: 2
output from myFunc is :0
output from myFunc is :1
...
```

```
(Note: exact order may vary due to scheduling)
```

```
## Output Explanation
```

```
- A loop creates 6 separate processes
```

```
- Each process runs myFunc with different input
```

```
- Each process prints numbers from 0 to i-1
```

```
- join() ensures each process completes before moving next
```

## `## Notes` 

```
- Process execution order is not guaranteed
```

- `join() controls synchronization - Removing join() would allow true parallel execution` 

```
FILE 12 --- spawning_processes_namespace.txt
```

```
# Chapter 3 - Importing Function from External File with Multiprocessing
```

```
## What Does It Do
```

```
This program demonstrates how to use a function defined in a separate Python
```

```
file with multiprocessing.
It imports `myFunc` from an external module and runs it in multiple processes.
```

```
## How To Run
```

```
Make sure Python 3 is installed. Then run:
```

```
1. Ensure both files exist:
```

```
   - main file (this script)
```

```
   - myFunc.py (contains function definition)
```

```
2. Run:
```

```
    python filename.py
```

```
## Key Concepts Covered
```

```
- Multiprocessing in Python
```

```
- Importing functions from external modules
- Process creation using Process class
- Passing arguments to processes
- Code modularity
- Process lifecycle management
```

```
## Advantages
```

```
- Improves code organization (modular design)
- Reusable function across multiple processes
- Clean separation of logic
```

```
- Easy to maintain in large projects
```

## `## Disadvantages` 

```
- Requires multiple files setup
```

```
- Import errors if file path is incorrect
- join() inside loop reduces parallel execution
- No inter-process communication
```

## `## Expected Output` 

```
calling myFunc from process n°: 0
output from myFunc is :0
calling myFunc from process n°: 1
output from myFunc is :0
output from myFunc is :1
...
```

## `(Note: output order may vary depending on scheduling)` 

## `## Output Explanation` 

- `myFunc is imported from external file `myFunc.py`` 

- `Each process runs myFunc with different value of i` 

- `Processes execute one by one due to join() inside loop` 

- `Each process prints its own output sequence` 

## `## Notes` 

- `External module must be in same directory` 

- `Proper import is required for multiprocessing to work` 

- `join() ensures sequential execution in this example` 

