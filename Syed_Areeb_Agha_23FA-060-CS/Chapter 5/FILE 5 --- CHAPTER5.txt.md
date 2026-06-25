```
FILE 5 --- asyncio_and_futures.txt
```

```
# Chapter 4 - Asyncio Future with Multiple Coroutines
```

```
## What Does It Do
```

```
This program demonstrates the use of asyncio Futures and coroutines in Python.
It runs two separate asynchronous tasks:
```

`1. Sum of N integers` 

`2. Factorial of N numbers` 

```
Each coroutine computes its result and stores it in a Future object, which is
then printed using a callback.
```

## `## How To Run` 

```
Make sure Python 3 is installed.
```

```
Run from terminal:
```

```
    python filename.py 5 5
```

```
(First argument = N for sum, second argument = N for factorial)
```

```
## Key Concepts Covered
```

- `Asyncio coroutines` 

- `asyncio.Future object` 

- `Event loop management` 

- `Callback functions (add_done_callback)` 

- `Concurrent execution of tasks` 

- `yield from (old async style)` 

## `## Advantages` 

- `Runs multiple tasks concurrently` 

- `Demonstrates Future-based async programming` 

- `Useful for understanding task completion callbacks` 

- `Efficient for I/O or delayed computations` 

## `## Disadvantages` 

- `Uses deprecated @asyncio.coroutine style` 

- `Not modern async/await syntax` 

- `Manual Future handling increases complexity` 

- `Not truly CPU parallel (single-threaded event loop)` 

## `## Expected Output` 

```
First coroutine (sum of N ints) result = X
Second coroutine (factorial) result = Y
```

```
## Output Explanation
```

- `first_coroutine calculates sum from 1 to N` 

- `second_coroutine calculates factorial of N` 

- `Both run concurrently using asyncio event loop` 

- `Results are stored in Future objects` 

- `Callback prints result when each Future completes` 

## `## Notes` 

- `sys.argv is used for input values` 

- `asyncio.wait() runs both coroutines together` 

- `loop.close() ensures proper cleanup` 

- `Execution order of outputs may vary` 

## `FILE2 --- asyncio_coroutine.txt` 

```
# Chapter 4 - Finite State Machine using Asyncio Coroutines
```

```
## What Does It Do
```

```
This program simulates a Finite State Machine (FSM) using Python's `asyncio`
module.
```

```
It defines multiple states (state1, state2, state3, end_state) and transitions
between them randomly using coroutine-based execution.
```

## `## How To Run` 

```
Make sure Python 3 is installed.
```

```
Run:
```

```
    python filename.py
```

```
## Key Concepts Covered
```

```
- Asyncio coroutines
```

```
- Finite State Machine (FSM)
- yield from (coroutine chaining)
```

```
- Event-driven programming
- Random state transitions
- Event loop execution
```

## `## Advantages` 

```
- Demonstrates asynchronous programming concept
```

```
- Good model for state-based systems
```

- `Shows non-linear execution flow` 

- `Useful for learning async control flow` 

## `## Disadvantages` 

- `Uses outdated asyncio.coroutine style (modern Python uses async/await)` 

```
- time.sleep() blocks event loop (not truly async)
```

- `Complex flow is hard to debug` 

- `Random behavior makes output non-deterministic` 

## `## Expected Output` 

```
Finite State Machine simulation with Asyncio Coroutine
Start State called
```

```
...evaluating...
...evaluating...
...stop computation...
```

```
Resume of the Transition :
Start State calling State X ...
```

```
(Note: output changes every run due to randomness)
```

## `## Output Explanation` 

- `start_state() begins execution` 

- `Randomly transitions to state1 or state2` 

- `Each state may call another state randomly` 

- `Process continues until end_state is reached` 

- `Execution simulates FSM behavior` 

## `## Notes` 

- `This is coroutine-based FSM simulation` 

- `Modern Python should use async/await instead of @asyncio.coroutine` 

- `time.sleep() should be replaced with asyncio.sleep() for real async behavior` 

- `Execution path is random due to randint()` 

## `FILE 3 --- asyncio_event_loop.txt` 

```
# Chapter 4 - Asyncio Event Loop with call_later Scheduling
```

```
## What Does It Do
```

```
This program demonstrates manual event loop control using asyncio in Python.
It creates three tasks (task_A, task_B, task_C) that call each other in a cyclic
order using `call_later()` until a time limit is reached.
```

## `## How To Run` 

```
Make sure Python 3 is installed.
```

```
Run:
```

```
    python filename.py
```

```
## Key Concepts Covered
- Asyncio event loop
- call_soon() scheduling
- call_later() delayed execution
- Event loop time management
- Task chaining (A → B → C cycle)
- loop.run_forever()
```

```
## Advantages
```

```
- Demonstrates low-level event loop control
```

```
- Shows how tasks can be scheduled manually
```

```
- Useful for understanding async scheduling internals
- Simulates cyclic task execution
```

```
## Disadvantages
```

```
- Uses blocking time.sleep() (not truly async)
```

```
- Hard to manage and debug
```

```
- Not modern async/await style
```

```
- Can lead to inefficient execution
```

## `## Expected Output` 

```
task_A called
task_B called
task_C called
task_A called
task_B called
...
```

```
(Repeats until time limit is reached)
```

```
## Output Explanation
```

```
- task_A starts first using call_soon()
```

```
- Each task schedules the next task using call_later()
```

```
- Tasks run in a cycle: A → B → C → A
```

```
- loop runs until end_loop time is reached
```

- `loop.stop() ends execution` 

## `## Notes` 

- `This is a manual event loop example` 

```
- time.sleep() blocks the loop (should be asyncio.sleep in modern code)
```

- `loop.run_forever() keeps program running until stopped` 

## `FILE 4 --- asyncio_task_manipulation.txt` 

## `# Chapter 4 - Asyncio Tasks Running in Parallel` 

## `## What Does It Do` 

```
This program demonstrates the use of asyncio.Task to run multiple mathematical
```

```
functions concurrently in Python.
It executes three tasks in parallel:
```

`1. Factorial calculation` 

`2. Fibonacci sequence generation` 

`3. Binomial coefficient calculation` 

```
All tasks run concurrently using the asyncio event loop.
```

```
## How To Run
```

```
Make sure Python 3 is installed.
```

## `Run:` 

```
    python filename.py
```

- `## Key Concepts Covered - asyncio.Task` 

- `Coroutine execution` 

- `Concurrent task scheduling` 

- `Event loop management` 

- `yield from (old asyncio style) - Parallel execution of functions` 

```
## Advantages
```

- `Runs multiple tasks concurrently` 

- `Efficient for asynchronous workloads` 

- `Demonstrates task scheduling clearly` 

- `Useful for learning asyncio fundamentals` 

## `## Disadvantages` 

- `Uses outdated @asyncio.coroutine syntax` 

- `factorial function has missing variable issue (fact undefined)` 

- `Not truly parallel CPU execution` 

- `Blocking-style logic inside coroutines` 

## `## Expected Output` 

```
Asyncio.Task: Compute fibonacci(0)
Asyncio.Task: Compute binomial_coefficient(1)
Asyncio.Task: Compute fibonacci(1)
...
Asyncio.Task - fibonacci(10) = X
Asyncio.Task - binomial_coefficient(20, 10) = Y
```

```
(Note: order may vary due to concurrency)
```

## `## Output Explanation` 

- `Three tasks are scheduled using asyncio.Task` 

- `Event loop runs them concurrently` 

- `Each task yields control using asyncio.sleep` 

- `Results are printed when each coroutine completes` 

## `## Notes` 

- `This is cooperative multitasking (not multi-threading)` 

- `asyncio.Task schedules coroutines concurrently` 

- `Code has a bug: factorial uses undefined variable `fact`` 

- `Modern Python should use async/await instead of @asyncio.coroutine` 

```
FILE 5 ---  concurrent_futures_pooling.txt
```

```
# Chapter 5 - Sequential vs ThreadPool vs ProcessPool Execution
```

```
## What Does It Do
```

```
This program compares three different execution models in Python:
```

`1. Sequential execution (single thread)` 

`2. Thread pool execution (ThreadPoolExecutor)` 

`3. Process pool execution (ProcessPoolExecutor)` 

```
It runs a CPU-heavy function (`count`) on a list of numbers and measures
execution time for each method.
```

## `## How To Run` 

```
Make sure Python 3 is installed.
```

## `Run:` 

```
    python filename.py
```

```
## Key Concepts Covered
```

- `Sequential execution` 

- `concurrent.futures module` 

- `ThreadPoolExecutor` 

- `ProcessPoolExecutor` 

- `Parallel vs concurrent execution` 

- `Performance comparison` 

- `CPU-bound task handling` 

## `## Advantages` 

- `Clear comparison of execution models` 

- `Demonstrates multiprocessing vs multithreading` 

- `Useful for understanding performance tradeoffs` 

- `Easy to extend for benchmarking` 

## `## Disadvantages` 

- `Uses time.clock() (deprecated in modern Python)` 

- `Threading not effective for CPU-heavy tasks (GIL limitation)` 

- `Overhead in process creation` 

- `No proper result collection handling` 

## `## Expected Output` 

```
Item 1, result X
Item 2, result Y
...
Sequential Execution in T1 seconds
Item 1, result X
...
Thread Pool Execution in T2 seconds
Item 1, result X
...
Process Pool Execution in T3 seconds
```

## `## Output Explanation` 

- `First runs sequential loop (one by one execution)` 

- `Then runs same tasks using thread pool (5 workers)` 

- `Then runs using process pool (true parallel execution)` 

- `Time comparison shows performance differences` 

## `## Notes` 

- `ProcessPoolExecutor is best for CPU-bound tasks` 

- `ThreadPoolExecutor is better for I/O-bound tasks` 

- `time.clock() should be replaced with time.perf_counter() in modern Python` 

