## Class Structure
In order to structure the system in an effective way, class diagrams have been designed to provide an overview of how the system will operate. Ideally, to provide a better layer of scalability,  the system should be designed in a way whereby the GUI's are segmented from the logical implementation of the server and the client. However, because of the scope of this project and the requirement to demonstrate proper usage of a transmission protocol using Java, in the server and the client, both GUI's and logic, are implemented with one file each, ```Server.java``` and ```Client.java```. 

### Server
The server UML class diagram consists of a ```Server``` class that extends the Java ```JFrame``` class in order to provide a graphical user interface. Also, the ```ActionListener``` interface is implemented in order to allow user interaction with buttons on the GUI. The ```Server``` class consists of array list attributes to store the connections within the server, and also store the clients names connected to the server. Within the ```Server``` class there is an inner class called ```StartServer``` that implements the Java ```Runnable``` interface. Another inner class called ```ClientHandler```  implements the ```Runnable``` interface to allow multithreading. This class is used to set the client from a passed parameter and handle the messages that income from the clients. Additional public methods are also used within he server to add a user, remove a user, and send an incoming message to all clients connected to the server.

 ![Server Class Diagram. \label{Server}](04_assets/04_system_design/ClassDiagrams/ServerClass-Diagram.jpg)

### Client
Secondly, the ```Client``` also extends the java ```JFrame``` class to provide a graphical interface. The ```ActionListener``` interface is implemented to allow client interaction. Attributes such as a port number, socket, and address are declared initially in the program. Multiple methods implementations are used to provide graphical look-and-feel within the program. The class also runs a separate class called ```IncomingReader``` which runs a thread to listen and handle any messages  being redistributed from the server sent to the client. 

 ![Client Class Diagram. \label{Client}](04_assets/04_system_design/ClassDiagrams/ClientClass-Diagram.jpg)
