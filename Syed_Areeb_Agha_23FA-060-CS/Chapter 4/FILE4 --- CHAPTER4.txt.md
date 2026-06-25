```
FILE1 --- alltoall.txt
```

```
# Chapter 3 - MPI Alltoall Communication using mpi4py
```

```
## What Does It Do
```

```
This program demonstrates parallel communication between multiple processes
using MPI (Message Passing Interface) via the `mpi4py` library.
Each process sends and receives data from all other processes using the
`Alltoall` communication pattern.
```

## `## How To Run` 

```
Make sure Python 3 is installed and `mpi4py` is available.
```

```
Install requirements:
    pip install mpi4py numpy
```

```
Run using MPI launcher:
```

```
    mpiexec -n 4 python filename.py
```

```
## Key Concepts Covered
```

```
- MPI (Message Passing Interface)
```

```
- mpi4py library usage
```

- `Process rank and size` 

```
- Collective communication (Alltoall)
```

- `Distributed memory systems` 

- `Parallel data exchange` 

```
## Advantages
```

```
- True distributed parallel processing
```

```
- Efficient communication between processes
```

- `Scales well on multi-core/multi-node systems` 

- `Useful for high-performance computing (HPC)` 

```
## Disadvantages
```

- `Requires MPI setup (more complex environment)` 

```
- Harder to debug than multiprocessing
```

- `Not beginner-friendly` 

- `Needs external runtime (mpiexec)` 

## `## Expected Output` 

```
process 0 sending [0 0 0 0] receiving [...]
process 1 sending [1 2 3 4] receiving [...]
process 2 sending [2 4 6 8] receiving [...]
process 3 sending [3 6 9 12] receiving [...]
```

```
(Note: exact values depend on number of processes)
```

## `## Output Explanation` 

```
- Each process gets a unique rank (0 to size-1)
```

- `Each process creates a send array based on its rank` 

- ``Alltoall` distributes data between all processes` 

- `Each process receives combined data from all others` 

## `## Notes` 

```
- Requires MPI environment (not just Python)
```

- `Must run with mpiexec or mpirun` 

- `Best suited for distributed systems and HPC clusters` 

```
FILE 2 --- broadcast.txt
```

```
# Chapter 3 - Broadcasting Data using mpi4py (MPI bcast)
```

```
## What Does It Do
```

```
This program demonstrates how to share a single value from one process to all
other processes using MPI broadcast (bcast).
Process 0 initializes a variable, and all other processes receive the same
value.
```

## `## How To Run` 

```
Make sure Python 3 is installed and mpi4py is installed.
```

```
Install dependencies:
    pip install mpi4py
```

```
Run using MPI:
```

```
    mpiexec -n 4 python filename.py
```

```
## Key Concepts Covered
```

```
- MPI communication model
```

```
- Process rank system
- Broadcast (bcast) operation
- Root process concept
```

```
- Data sharing in distributed systems
```

## `## Advantages` 

```
- Efficient way to share data across processes
```

```
- Reduces need for repeated communication
```

```
- Ensures all processes get same value
```

- `Useful in parallel initialization` 

```
## Disadvantages
```

```
- Only one-to-all communication (limited flexibility)
```

```
- Requires MPI setup
```

```
- Not suitable for dynamic data exchange
```

- `Debugging distributed code is difficult` 

## `## Expected Output` 

```
process = 0 variable shared = 100
process = 1 variable shared = 100
process = 2 variable shared = 100
process = 3 variable shared = 100
```

```
## Output Explanation
```

```
- Process 0 sets the value (100)
```

```
- All other processes receive this value using broadcast
```

- `MPI ensures synchronization across all processes` 

## `## Notes` 

- `bcast is a collective communication function` 

```
- All processes must call bcast
```

- `root process defines the original data source` 

```
FILE 3 ---deadLockProblems.py
```

```
# Chapter 3 - Point-to-Point Communication using mpi4py (send/recv)
```

## `## What Does It Do` 

```
This program demonstrates point-to-point communication between two specific MPI
processes using `send()` and `recv()`.
Process 1 and Process 5 exchange messages directly with each other.
```

```
## How To Run
```

```
Make sure Python 3 and mpi4py are installed.
```

```
Install dependency:
    pip install mpi4py
```

```
Run using MPI:
```

```
    mpiexec -n 6 python filename.py
```

```
## Key Concepts Covered
```

```
- MPI ranks
```

```
- Point-to-point communication
- send() and recv() functions
- Source and destination processes
- Blocking communication
- Direct process messaging
```

## `## Advantages` 

```
- Simple direct communication between processes
```

```
- Useful for controlled data exchange
```

```
- Easy to understand MPI messaging
```

```
- Good for small distributed tasks
```

## `## Disadvantages` 

```
- Not scalable for large systems
```

```
- Risk of deadlock if order is incorrect
```

```
- Requires careful rank management
```

- `Blocking calls may slow execution` 

```
## Expected Output
```

```
my rank is X
(my rank 1 and 5 will exchange messages)
```

```
sending data a to process 5
data received is = b
```

```
sending data b to process 1
data received is = a
```

```
## Output Explanation
```

```
- Rank 1 sends "a" to rank 5 and receives "b"
```

```
- Rank 5 sends "b" to rank 1 and receives "a"
```

```
- Other ranks do nothing except print their rank
```

```
- Communication happens only between two processes
```

## `## Notes` 

```
- Order of send/recv is critical to avoid deadlock
```

```
- Must run with at least 6 processes
```

- `Each process executes same script but different rank logic` 

```
FILE 4 --- gather.txt
```

```
# Chapter 3 - Gathering Data using mpi4py (MPI gather)
```

```
## What Does It Do
```

```
This program demonstrates the MPI gather operation, where all processes send
their computed values to a single root process (rank 0).
Each process calculates a value, and the root process collects all values into a
list.
```

```
## How To Run
Make sure Python 3 and mpi4py are installed.
```

```
Install dependency:
    pip install mpi4py
```

```
Run using MPI:
```

```
    mpiexec -n 4 python filename.py
```

```
## Key Concepts Covered
```

```
- MPI gather operation
```

```
- Process rank and size
```

```
- Collective communication
```

```
- Data aggregation at root process
```

```
- Distributed computation
```

## `## Advantages` 

```
- Efficient way to collect distributed results
```

```
- Reduces manual communication complexity
```

```
- Useful for final result aggregation
```

```
- Works well in parallel computing tasks
```

## `## Disadvantages` 

```
- Only root process receives full data
```

```
- Can cause memory load on root process
```

```
- Not suitable for real-time streaming data
```

```
- Requires synchronization of all processes
```

```
## Expected Output
```

```
rank = 0 ...receiving data to other process
process 0 receiving X from process 1
process 0 receiving Y from process 2
process 0 receiving Z from process 3
```

```
(Note: values depend on rank computations)
```

```
## Output Explanation
```

```
- Each process computes: (rank + 1)^2
```

```
- All values are sent to process 0 using gather
```

```
- Process 0 receives a list of all values
```

```
- Root process prints received values from each process
```

## `## Notes` 

```
- gather is a collective operation
```

```
- Only root process processes final collected data
```

```
- All processes must call gather
```

```
FILE 5 --- helloworld_MPI.txt
```

```
# Chapter 3 - Hello World using mpi4py (MPI Basics)
```

```
## What Does It Do
```

```
This is a basic MPI program that demonstrates how multiple processes run in
parallel using `mpi4py`.
Each process prints a simple "hello world" message along with its unique rank
(process ID).
```

```
## How To Run
Make sure Python 3 and mpi4py are installed.
```

```
Install dependency:
    pip install mpi4py
```

```
Run using MPI:
    mpiexec -n 4 python hello.py
```

```
## Key Concepts Covered
- MPI initialization
- Process rank identification
- Parallel execution
- mpi4py basics
- Distributed processes
```

```
## Advantages
- Very simple introduction to MPI
- Helps understand process ranks
- Confirms parallel execution setup
- Useful as a sanity test for MPI environment
```

```
## Disadvantages
- No actual computation or communication
- Only prints output
- Not useful for real-world processing
- Very basic example
```

```
## Expected Output
```

```
hello world from process 0
hello world from process 1
hello world from process 2
hello world from process 3
```

```
## Output Explanation
- Each process runs independently
- Each process prints its own rank
- Number of processes depends on mpiexec -n value
- Output order may vary
```

```
## Notes
- This is usually the first MPI program
- Used to verify MPI installation
- Each process executes the same script
```

```
FILE 6 --- pointToPointCommunication.txt
```

```
# Chapter 3 - Point-to-Point Communication (Multiple Send/Recv)
```

```
## What Does It Do
This program demonstrates MPI point-to-point communication between multiple
processes using `send()` and `recv()`.
Different processes send different types of data to different destination
processes.
```

```
## How To Run
Make sure Python 3 and mpi4py are installed.
```

```
Install dependency:
    pip install mpi4py
```

```
Run using MPI:
    mpiexec -n 9 python filename.py
```

```
## Key Concepts Covered
- MPI ranks
```

```
- Point-to-point communication
```

```
- send() and recv() functions
```

- `Multiple sender/receiver pairs` 

- `Blocking communication` 

- `Process mapping` 

## `## Advantages` 

```
- Demonstrates real-world message passing
```

```
- Supports multiple independent communication channels
```

- `Easy to understand rank-based logic` 

- `Useful for distributed workflows` 

## `## Disadvantages` 

- `Requires careful rank coordination` 

```
- High risk of mismatch in send/recv pairs
```

```
- Not scalable for large systems
```

```
- Debugging communication errors is difficult
```

## `## Expected Output` 

```
my rank is : 0
my rank is : 1
my rank is : 4
my rank is : 8
```

```
sending data 10000000 to process 4
sending data hello to process 8
```

```
data received is = 10000000
data1 received is = hello
```

```
## Output Explanation
```

```
- Rank 0 sends integer data to rank 4
```

```
- Rank 1 sends string data to rank 8
```

```
- Rank 4 receives data from rank 0
```

```
- Rank 8 receives data from rank 1
```

```
- Other ranks only print their rank
```

## `## Notes` 

```
- Each send must match a corresponding recv
```

```
- Program must be run with at least 9 processes
```

- `Order of output may vary due to parallel execution` 

```
FILE 7 --- reduction.txt
```

```
# Chapter 3 - MPI Reduce Operation using mpi4py
```

## `## What Does It Do` 

```
This program demonstrates the MPI Reduce operation using `mpi4py`.
Each process creates an array of numbers, and all arrays are combined (summed)
into a single result at the root process (rank 0).
```

## `## How To Run` 

```
Make sure Python 3, mpi4py, and numpy are installed.
```

```
Install dependencies:
    pip install mpi4py numpy
```

```
Run using MPI:
```

```
    mpiexec -n 4 python filename.py
```

```
## Key Concepts Covered
```

```
- MPI Reduce operation
```

```
- Collective communication
```

```
- Data aggregation using operations (SUM)
```

```
- Numpy arrays in parallel computing
```

- `Process rank and size` 

- `Root process concept` 

## `## Advantages` 

```
- Efficient aggregation of distributed data
```

```
- Reduces communication overhead
```

```
- Useful for mathematical computations
```

- `Supports array-based operations` 

## `## Disadvantages` 

```
- Only root process gets final result
```

```
- Requires synchronization of all processes
```

```
- Not suitable for partial result visibility
```

- `Debugging distributed reductions can be complex` 

## `## Expected Output` 

```
process 0 sending [...]
process 1 sending [...]
process 2 sending [...]
process 3 sending [...]
```

```
on task 0 after Reduce: data = [SUM_RESULT_ARRAY]
```

## `## Output Explanation` 

- `Each process creates an array using its rank` 

- `MPI Reduce sums all arrays element-wise` 

- `Final result is stored only in root process (rank 0)` 

- `Other processes receive empty/zero arrays` 

## `## Notes` 

- `MPI_SUM is used as the reduction operation` 

```
- All processes must participate in Reduce
```

- `Root process collects final aggregated data` 

```
FILE 8 --- scatter.txt
```

```
# Chapter 3 - MPI Scatter Operation using mpi4py
```

## `## What Does It Do` 

```
This program demonstrates the MPI Scatter operation using `mpi4py`.
A list of data is divided and distributed from the root process (rank 0) to all
other processes.
```

```
Each process receives one element from the original array.
```

## `## How To Run` 

```
Make sure Python 3 and mpi4py are installed.
```

```
Install dependency:
    pip install mpi4py
```

```
Run using MPI:
```

```
    mpiexec -n 10 python filename.py
```

```
## Key Concepts Covered
```

- `MPI Scatter operation` 

- `Collective communication` 

- `Data distribution from root process` 

- `Process ranks` 

- `Parallel data handling` 

- `Load distribution` 

```
## Advantages
```

- `Efficient way to distribute data` 

- `Reduces manual data assignment` 

- `Useful for parallel computations` 

- `Balanced workload distribution` 

```
## Disadvantages
```

- `Requires fixed number of processes` 

- `Only root process holds full dataset initially` 

- `Not flexible for dynamic workloads` 

- `Debugging distributed execution is complex` 

## `## Expected Output` 

```
process = 0 variable shared = 1
process = 1 variable shared = 2
process = 2 variable shared = 3
...
process = 9 variable shared = 10
```

```
## Output Explanation
```

- `Rank 0 holds full array` 

- `MPI Scatter divides array into parts` 

- `Each process receives one element` 

- `Each process prints its assigned value` 

```
## Notes
```

- `Number of processes must match array size` 

- `All processes must call scatter` 

- `root process distributes data equally` 

```
FILE 9 --- virtualTopology.txt
```

```
# Chapter 3 - Cartesian Grid Topology using mpi4py (MPI Cart)
```

```
## What Does It Do
```

```
This program demonstrates how MPI can create a 2D Cartesian grid topology using
`Create_cart()`.
Each process is placed in a virtual grid and identifies its neighboring
processes (UP, DOWN, LEFT, RIGHT).
```

```
## How To Run
```

```
Make sure Python 3, mpi4py, and numpy are installed.
```

```
Install dependencies:
    pip install mpi4py numpy
```

```
Run using MPI:
```

```
    mpiexec -n 4 python filename.py
```

```
(or higher number like 9, 16 for better grid visualization)
```

```
## Key Concepts Covered
```

- `MPI Cartesian topology` 

- `Create_cart() function` 

- `Process grid mapping` 

- `Neighbor discovery using Shift()` 

- `Periodic boundary conditions` 

- `2D grid communication structure` 

## `## Advantages` 

- `Useful for grid-based parallel problems` 

- `Simplifies neighbor communication` 

- `Supports structured parallel algorithms` 

- `Efficient for scientific computing (e.g., simulations)` 

## `## Disadvantages` 

- `Requires understanding of MPI topology` 

- `Grid size depends on number of processes` 

- `Harder to debug than linear communication` 

- `Not useful for simple tasks` 

## `## Expected Output` 

```
Process = 0 row = X column = Y
```

```
---->
neighbour_processes[UP] = ...
neighbour_processes[DOWN] = ...
neighbour_processes[LEFT] = ...
neighbour_processes[RIGHT] = ...
```

```
(Each process prints its position and neighbors)
```

```
## Output Explanation
```

- `MPI creates a 2D grid of processes` 

- `Each process is assigned (row, column)` 

- ``Shift()` finds neighboring processes in each direction` 

- `Periodic=True means edges wrap around (like a torus)` 

## `## Notes` 

- `Grid dimensions depend on total number of processes` 

- `Best visualization with 4, 9, 16 processes` 

- `Useful for simulations like heat transfer, fluid dynamics` 

- `reorder=True allows MPI to optimize process mapping` 

