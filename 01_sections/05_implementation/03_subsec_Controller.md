## Controller
The controller dictates the behaviour of the application based on user-inputs. For example if the user clicks the connect button and the user name field has a user name they will be connected to the server and there user name will be displayed in the users list on the UI and to all of the other clients. This is achieve by the action listener, which delivers the component responsible for firing an event. In this case it’s connect button. Once the connect button is pressed by the user an all the conditions are met a new socket object is instantiated specifying the address and the port number which to connect to. After the connections are established messages can now be send to the server which will be send to all other clients connected to it. This is done using the I/O streams getInputStream and the getOutputStream (see below for code snippet of what happens when a user selects the connect button on the UI).

```
if (sendEvent.getSource() == connectButton && !userLoginInput.getText().toString().equals("")) {
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
                }
                 catch (Exception ex) {
                    JOptionPane.showMessageDialog(null, "Cannot Connect Please try again");
                    userLoginInput.setEditable(true);
                }
                Thread IncomingReader = new Thread(new IncomingReader());
                IncomingReader.start();
            }
```   

