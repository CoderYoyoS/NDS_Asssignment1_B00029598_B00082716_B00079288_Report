### Server Implementation

The core operations implemented into the server program are as follows:   
- Start the server on a thread and listen to connection requests from clients.   
- Accept the client connection.   
- Extract the message from the clients output.   
- Create a new thread to process the clients output.  

See below code snippet to see how this was achieved.   

Server.java code snippet   
\vspace*{\fill}   
```   
    public class StartServer implements Runnable {
		public void run() {
            connections = new ArrayList<String>();
            users = new ArrayList<String>();
            try {
				ServerSocket serverSocket = new ServerSocket(2222);
                while (true) {
                    Socket clientSocket = serverSocket.accept();
                    PrintWriter writer = new PrintWriter(clientSocket.getOutputStream());
                    connections.add(writer);
                    Thread clientListener = new Thread(new ClientHandler(clientSocket, writer));
                    clientListener.start();
                }
            } catch (Exception error) {
                sb.append("Error making a connection."+ "<br>");
                serverLogBoard.setText(sb.toString());

            }
        }
    }
```   
\vspace*{\fill}   

The ```Server.java``` program is sub-classed with the ```ClientHandler``` thread class that runs the thread for processing the clients output. Whilst processing a message from the client, the primary purpose of ```ClientHandler``` is to:   
- Extract the output.   
- Determine whether the transmission was a new connection, a disconnection or a chat message.   

This is necessary for outputting to the server log (more on this in the Controller subsection) what is happening at that specific moment in time in the system. See below code snippet of how the ```ClientHandler``` subclass was implemented.   
\vspace*{\fill}  
```   
 public ClientHandler(Socket clientSocket, PrintWriter user) {
            client = user;
            try {
                sock = clientSocket;
                InputStreamReader isReader = new InputStreamReader(sock.getInputStream());
                reader = new BufferedReader(isReader);
            } catch (Exception error) {
                serverLogBoard.setText("Unexpected error. \n");
            }
        }

        public void run() {
            String message, connectKey = "Connect", disconnectKey = "Disconnect", chatKey = "Chat";
            String[] messageData;

            try {
                while ((message = reader.readLine()) != null) {
                    messageData = message.split(":");

                    if (messageData[2].equals(connectKey)) {
                        sb.append(messageData[0]  + " has entered the chat "+ "<br><br>");
                        serverLogBoard.setText(sb.toString());
                        addUser(messageData[0]);
                    }
                    else if (messageData[2].equals(disconnectKey)) {
                        sb.append(messageData[0]+ " has left the chat "+ "<br><br>");
                        serverLogBoard.setText(sb.toString());
                        connections.remove(client);
                        removeUser(messageData[0]);
                    }
                    else if (messageData[2].equals(chatKey)) {
                        sb.append(messageData[0] +" Typed "+ messageData[1] + "<br><br>");
                        serverLogBoard.setText(sb.toString());
                        sendToAll(message);
                    }
                }
            } catch (Exception ex) {

               ex.printStackTrace();
            }
        }
```
\vspace*{\fill}  




