```
FILE 6 --- CHAPTER 6
```

```
Celery
```

```
File 1 --- addTask.txt
```

```
# Chapter 5 - Celery Simple Task Execution (addTask.py)
```

## `## What Does It Do` 

```
This program demonstrates a basic Celery task that performs addition of two
numbers.
```

```
It defines a task `add(x, y)` which runs asynchronously using a message broker
(RabbitMQ).
```

## `## How To Run` 

```
Make sure Python 3, Celery, and a message broker (RabbitMQ) are installed.
```

```
Install Celery:
```

```
    pip install celery
```

```
Run RabbitMQ server locally.
```

```
Start Celery worker:
```

```
    celery -A addTask worker --loglevel=info
```

```
Run Python file or call task from Python shell:
    add.delay(4, 6)
```

```
## Key Concepts Covered
```

- `Celery task queue system` 

- `Asynchronous task execution` 

- `Message broker (AMQP / RabbitMQ)` 

- `Task decorator (@app.task)` 

- `Distributed computing basics` 

- `Producer-consumer architecture` 

## `## Advantages` 

- `Supports distributed task execution` 

- `Asynchronous processing improves performance` 

- `Scalable architecture for large systems` 

- `Decouples task execution from main application` 

## `## Disadvantages` 

- `Requires external broker setup (RabbitMQ/Redis)` 

- `More complex configuration` 

- `Debugging is harder than normal Python code` 

- `Overhead for small tasks` 

```
## Expected Output
```

## `Result of add(4, 6) = 10` 

## `## Output Explanation` 

- `Task `add` is registered with Celery` 

- `When called with `.delay()`, it is sent to message broker` 

- `Celery worker processes the task asynchronously` 

- `Result is returned after execution` 

## `## Notes` 

- `Broker URL: amqp://guest@localhost//` 

- `Celery worker must be running before executing tasks` 

- `This is a distributed task queue system, not just local execution` 

```
File 2 --- addTask_main.txt
```

```
# Chapter 5 - Running Celery Task (addTask.py execution)
```

```
## What Does It Do
```

```
This program demonstrates how to execute a Celery asynchronous task defined in
another file (`addTask.py`).
It calls the `add` task using `.delay()` which sends the task to the Celery
worker for background processing.
```

```
## How To Run
Make sure:
```

- `Celery is installed` 

```
- RabbitMQ (or another broker) is running
```

```
- Celery worker is active
```

```
Steps:
```

`1. Start RabbitMQ server` 

`2. Start Celery worker: celery -A addTask worker --loglevel=info` 

```
3. Run this script:
    python filename.py
```

```
## Key Concepts Covered
```

```
- Importing Celery tasks from another module
```

```
- Asynchronous task execution using .delay()
```

- `Message queue system` 

- `Producer-consumer model` 

- `Task delegation to worker process` 

```
## Advantages
```

```
- Non-blocking execution of tasks
```

```
- Improves application performance
```

```
- Scalable background processing
```

- `Clean separation of task definition and execution` 

## `## Disadvantages` 

- `Requires running Celery worker separately` 

```
- Depends on external broker (RabbitMQ/Redis)
```

```
- No immediate visible output unless result backend is configured
```

- `Debugging async tasks is harder` 

## `## Expected Output` 

```
(No direct output in terminal unless result is printed or logged)
```

```
OR if result is accessed:
```

```
AsyncResult object returned:
<AsyncResult: task-id>
```

## `## Output Explanation` 

```
- `addTask.add.delay(5,5)` sends task to Celery queue
```

```
- Worker picks up task and executes it in background
```

- `Result is stored in backend (if configured)` 

- `Script itself does not block or print result automatically` 

## `## Notes` 

- `This script only triggers the task` 

- `Actual execution happens in Celery worker` 

- ``.delay()` is non-blocking call` 

```
Pyro 4
```

```
first Example
```

```
File 1 --- pyro_client.txt
```

```
# Chapter 6 - Pyro4 Remote Procedure Call (RPC) Client
```

## `## What Does It Do` 

```
This program demonstrates a simple client using Pyro4 (Python Remote Objects).
It connects to a remote server object using a name server and calls a remote
method `welcomeMessage()`.
```

```
The user enters their name, and the server returns a personalized message.
```

## `## How To Run` 

```
Make sure Pyro4 is installed:
```

```
    pip install Pyro4
```

```
You must also have:
```

- `Pyro4 name server running` 

- `Pyro4 server script running and registered as "server"` 

```
Steps:
```

`1. Start name server:` 

```
    python -m Pyro4.naming
```

`2. Start server (separate script)` 

`3. Run this client:` 

```
    python filename.py
```

## `## Key Concepts Covered` 

- `Remote Procedure Call (RPC)` 

- `Pyro4 Proxy object` 

- `Name server lookup (PYRONAME)` 

- `Client-server architecture` 

- `Distributed systems communication` 

- `Remote method invocation` 

## `## Advantages` 

- `Enables distributed computing easily` 

- `Transparent remote function calls` 

- `Easy to integrate client-server systems` 

- `Useful for network-based applications` 

## `## Disadvantages` 

- `Requires running multiple services (server + name server)` 

- `Network dependency can cause delays` 

- `Harder debugging compared to local code` 

- `Security concerns if not configured properly` 

## `## Expected Output` 

```
What is your name? Ali
Hello Ali, welcome to the server
```

## `## Output Explanation` 

- `Client asks user for input name` 

- `Pyro4 proxy connects to remote server object` 

- ``welcomeMessage(name)` is executed on server` 

- `Response is returned and printed locally` 

```
## Notes
```

- `"PYRONAME:server" must match registered server name` 

- `Server must be running before client execution` 

- `This is a basic RPC example using Pyro4` 

```
File 2 --- pyro_server.txt
```

```
# Chapter 6 - Pyro4 RPC Server (Remote Object Server)
```

## `## What Does It Do` 

```
This program creates a Pyro4 server that exposes a remote object method
`welcomeMessage`.
```

```
Clients can connect to this server over the network and call the method as if it
were local.
```

```
The server registers itself with a Pyro Name Server under the name "server".
```

## `## How To Run` 

```
Make sure Pyro4 is installed:
```

```
    pip install Pyro4
```

```
You must run in this order:
```

`1. Start Pyro Name Server: python -m Pyro4.naming` 

`2. Start this server script: python filename.py` 

`3. Then run the client script.` 

## `## Key Concepts Covered` 

- `Remote Procedure Call (RPC)` 

- `Pyro4 Daemon` 

- `Name server registration` 

- `Object exposure using @Pyro4.expose` 

- `Distributed system architecture` 

- `Server-side event loop (requestLoop)` 

## `## Advantages` 

- `Enables remote method invocation easily` 

- `Supports distributed applications` 

- `Transparent communication between client and server` 

- `Scalable architecture for network systems` 

## `## Disadvantages` 

- `Requires multiple running services` 

- `Network dependency introduces latency` 

- `More complex setup than local programs` 

- `Security risks if exposed publicly` 

## `## Expected Output` 

## `Ready. Object uri = PYRO:xxxxxxxxxxxxxxxxx` 

```
(Server stays running and waits for requests)
```

## `## Output Explanation` 

- `Server object is created and exposed via Pyro4` 

- `Daemon registers the object` 

- `Name server maps "server" → object URI` 

- `requestLoop() keeps server running` 

- `Client can now call welcomeMessage remotely` 

## `## Notes` 

- `Name server must be running before starting this server` 

- `Client uses "PYRONAME:server" to access this object` 

- `This is a basic RPC server implementation using Pyro4` 

## `Second Example` 

```
File 1 --- chainTopology.txt
```

## `# Chapter 6 - Pyro4 Chain Topology (Distributed Object Chaining)` 

## `## What Does It Do` 

```
This program demonstrates a chain-based distributed system using Pyro4.
Multiple server objects are connected in a logical chain. Each object forwards a
message to the next server until the message returns to the starting node,
forming a loop.
```

```
It simulates how distributed systems can pass data across multiple nodes.
```

## `## How To Run` 

```
Make sure Pyro4 is installed:
```

```
    pip install Pyro4
```

```
You also need:
```

- `Pyro Name Server running` 

- `Multiple chain server instances running (each with different names)` 

```
Typical setup:
```

`1. Start name server:` 

```
    python -m Pyro4.naming
```

`2. Start multiple chain servers (different names)` 

`3. Run a client that calls `process()`` 

```
## Key Concepts Covered
```

- `Distributed object chaining` 

- `Pyro4 remote object communication` 

- `Recursive message passing` 

- `Name server lookup (PYRONAME)` 

- `Network-based object references` 

- `Topology-based distributed systems` 

## `## Advantages` 

- `Demonstrates real distributed system behavior` 

- `Useful for learning networked object communication` 

- `Shows message routing across multiple nodes` 

- `Flexible architecture for chain-based processing` 

## `## Disadvantages` 

- `Complex setup with multiple servers required` 

- `Debugging distributed flow is difficult` 

- `Network dependency may cause delays` 

- `Risk of infinite loops if logic is incorrect` 

## `## Expected Output` 

```
Server A forwarding the message to the object B
Server B forwarding the message to the object C
Back at Server A; the chain is closed!
```

```
## Output Explanation
```

- `Each server receives a message` 

```
- If current server name is already in message list, chain stops
```

- `Otherwise, message is appended and forwarded to next server` 

- `Final server returns completed chain back to origin` 

## `## Notes` 

- `Each node must be registered in Pyro name server` 

- `PYRONAME must match server registration names` 

- `This simulates distributed chain topology` 

- `Useful for understanding routing in distributed systems` 

```
File 2 --- client_chain.txt
```

## `# Chapter 6 - Pyro4 Chain Topology Client` 

## `## What Does It Do` 

```
This program acts as a client for the Pyro4 chain topology system.
It connects to the first node in a distributed chain and sends a message list.
The message is processed across multiple remote server objects and returns back
after completing the chain.
```

## `## How To Run` 

```
Make sure Pyro4 is installed:
```

```
    pip install Pyro4
```

```
You must also have:
```

- `Pyro Name Server running` 

- `Chain servers already started (example.chainTopology.*)` 

```
Steps:
```

## `1. Start name server:` 

```
    python -m Pyro4.naming
```

`2. Start chain servers (multiple nodes)` 

`3. Run this client:` 

```
    python filename.py
```

```
## Key Concepts Covered
```

- `Pyro4 remote object proxy` 

- `Distributed chain communication` 

- `Message passing in network topology` 

- `Remote method invocation (RMI)` 

- `PYRONAME lookup system` 

- `Multi-node distributed execution` 

## `## Advantages` 

- `Demonstrates full distributed workflow` 

- `Shows real-world message routing concept` 

- `Easy client-side interaction with remote system` 

- `Useful for understanding distributed architectures` 

## `## Disadvantages` 

- `Requires multiple running server nodes` 

- `Complex setup compared to local programs` 

- `Debugging across nodes is difficult` 

- `Network dependency can cause delays or failures` 

## `## Expected Output` 

```
Server 1 forwarding the message to next node
Server 2 forwarding the message to next node
Back at Server 1; the chain is closed!
```

```
Result = ['passed on from Server 1', 'passed on from Server 2', 'complete at
Server 1']
```

## `## Output Explanation` 

- `Client sends initial message ["hello"]` 

- `Message travels through chain of servers` 

- `Each server appends its name and forwards it` 

- `When message returns to starting node, chain stops` 

- `Final result is printed by client` 

## `## Notes` 

- `PYRONAME:example.chainTopology.1 must exist in name server` 

- `All chain nodes must be running before execution` 

- `This is a distributed topology simulation using RPC` 

```
File 3 --- server_chain_1.txt
```

```
# Chapter 6 - Pyro4 Chain Topology Server Node
```

## `## What Does It Do` 

```
This program creates a single node (server) in a Pyro4-based chain topology
system.
```

```
Each server node registers itself with the Pyro Name Server and becomes part of
a distributed chain.
```

```
This specific script represents one node (e.g., server "1") which forwards
messages to the next server in the chain.
```

## `## How To Run` 

```
Make sure Pyro4 is installed:
```

```
    pip install Pyro4
```

```
You must also have:
```

- `Pyro Name Server running` 

- `Other chain nodes running (like server 2, 3, etc.)` 

```
Steps:
```

`1. Start Pyro Name Server: python -m Pyro4.naming` 

`2. Start this server:` 

```
    python filename.py
```

`3. Start other chain servers with different IDs` 

```
## Key Concepts Covered
```

- `Pyro4 Daemon` 

- `Remote object registration` 

- `Name server binding (PYRONAME)` 

- `Distributed chain topology` 

- `Object-oriented RPC` 

- `Server event loop (requestLoop)` 

```
## Advantages
```

- `Enables distributed node-based architecture` 

- `Each server acts independently` 

- `Scalable chain system design` 

- `Useful for learning distributed computing` 

## `## Disadvantages` 

- `Requires multiple servers running simultaneously` 

- `Complex configuration and setup` 

- `Debugging across nodes is difficult` 

- `Network dependency increases failure risk` 

```
## Expected Output
```

```
server_1 started
```

```
(Server remains running and waiting for requests)
```

## `## Output Explanation` 

```
- A Chain object is created for current node
```

- `Pyro Daemon registers the object - Name server maps: example.chainTopology.1 → this server - requestLoop() keeps server active to handle requests` 

## `## Notes` 

- `current_server and next_server define chain flow` 

- `Each node must be registered separately` 

- `All nodes together form a distributed chain system` 

```
File 4 --- server_chain_2.txt
```

## `# Chapter 6 - Pyro4 Chain Topology Server Node (Server 2)` 

## `## What Does It Do` 

```
This program creates another node (server 2) in a Pyro4 chain topology system.
It works exactly like server 1, but it forwards messages to the next node
(server 3).
Together with other servers, it forms a distributed chain network.
```

## `## How To Run` 

```
Make sure Pyro4 is installed:
```

```
    pip install Pyro4
```

```
You must also run:
```

```
- Pyro Name Server
```

```
- Other chain nodes (server 1, server 3, etc.)
```

```
Steps:
```

`1. Start Pyro Name Server: python -m Pyro4.naming` 

`2. Start server 1` 

`3. Start this server (server 2)` 

`4. Start server 3 (and others if needed)` 

```
Run:
```

```
    python filename.py
```

```
## Key Concepts Covered
```

- `Pyro4 distributed objects` 

- `Chain topology communication` 

- `Name server registration (PYRONAME)` 

- `Daemon-based server execution` 

- `Remote object forwarding` 

- `Multi-node architecture` 

```
## Advantages
```

- `Enables scalable distributed systems` 

- `Each node works independently` 

- `Easy to extend chain by adding more servers` 

- `Useful for learning network routing concepts` 

```
## Disadvantages
```

- `Requires multiple running servers` 

- `Complex setup and coordination` 

- `Hard to debug multi-node flow` 

- `Network dependency increases failure points` 

```
## Expected Output
```

```
server_2 started
```

```
(Server stays active waiting for requests)
```

```
## Output Explanation
```

```
- A Chain object is created for server 2
- It registers itself as:
  example.chainTopology.2
```

- `It connects to Pyro Name Server` 

- `requestLoop() keeps server running continuously` 

- `It waits for messages from previous node` 

```
## Notes
```

- `current_server = "2"` 

- `next_server = "3"` 

- `This is one part of a distributed chain system` 

```
File 5 --- server_chain_3.txt
```

## `# Chapter 6 - Pyro4 Chain Topology Server Node (Server 3)` 

```
## What Does It Do
```

```
This program creates the third node in a Pyro4 chain topology system.
It registers itself with the Pyro Name Server and connects back to server 1,
forming a circular chain (loop).
```

```
This allows messages to circulate through all nodes until they return to the
starting point.
```

```
## How To Run
```

```
Make sure Pyro4 is installed:
```

```
    pip install Pyro4
```

```
You must run:
```

- `Pyro Name Server` 

- `Server 1` 

- `Server 2` 

- `Server 3 (this file)` 

```
Steps:
```

`1. Start Pyro Name Server: python -m Pyro4.naming` 

```
2. Start all server nodes:
```

```
   - server 1
```

```
   - server 2
   - server 3
```

```
3. Run this script:
    python filename.py
```

```
## Key Concepts Covered
- Pyro4 distributed objects
- Circular chain topology
- Remote object registration
- Name server (PYRONAME)
- Daemon-based server execution
- Distributed loop communication
```

```
## Advantages
- Demonstrates circular distributed architecture
- Easy to expand by adding more nodes
- Useful for learning network loops
- Supports scalable RPC systems
```

```
## Disadvantages
- Requires multiple servers running together
- Complex debugging in loop systems
- Risk of infinite loops if logic is incorrect
- High dependency on network stability
```

```
## Expected Output
```

```
server_3 started
```

```
(Server stays running and waits for requests)
```

```
## Output Explanation
- Server 3 registers as:
  example.chainTopology.3
- It forwards messages to server 1 (creating a loop)
- Part of circular chain topology system
- requestLoop() keeps server active indefinitely
```

```
## Notes
- current_server = "3"
- next_server = "1"
- This completes a circular chain (1 → 2 → 3 → 1)
```

```
Socket
```

```
File 1 --- addTask.txt
```

```
# Chapter 5 - Celery Task Definition (tasks.py)
```

```
## What Does It Do
This program defines a simple Celery task that performs addition of two numbers.
The task is registered with Celery and executed asynchronously using a message
broker (RabbitMQ).
```

```
## How To Run
Make sure Python 3, Celery, and RabbitMQ are installed.
```

```
Install Celery:
    pip install celery
```

```
Start RabbitMQ server.
```

```
Start Celery worker:
    celery -A tasks worker --loglevel=info
```

```
You can test the task in Python shell:
    from tasks import add
    add.delay(2, 3)
```

## `## Key Concepts Covered` 

- `Celery application setup` 

- `Task definition using @app.task` 

- `Asynchronous execution` 

```
- Message broker (AMQP / RabbitMQ)
```

- `Distributed task queue system` 

- `Producer-consumer model` 

## `## Advantages` 

- `Non-blocking task execution` 

- `Scalable background processing` 

- `Useful for web applications and APIs` 

- `Separates task logic from main program` 

## `## Disadvantages` 

- `Requires external broker setup` 

- `More configuration overhead` 

- `Harder debugging than normal functions` 

- `Not suitable for very small projects` 

## `## Expected Output` 

```
Result (if accessed):
5
```

```
Or worker logs:
```

```
[INFO] Received task tasks.add
```

```
[INFO] Task completed successfully
```

## `## Output Explanation` 

- `Function `add` is registered as a Celery task` 

- ``.delay()` sends task to message broker` 

- `Worker picks task and executes it asynchronously` 

- `Result is returned via backend (if configured)` 

## `## Notes` 

- `Broker used: pyamqp://guest@localhost//` 

- `Celery worker must be running before calling tasks` 

- `This is a basic distributed task queue example` 

```
File 2 --- addTask_main.txt
```

```
# Chapter 5 - Running Celery Task (addTask usage)
```

## `## What Does It Do` 

```
This program triggers a Celery asynchronous task defined in another file
(`addTask.py` or `tasks.py`).
It calls the `add` function using `.delay()`, which sends the task to a
background worker via the message broker.
```

```
## How To Run
Make sure:
- Celery is installed
```

```
- RabbitMQ (or another broker) is running
```

- `Celery worker is active` 

```
Steps:
```

`1. Start RabbitMQ server` 

`2. Start Celery worker: celery -A addTask worker --loglevel=info` 

`3. Run this script: python filename.py` 

```
## Key Concepts Covered
```

```
- Importing Celery tasks from another module
```

```
- Asynchronous task execution
```

```
- .delay() method usage
```

```
- Message queue communication
```

```
- Producer-consumer architecture
```

- `Background processing` 

## `## Advantages` 

```
- Non-blocking execution
```

```
- Improves application performance
```

- `Scalable task handling` 

```
- Clean separation of logic and execution
```

## `## Disadvantages` 

- `Requires running Celery worker separately` 

- `Depends on external broker setup` 

- `No immediate output in script` 

- `Harder debugging for async flow` 

```
## Expected Output
```

```
(No direct output in terminal)
```

```
OR worker logs:
[INFO] Task add received
```

```
[INFO] Task completed successfully
```

```
## Output Explanation
```

```
- `add.delay(5, 5)` sends task to queue
```

```
- Celery worker processes task in background
```

- `Result is stored in backend (if configured)` 

- `Script itself does not print result` 

## `## Notes` 

```
- This script only triggers task execution
```

- `Actual computation happens in worker process` 

- `Must ensure task module name matches worker command` 

```
File 3 --- client.txt
```

```
# Chapter 7 - Socket Programming (Client Side)
```

## `## What Does It Do` 

```
This program is a simple TCP client using Python's `socket` module.
It connects to a server running on the same machine (localhost) at port 9999,
receives data (time), and prints it.
```

```
## How To Run
```

```
Make sure Python 3 is installed.
```

```
You must also have a server program running on port 9999 before running this
client.
```

```
Steps:
```

`1. Start the server (server.py must be running first)` 

`2. Run this client:` 

```
    python client.py
```

```
## Key Concepts Covered
```

```
- Socket programming in Python
```

```
- TCP/IP client-server model
```

```
- socket.socket() creation
- Connecting to server using hostname and port
- Receiving data using recv()
```

```
- Decoding byte data to string
```

```
## Advantages
```

```
- Simple client-server communication model
```

```
- Useful for learning network programming
- Lightweight and fast communication
```

```
- Real-world networking concept
```

```
## Disadvantages
```

```
- Requires server to be running first
```

```
- No error handling included
- Fixed buffer size (1024 bytes)
```

```
- Not secure (no encryption)
```

## `## Expected Output` 

```
Time connection server: 12:45:30
```

```
## Output Explanation
```

```
- Client creates a TCP socket
```

```
- Connects to server at (host, 9999)
```

```
- Receives time data from server
```

```
- Converts bytes to string using decode('ascii')
```

```
- Prints received server time
```

## `## Notes` 

```
- Server must send data before client calls recv()
- host = socket.gethostname() means local machine
- Port 9999 must match server configuration
```

```
File 4 --- client2.txt
```

```
# Chapter 7 - Socket Programming (File Receiving Client)
```

```
## What Does It Do
This program is a TCP client that connects to a server on port 60000.
It sends a message to the server ("HelloServer!") and then receives a file from
the server in chunks.
The received data is saved into a local file named `received.txt`.
```

```
## How To Run
Make sure Python 3 is installed.
```

```
You must run the server program first (which sends file data on port 60000).
```

```
Steps:
```

`1. Start server script (server must be running on port 60000)` 

`2. Run this client:` 

```
    python client.py
```

```
## Key Concepts Covered
```

- `Socket programming in Python` 

- `TCP client-server communication` 

- `Sending data using send()` 

- `Receiving data in chunks using recv()` 

```
- File handling in binary mode ('wb')
```

- `Streaming file transfer over network` 

## `## Advantages` 

```
- Efficient way to transfer files over network
```

```
- Handles large data using chunks (1024 bytes)
```

```
- Simple TCP communication model
```

```
- Saves received data directly to file
```

```
## Disadvantages
```

```
- No encryption (insecure transfer)
```

```
- No error handling for connection failure
```

```
- Depends fully on server availability
```

- `Fixed buffer size for receiving data` 

```
## Expected Output
```

```
file opened
receiving data...
Data=> <file content chunk>
receiving data...
Data=> <file content chunk>
Successfully get the file
connection closed
```

```
## Output Explanation
```

```
- Client connects to server at (host, 60000)
```

```
- Sends "HelloServer!" message
```

```
- Receives file data in chunks
```

```
- Writes each chunk into received.txt
```

```
- Stops when server closes connection
```

## `## Notes` 

```
- File is saved in binary mode (wb)
```

```
- recv(1024) reads data in 1KB chunks
```

```
- Loop ends when no more data is received
```

```
File 5 --- server.txt
```

```
# Chapter 7 - Socket Programming (Time Server)
```

```
## What Does It Do
This program creates a simple TCP server using Python sockets.
It listens on port 9999 and sends the current system time to any client that
connects.
```

```
Each client connection is handled one at a time in an infinite loop.
```

```
## How To Run
Make sure Python 3 is installed.
```

```
Steps:
```

`1. Run this server first: python server.py` 

`2. Then run the client program that connects to port 9999.` 

```
## Key Concepts Covered
```

```
- Socket programming in Python
```

```
- TCP server creation
```

```
- bind(), listen(), accept()
- Client-server connection handling
```

- `Sending data over network` 

- `System time retrieval using time.ctime()` 

## `## Advantages` 

```
- Simple server implementation
```

```
- Good for learning network fundamentals
```

```
- Real-time data sharing example
- Handles multiple sequential client connections
```

```
## Disadvantages
```

```
- Single-threaded (handles one client at a time)
```

```
- No error handling
- No security or encryption
- No concurrency support
```

```
## Expected Output (Server Side)
```

```
Connected with ('127.0.0.1', 54321)
Connected with ('127.0.0.1', 54322)
```

## `## Expected Output (Client Side)` 

```
Time connection server: Tue Jun 6 03:10:15 2026
```

```
## Output Explanation
```

- `Server binds to hostname and port 9999` 

- `Waits for client connections using listen()` 

```
- accept() returns client socket and address
```

- `Server sends current time using send()` 

- `Client receives and displays time` 

## `## Notes` 

```
- serversocket.listen(5) allows up to 5 queued connections
```

```
- This is a blocking server (no threading used)
```

- `Each connection is closed after sending data` 

```
File 6 --- server2.txt
```

```
# Chapter 7 - Socket Programming (File Sending Server)
```

```
## What Does It Do
This program creates a TCP server that listens on port 60000.
When a client connects, it receives a message from the client, then sends a file
(`mytext.txt`) in chunks to the client over the network.
```

```
After sending the file, it sends a closing message and terminates the
connection.
```

```
## How To Run
Make sure Python 3 is installed.
```

```
Steps:
```

`1. Create a file named `mytext.txt` in the same directory` 

`2. Run this server first: python server.py` 

`3. Then run the corresponding client program` 

## `## Key Concepts Covered` 

- `Socket programming (TCP server)` 

- `File handling in binary mode ('rb')` 

- `Sending data over socket using send()` 

- `Receiving client requests using recv()` 

- `Chunk-based file transfer` 

- `Client-server communication` 

## `## Advantages` 

- `Efficient file transfer using chunks (1024 bytes)` 

- `Simple TCP-based communication` 

- `Demonstrates real-world server behavior` 

- `Supports multiple client connections (sequential)` 

## `## Disadvantages` 

- `No concurrency (one client at a time)` 

- `No error handling` 

- `No encryption or security` 

- `File is assumed to exist (no validation)` 

```
## Expected Output (Server Side)
```

```
Server listening....
Got connection from ('127.0.0.1', 54321)
Server received 'HelloServer!'
Sent b'file content...'
Donesending
```

```
## Expected Output (Client Side)
```

```
receiving data...
Data=> <file content>
Successfully get the file
connection closed
```

## `## Output Explanation` 

```
- Server listens on port 60000
```

- `Client connects and sends a request message` 

```
- Server opens `mytext.txt` in binary mode
```

```
- File is sent in 1024-byte chunks
```

```
- After file transfer, server sends thank you message
- Connection is closed
```

## `## Notes` 

- `File must exist before running server` 

- `Each client gets file independently` 

```
- f.close() should ideally be outside loop (minor bug in original code)
```

