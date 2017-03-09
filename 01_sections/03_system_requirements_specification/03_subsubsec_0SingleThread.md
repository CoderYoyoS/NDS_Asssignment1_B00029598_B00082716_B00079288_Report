### Single-Threaded Approach

A single-threaded implementation can be easily constructed and it will serve its purpose up until the program needs to handle multiple clients. Because a thread is a single path of execution there is a consistent need to execute the program in a loop which can be expensive to performance, throughput and I/O. When implementing a single threaded server, a loop must be executed that constantly listens to incoming connection requests and also has the job of processing them. Below is pseudocode to demonstrate what happens when this design is implemented.      
\vspace*{\fill}   
`StartServerOnPortAndRunAThread()`   
&nbsp;&nbsp;`While(serverIsRunning)`   
&nbsp;&nbsp;&nbsp;&nbsp;`ListenForClients()`   
&nbsp;&nbsp;&nbsp;&nbsp;`if(AClientWantsToConnect())`   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`AcceptConnectionRequest()`   
&nbsp;&nbsp;&nbsp;&nbsp;`Then Try`   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`ProcessTheRequest()`   
&nbsp;&nbsp;`RepeatWhileServerIsRunning()`   
\vspace*{\fill}   
Accepting requests from clients and processing them on the same thread is generally considered a poor design methodology. If the thread is busy/blocked doing either operation, an error will most likely occur, potentially causing a system failure. In comparison, a multi-threaded server can listen for connections, accept them and hand off to another thread for processing the request.

