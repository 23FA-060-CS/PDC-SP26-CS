FILE 1 --- Barrier_README.txt  Barrier.py - README

# What Does It Do This program simulates a race between 3 runners
using Python threading. Each runner runs in a separate thread and sleeps
for a random time (2-5 seconds). A Barrier is used to make all threads
wait until every runner has finished before printing \"Race over!\".

# How To Run

python Barrier.py

# Key Concepts Covered - threading.Barrier to synchronize multiple
threads - threading.Thread for concurrent execution - Random sleep to
simulate different speeds - ctime() to display current time

# Advantages - Clean example of thread synchronization - Barrier
ensures all threads reach the same point before continuing - Easy to
scale by changing num_runners

# Disadvantages - runners list is shared and uses pop() which can
cause issues if not thread-safe - No error handling - Hardcoded number
of runners

# Expected Output

START RACE!!!! Huey reached the barrier at: \[time\] Dewey reached the
barrier at: \[time\] Louie reached the barrier at: \[time\] Race over!

FILE 2 --- condition_README.txt \# condition.py - README

# What Does It Do This program demonstrates the Producer-Consumer
problem using threading.Condition. The Producer adds items to a shared
list (max 10). The Consumer removes items from the list. Both threads
communicate using condition.wait() and condition.notify().

# How To Run

python condition.py

# Key Concepts Covered - threading.Condition for thread
communication - Producer-Consumer design pattern - condition.wait() to
pause a thread - condition.notify() to wake up a waiting thread -
logging module for timestamped output

# Advantages - Solves a classic concurrency problem - Condition
variable prevents busy waiting - Logging gives clear visibility of
thread activity

# Disadvantages - Fixed number of iterations (20), not dynamic -
Consumer sleeps 2 seconds which is slower than producer (0.5s), can
cause lag - No graceful shutdown mechanism

# Expected Output

\[timestamp\] Producer INFO total items 1 \[timestamp\] Consumer INFO
consumed 1 item \... (continues for 20 iterations each)

FILE 3 --- event_README.txt \# event.py - README

# What Does It Do This program demonstrates thread synchronization
using threading.Event. The Producer generates 5 random numbers and
appends them to a shared list, then sets the event. The Consumer waits
for the event to be set, then pops and logs the item.

# How To Run

python event.py

# Key Concepts Covered - threading.Event for signaling between
threads - event.set() to signal the consumer - event.clear() to reset
the signal - event.wait() to block until signaled - logging module for
output

# Advantages - Simple signaling mechanism between threads - Producer
controls when consumer can act - Easy to understand flow

# Disadvantages - Consumer runs in infinite loop with no exit
condition, program may hang after producer finishes - Only one consumer,
no scalability shown - No exception handling

# Expected Output

\[timestamp\] Producer INFO Producer notify: item \[number\] appended by
Thread-1 \[timestamp\] Consumer INFO Consumer notify: \[number\] popped
by Thread-2 \... (5 times)

FILE 4 --- mythreadclass_README.txt \# mythreadclass.py - README

# What Does It Do This program creates 9 threads using a custom thread
class called MyThreadClass. Each thread is given a name and a random
duration (1-10 seconds). All threads run concurrently, sleep for their
duration, then finish. Total execution time is printed at the end.

# How To Run

python mythreadclass.py

# Key Concepts Covered - Creating a custom Thread class by inheriting
from threading.Thread - Overriding the run() method - Running multiple
threads concurrently - Measuring total execution time - os.getpid() to
show process ID

# Advantages - Custom thread class is reusable and clean - Shows true
concurrent execution - Execution time shows benefit of multithreading

# Disadvantages - No shared data or synchronization demonstrated -
Random duration means output order is unpredictable - No error handling

# Expected Output

\-\--\> Thread#1 running, belonging to process ID \[pid\] \-\--\>
Thread#2 running, belonging to process ID \[pid\] \... (all 9 threads
start) \-\--\> Thread#3 over \... (threads finish in random order) End
\-\-- \[X\] seconds \-\--

FILE 5 --- mythreadclasslock_README.txt \# mythreadclasslock.py - README

# What Does It Do This program is the same as mythreadclass.py but
adds a threading.Lock. The lock is acquired at the start of each
thread\'s run() method and released at the end. This means only one
thread runs at a time, making execution serial despite using threads.

# How To Run

python mythreadclasslock.py

# Key Concepts Covered - threading.Lock to enforce mutual exclusion -
Lock.acquire() and Lock.release() - Difference between concurrent and
serial thread execution - How locks can accidentally serialize
multithreaded programs

# Advantages - Demonstrates what happens when a lock is held too
long - Good comparison against mythreadclass.py - Shows how to implement
a basic lock

# Disadvantages - Lock is held during sleep, so threads run one by one
(defeats multithreading) - Much slower than mythreadclass.py due to
serialization - No deadlock protection if exception occurs before
release

# Expected Output

\-\--\> Thread#1 running, belonging to process ID \[pid\] \-\--\>
Thread#1 over \-\--\> Thread#2 running, belonging to process ID \[pid\]
\-\--\> Thread#2 over \... (threads run one at a time) End \-\-- \[X\]
seconds \-\--

FILE 6 --- mythreadclasslock2_README.txt \# mythreadclasslock2.py -
README

# What Does It Do This is an improved version of mythreadclasslock.py.
The lock is acquired and released quickly (before sleep), so threads can
overlap during their sleep phase. This restores concurrency while still
protecting the critical print section.

# How To Run

python mythreadclasslock2.py

# Key Concepts Covered - Proper lock usage: acquire and release only
around critical section - Difference between mythreadclasslock.py and
this version - Concurrent execution restored by releasing lock before
sleep - Best practice for minimizing lock hold time

# Advantages - Faster than mythreadclasslock.py because lock is held
briefly - Shows correct way to use locks - Print section is still
protected from race conditions

# Disadvantages - Output order of \"over\" messages is still
unpredictable - No shared data is actually being protected here, lock is
mostly for print - No error handling

# Expected Output

\-\--\> Thread#1 running, belonging to process ID \[pid\] \-\--\>
Thread#2 running, belonging to process ID \[pid\] \... (all threads
start quickly) \-\--\> Thread#5 over \-\--\> Thread#2 over \... (finish
in random order) End \-\-- \[X\] seconds \-\--

FILE 7 --- rlock_README.txt \# rlock.py - README

# What Does It Do This program demonstrates threading.RLock (Reentrant
Lock) using a Box class. An adder thread adds a random number of items
to the box. A remover thread removes a random number of items. RLock
allows the same thread to acquire the lock multiple times without
deadlock.

# How To Run

python rlock.py

# Key Concepts Covered - threading.RLock vs regular Lock - Reentrant
locking (same thread can lock multiple times) - Box class as a shared
resource - Two threads modifying a shared value safely

# Advantages - RLock prevents deadlock when a locked method calls
another locked method - Clear real-world analogy (adding/removing items
from a box) - Safe concurrent access to shared data

# Disadvantages - No final total_items print to verify correctness -
Random item counts make output hard to predict - No timeout or stopping
condition if counts differ greatly

# Expected Output

N° \[x\] items to ADD N° \[y\] items to REMOVE ADDED one item \--\>
\[x-1\] item to ADD REMOVED one item \--\> \[y-1\] item to REMOVE \...
(continues until both finish)

FILE 8 --- semaphore_README.txt \# semaphore.py - README

# What Does It Do This program demonstrates threading.Semaphore for
thread synchronization. The Consumer waits (blocks) until the semaphore
is released. The Producer creates a random item, then releases the
semaphore. This runs 10 times in a loop.

# How To Run

python semaphore.py

# Key Concepts Covered - threading.Semaphore as a signaling
mechanism - semaphore.acquire() to block consumer - semaphore.release()
to signal consumer - Global variable shared between threads - Logging
for timestamped output

# Advantages - Clear example of semaphore usage - Guarantees consumer
always waits for producer - Simple and easy to follow

# Disadvantages - Uses a global variable (item) which is not ideal -
Semaphore initialized to 0, meaning consumer always blocks first - No
error handling or timeout

# Expected Output

\[timestamp\] Consumer INFO Consumer is waiting \[timestamp\] Producer
INFO Producer notify: item number \[x\] \[timestamp\] Consumer INFO
Consumer notify: item number \[x\] \... (10 times)

FILE 9 --- threaddefinition_README.txt \# threaddefinition.py - README

# What Does It Do This is the most basic threading example. It creates
10 threads, each calling my_func with a thread number. Threads are
started and joined one by one inside the loop.

# How To Run

python threaddefinition.py

# Key Concepts Covered - threading.Thread with target and args -
Starting threads with t.start() - Joining threads with t.join() - Basic
function-based threading

# Advantages - Simplest possible threading example - Good starting
point for beginners - Clear and readable code

# Disadvantages - t.join() is called inside the loop, so threads
actually run one by one (not concurrently) - No shared data or
synchronization - Very limited functionality

# Expected Output

my_func called by thread N°0 my_func called by thread N°1 my_func called
by thread N°2 \... (up to N°9)

FILE 10 --- threaddetermine_README.txt \# threaddetermine.py - README

# What Does It Do This program creates 3 named threads, each running a
different function (A, B, C). Each function prints its thread name,
sleeps for 2 seconds, then prints exit. All three threads run
concurrently.

# How To Run

python threaddetermine.py

# Key Concepts Covered - Naming threads using the name parameter -
threading.currentThread().getName() to get thread name - Concurrent
execution of 3 threads - time.sleep() to simulate work

# Advantages - Shows how to name threads for easier debugging - All
three functions run at the same time - Clean and readable structure

# Disadvantages - All threads sleep for same fixed duration (2
seconds), no variation - Functions A, B, C do the same thing, could be
one function - No shared data demonstrated

# Expected Output

function_A \--\> starting function_B \--\> starting function_C \--\>
starting function_A \--\> exiting function_B \--\> exiting function_C
\--\> exiting

FILE 11 --- threadnameandprocesses_README.txt \#
threadnameandprocesses.py - README

# What Does It Do This program creates 2 threads using a custom
MyThreadClass. Each thread simply prints the process ID it is running
under. It shows that threads share the same process ID.

# How To Run

python threadnameandprocesses.py

# Key Concepts Covered - Custom thread class - os.getpid() to retrieve
process ID - Showing that all threads belong to the same process - Basic
thread creation and joining

# Advantages - Clearly shows threads share a single process - Minimal
and easy to understand - Good for explaining threads vs processes
concept

# Disadvantages - Very limited functionality - os.getpid() line is
commented out so process ID is not actually shown - Only 2 threads, not
scalable demo

# Expected Output

ID of process running Thread#1 ID of process running Thread#2 End

FILE 12 --- threadingwithqueue_README.txt \# threadingwithqueue.py -
README

# What Does It Do This program demonstrates thread-safe communication
using Queue. One Producer thread generates 5 random numbers and puts
them in a queue. Three Consumer threads take items from the queue and
process them. Queue handles all synchronization automatically.

# How To Run

python threadingwithqueue.py

# Key Concepts Covered - queue.Queue for thread-safe data sharing -
Multiple consumers reading from one queue - queue.get() blocks until
item is available - queue.task_done() to signal item processing is
complete - Producer-Consumer pattern with Queue

# Advantages - Queue is thread-safe by default, no manual locking
needed - Multiple consumers increase throughput - Clean and scalable
design

# Disadvantages - Consumer runs in infinite loop with no exit
condition, program may hang - No queue size limit defined - t2, t3, t4
join() may never return due to infinite consumer loop

# Expected Output

Producer notify : item N°\[x\] appended to queue by Thread-1 Consumer
notify : \[x\] popped from queue by Thread-2 \... (5 items produced,
consumed by any of the 3 consumers)
