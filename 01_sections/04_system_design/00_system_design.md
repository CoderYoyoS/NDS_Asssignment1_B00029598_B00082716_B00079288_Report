# System Design

##GUI Design
During the design process for both the client and the server GUI's there was a priority on making both the designs similar in order  to give the overall application a uniform look and feel. Furthermore, during the deliberation of both UI's, a particular emphasis was given to creating simple and easy to use interfaces. Both the client and server design will be discussed separately below in order to give a more detailed description.

## GUI Design Client
In the design process  of the client GUI specific attention was paid to creating a simple and easy to use interface. To achieve this a simplistic single page interface was implemented to simplify and limit the user’s interaction with the UI. Moreover, this interface was designed to be simplistic in the way it refreshed and updated the interface, this was done by merely refreshing certain fields with updated values. Incorporating, this simple design model led to a simplistic implementation for the client interface and more emphasis could be placed on the back end server, client logic. Please see figure 3.1 below to see a simple design mockup.

![Mockup Image of Client UI. \label{figure 1}](04_assets/04_system_design/clientGUIDesign.PNG){width=60% height=60%}

## GUI Design Server
When designing the UI for the server, there was a focus put on mirroring the layout and structure of the client design as mentioned previously. In addition, the server interface was designed in a clear and concise manner in order for it to be easy to not only keep track of who is using the application but also to see each user that has entered into the chat group. 

![Mockup Image of Server UI. \label{figure 2}](04_assets/04_system_design/serverGUIDesign.PNG){width=60% height=60%} 

## Class Diagrams
In order to structure the system in an effective way, class diagrams have been designed to provide an overview of how the system will operate. Ideally, to provide a better layer of scalability,  the system should be designed in a way whereby the GUI's are segmented from the  logical implementation of the server and the client. However, because of the scope of this project and the requirement to demonstrate proper usage of a transmission protocol using Java, both the server and the client, both GUI's and logic, are implemented with one file each, ```Server.java``` and ```Client.java```. 
