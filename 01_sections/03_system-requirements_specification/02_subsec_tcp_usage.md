## TCP Protocol Using Java

In order to implement the TCP protocol server using Java code five steps are taken. Firstly, the server
is instantiated using ```ServerSocket``` and is bound to a specific port. 
```
        ServerSocket serverSocket = new ServerSocket(port);
```
Secondly, The server invokes the accept method and is constantly waiting until the
a client has made a connection on the given port. 
```
        while(true){
            Socket socket = serverSocket.accept();

         (...)
```
In the third step the client instantiates a socket object specifying a server with addition
of the server name and port number to connect to the server.
```
        Socket client = new Socket(serverName, port);
```
Then the socket class attempts to connect the client to the server. Once connected, the client 
is not able to the server through the server object.
In step five the the accept method on the server returns a reference to the new socket to the clients 
socket. 
Then communication is available between the server and the client using I/O streams. Each socket is given
an ```InputStream``` and ```OutputStream```. The output stream of the client communicates with the input stream
of the server and the output stream of the server communicates with the input stream of the client.
Then the socket then must be closed in order to ensure the socket is not bound to the given address.
```
        //Create an input stream
        DataInputStream in = new DataInputStream(server.getInputStream());

        System.out.println(in.readUTF());

        //Create an output stream
        DataOutputStream out = new DataOutputStream(server.getOutputStream());

        //Close the server socket
        server.close();
```

