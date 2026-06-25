FILE 1 --- classes_README.txt \# classes.py - README

# What Does It Do This program demonstrates Object-Oriented
Programming (OOP) in Python. It creates two classes: MyClass and
AnotherClass (which inherits from MyClass). It shows how class variables
and instance variables behave differently, and how inheritance works.

# How To Run Make sure Python 3 is installed. Then run:

python classes.py

# Key Concepts Covered - Class variables shared across all instances -
Instance variables specific to each object - Variable shadowing
(instance overrides class variable) - Inheritance using
AnotherClass(MyClass) - Dynamic attribute assignment at runtime

# Advantages - Shows real-world OOP behavior clearly - Demonstrates
variable shadowing which is a common source of bugs - Inheritance
example is simple and easy to understand

# Disadvantages - No input from user, everything is hardcoded - No
error handling - Does not use constructors with arguments in MyClass

# Expected Output

instance.myfunction(1, 2) 3 instance.common 10 instance2.common 10
instance.common 30 instance2.common 30 instance.common 10
instance2.common 30 instance.common 10 instance2.common 50 hello
instance.myfunction (1, 2) 3 instance.test 10

FILE 2 --- dir_README.txt

 dir.py - README

# What Does It Do This program does two things: 1. Checks whether a
number is positive, negative, or zero using if/elif/else. 2. Calculates
the sum of all numbers in a list using a for loop.

# How To Run

python dir.py

# Key Concepts Covered - if / elif / else conditional statements - for
loop iteration over a list - Accumulator pattern (sum variable)

# Advantages - Very beginner-friendly code - Clearly shows basic
control flow in Python - Easy to modify the number or list

# Disadvantages - All values are hardcoded - No user input - No
function is defined, everything runs at top level

# Expected Output

Positive number The sum is 83

FILE 3 --- dosomething_README.txt \# dosomething.py - README

# What Does It Do This file defines a single helper function called
do_something. It fills a given list with random float numbers. The count
parameter decides how many random numbers to generate. This function is
used by multiprocessingtest.py, multithreadingtest.py, and
serialtest.py.

# How To Run This file is not meant to run on its own. It is imported
by other scripts:

from do_something import \*

# Key Concepts Covered - Defining reusable functions - Using the
random module - Appending to a list inside a loop - Passing list by
reference in Python

# Advantages - Clean and reusable function - Works well as a shared
module across multiple test files - Simple to understand

# Disadvantages - No return value, modifies list in place which can be
confusing - No input validation (e.g. negative count would cause no
error) - Only generates floats, not configurable

# Expected Output No direct output. Used as a module.

FILE 4 --- flie_README.txt \# flie.py - README

# What Does It Do This program demonstrates basic file handling in
Python. It creates a file called test.txt, writes two lines into it,
closes it, then reopens it and reads the full content and prints it.

# How To Run

python flie.py

Note: This will create a file named test.txt in the same folder.

# Key Concepts Covered - Opening a file in write mode using open() -
Writing lines to a file using f.write() - Closing a file using
f.close() - Reading full file content using f.read()

# Advantages - Simple and clear demonstration of file I/O - Shows both
reading and writing in one script - Easy to modify for other file
operations

# Disadvantages - File name is hardcoded - No error handling (e.g. if
file cannot be created) - Does not use \"with open()\" which is the
recommended modern approach - Typo in filename (flie instead of file)

# Expected Output

first line of file second line of file

FILE 5 --- flow_README.txt \# flow.py - README

# What Does It Do This program demonstrates three types of control
flow in Python: 1. if/elif/else - checks if a number is positive,
negative, or zero 2. for loop - calculates sum of a list of numbers 3.
while loop - calculates sum of natural numbers from 1 to n (n=10)

# How To Run

python flow.py

# Key Concepts Covered - Conditional statements (if / elif / else) -
for loop with a list - while loop with a counter - Accumulator pattern

# Advantages - Covers three major control flow structures in one
file - Easy to read and well-commented - Good reference for beginners

# Disadvantages - All values are hardcoded - No functions used,
everything is at top level - No user interaction

# Expected Output

Positive number The sum is 83 The sum is 55

FILE 6 --- lists_README.txt \# lists.py - README

# What Does It Do This program demonstrates Python\'s main data
structures: - Lists (ordered, mutable) - Dictionaries (key-value
pairs) - Tuples (ordered, immutable) It also shows how to index, modify,
and use built-in functions on these structures.

# How To Run

python lists.py

# Key Concepts Covered - Creating and modifying lists - Negative
indexing in lists - Creating and updating dictionaries - Tuples and
their immutability - Assigning built-in functions to variables (myfunc =
len)

# Advantages - Covers three important data structures in one file -
Shows negative indexing which is unique to Python - Demonstrates that
functions can be stored in variables

# Disadvantages - No user input - Some lines like \"example\" and
\"mylist\" just evaluate the value but print nothing - No error handling

# Expected Output

yet element 1 3.15 {\'Key 1\': \'value 1\', 2: 3, \'pi\': 3.14} 3.15 (1,
2, 3) 3

FILE 7 --- multiprocessingtest_README.txt \# multiprocessingtest.py -
README

# What Does It Do This program tests Python multiprocessing
performance. It spawns 10 separate processes, each generating 10 million
random numbers. It measures how long the entire operation takes using
time module.

# How To Run Make sure dosomething.py is in the same folder. Then run:

python multiprocessingtest.py

# Key Concepts Covered - multiprocessing.Process to create separate
processes - Parallel execution using multiple CPU cores - Measuring
execution time with time.time() - Using if \_\_name\_\_ ==
\"\_\_main\_\_\" guard

# Advantages - True parallelism using multiple CPU cores - Bypasses
Python\'s GIL (Global Interpreter Lock) - Best choice for CPU-heavy
tasks

# Disadvantages - Each process has its own memory, so out_list is not
shared between processes - More overhead to start compared to threads -
Output list data is lost after process ends (not returned)

# Expected Output

List processing complete. multiprocesses time= \[some float value in
seconds\]

FILE 8 --- multithreadingtest_README.txt \# multithreadingtest.py -
README

# What Does It Do This program tests Python multithreading
performance. It creates 10 threads, each supposed to generate 10 million
random numbers. It measures total execution time.

# How To Run Make sure dosomething.py is in the same folder. Then run:

python multithreadingtest.py

# Key Concepts Covered - threading.Thread to create threads - Shared
memory between threads - Measuring execution time - Using if
\_\_name\_\_ == \"\_\_main\_\_\" guard

# Advantages - Threads share memory, easier to pass data - Lower
overhead than processes to start - Useful for I/O-bound tasks

# Disadvantages - Python\'s GIL prevents true parallel execution for
CPU-bound tasks - Bug in code: do_something(size, out_list) is called
directly instead of passing as target, so threads run serially - Slower
than multiprocessing for CPU-heavy work

# Expected Output

List processing complete. multithreading time= \[some float value in
seconds\]

FILE 9 --- serialtest_README.txt \# serialtest.py - README

# What Does It Do This program runs do_something function 10 times one
after another (serially). Each run generates 10 million random numbers.
It measures total time taken to complete all runs.

# How To Run Make sure dosomething.py is in the same folder. Then run:

python serialtest.py

# Key Concepts Covered - Serial (sequential) execution - Performance
benchmarking using time module - Importing from another module - for
loop repetition

# Advantages - Simple and predictable execution order - Easy to debug
since everything runs one by one - Good baseline to compare against
threading and multiprocessing

# Disadvantages - Slowest approach for large tasks - Does not use any
parallelism - No performance optimization

# Expected Output

List processing complete. serial time= \[some float value in seconds\]

FILE 10 --- threadandprocesses_README.txt \# threadandprocesses.py -
README

# What Does It Do This program compares multithreading and
multiprocessing in a single file. It runs do_something using 10 threads
first, then using 10 processes. Both results are timed separately so you
can compare their performance. There is also a commented-out serial
version for reference.

# How To Run

python threadandprocesses.py

# Key Concepts Covered - Side-by-side comparison of threading vs
multiprocessing - Shared memory in threads vs separate memory in
processes - Measuring and printing execution time for each approach -
Using NUM_WORKERS constant for easy configuration

# Advantages - All three approaches (serial, threading,
multiprocessing) in one file - Easy to compare performance results
directly - Good for learning which approach is better for which task

# Disadvantages - Same threading bug as multithreadingtest.py
(function called directly, not passed as target) - Serial section is
commented out so it does not run by default - out_list is shared across
all iterations which can cause data mixing

# Expected Output

List processing complete. threading time= \[some float value in
seconds\] List processing complete. processes time= \[some float value
in seconds\]
