### Multi-Threaded Approach

As seen with the single-threaded design, when a server has to handle multiple clients and requests the system can become more susceptible to error and/or failure. Multi-threading the application provides a solution to this problem. As has been aforementioned, from a higher-level oversight, the program has two core operations that encompass its functionality, making a connection and processing the request. The single-threaded model handles both operations in one thread and the multi-threaded model handles both operations in thread independent to itself. See below pseudocode to demonstrate how this would work.   
\vspace*{\fill}   
```
StartServerOnPortAndRunAThread()   
    While(serverIsRunning)   
        ListenForClients() 
        if(AClientWantsToConnect()) 
            AcceptConnectionRequest()  
            //Let another thread do the work  
            CreateANewThreadToProcessTheRequest()   
            StartTheThread()
RepeatWhileServerIsRunning()   
```
\vspace*{\fill}   

The core benefit with this design is that if an expensive client request comes into the server, it can offload that task to a new thread and the server can quickly get back to listening out for new connections. In comparison to a single-threaded approach whereby if the thread is busy computing a request, any incoming connections will be denied because the thread is blocked or busy.

