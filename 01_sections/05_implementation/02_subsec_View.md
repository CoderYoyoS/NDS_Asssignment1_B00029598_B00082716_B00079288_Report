## View
Now that the client and the server are interacting in the correct manor, the GUI's for both can now be implemented. The interfaces are entirely constructed using the Java Swing libraries. The client UI was implemented first as this GUI was more complex and required more components. This interface was developed using layout managers, panels and other components such as buttons, text fields and text panes which are inherited form the aforementioned libraries. The client view comprised of four main panels which are as follows the main, top, middle and bottom panel. Each of these panels was design and created inside a method which returns a fully built panel comprised of the appropriate components needed for each one. The main panel is a container which encompasses all the other panels. It was developed using a layout manager called the border layout, which all the other panels can be added in a North, South, East, West  and Centre formant. The top panel simply contains a logo for the application and is added to the top of the main panel.

```
    mainPanel.add(getTopPanel(), BorderLayout.NORTH);
    mainPanel.add(getMiddlePanel(), BorderLayout.CENTER);
    mainPanel.add(getBottomPanel(), BorderLayout.SOUTH);
```
