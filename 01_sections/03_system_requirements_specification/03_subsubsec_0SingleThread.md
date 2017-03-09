### Single-Threaded Approach

A single-threaded implementation can be easily constructed and it will serve it's purpose up until the program needs to handle multiple clients. Because a thread is a single path of execution there is a consistent need to execute the program in a loop which can be expensive to performance, throughput and I/O. So when implementing a single threaded server, a loop has to be executed that constantly listens to incoming connection requests and also has the job of processing them. Below is pseudocode to demonstrate what happens when this design is implemented.       
\vspace*{\fill}   
```
StartServerOnPortAndRunAThread()
While(serverIsRunning)  
        ListenForClients() 
        if(AClientWantsToConnect())   
            AcceptConnectionRequest()
        Then Try  
            ProcessTheRequest()  
    RepeatWhileServerIsRunning()
```   
\vspace*{\fill}   

Accepting requests from clients and processing them on the same thread is generally considered a poor design methodology. If the thread is busy/blocked doing either operation, an error will most likely occur, potentially causing a system failure. In comparison, a multi-threaded server can listen for connections, accept them and hand off to another thread for processing the request.

