### Client Implementation

The core operations implemented into the client program are the following:   
- Create the client interface and present it to the user.   
- Present buttons to connect to the server and send a message.   

One of the core logical operations that the client performs is instantiating a connection with the server. This is achieved with the following code snippit.     

```   
public void actionPerformed(ActionEvent sendEvent) {
        if (sendEvent.getSource() == connectButton && !userLoginInput.equals("")) {
            if (isConnected == false) {
                userName = userLoginInput.getText();
                userLoginInput.setEditable(false);
                super.setTitle(userName+" Chat Window");
                try {
                    socket = new Socket(address, port);
                    InputStreamReader streamreader = new InputStreamReader(socket.getInputStream());
                    reader = new BufferedReader(streamreader);
                    writer = new PrintWriter(socket.getOutputStream());
                    writer.println(userName + ":has connected.:Connect");
                    writer.flush();
                    isConnected = true;
                } catch (Exception ex) {
                    JOptionPane.showMessageDialog(null, "Cannot Connect Please try again");
                    userLoginInput.setEditable(true);
                }
                IncomingReader();
            } else if (isConnected == true) {
                JOptionPane.showMessageDialog(null, "You are connected");
            }
        }
```   

\vspace*{\fill}     

The client then must create a new thread to listen to incoming messages from the server that it has redistributed from other clients. The client program is subclassed with a class called `IncomingReader` that, upon a connection has been made, deciphers messages that have been forwarded by the server and renders on the UI wether it is a chat message, a 'new-user' notification or if a user has disconnected. This is achieved by the below code snippit.   


```   
    public class IncomingReader implements Runnable {
        public void run() {
            String[] messageData;
            String stream, doneKey = "Done", connectKey = "Connect",
             disconnectKey = "Disconnect", chatKey = "Chat";

            try {
                while ((stream = reader.readLine()) != null) {
                    messageData = stream.split(":");

                    if (messageData[2].equals(chatKey)) {
                        sb.append(messageData[0] + ": " + messageData[1] + "<br>");
                        chatBoard.setText(sb.toString());
                    }
                    else if (messageData[2].equals(connectKey)) {
                        chatBoard.removeAll();
                        userAdd(messageData[0]);
                    }
                    else if (messageData[2].equals(disconnectKey)) {

                        userRemove(messageData[0]);
                    }
                    else if (messageData[2].equals(doneKey)) {
                        addUsers();
                        users.clear();
                    }
                }
            } catch (Exception error) {
                System.out.println("There was an error");
            }
        }
    }
```   
\vspace*{\fill}  

