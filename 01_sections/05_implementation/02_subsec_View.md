## View


Now that the client and the server are interacting in the correct manor, the GUI's for both can now be implemented. The interfaces are entirely constructed using the Java Swing libraries. Out of the two interfaces the client was created first as this GUI was more complex and required more components. Additionally, the client interface was developed using layout managers, panels and other components such as buttons, text fields and text panes which are inherited from the aforementioned libraries. Furthermore, this UI is broken up into four main sections which are made of panels. These comprise of the main, top, middle and the bottom panel. Each of these panels were create inside their own individual methods which returns fully built panels with the appropriate components, sizes and colours (please see the below code snippet 1 to view how the panels were created for the UI). The main panel is a container which encompasses all the other panels through the use of a layout manager called the BorderLayout. Which subsequent panels can be added in a top (North), left (West), right (East), and bottom (South) order. This allowed all other fully built panels to be easily added to the main panel in the name sake positions once created (please see the below code snippet 2 to view how the panels were added to the main panel). For the server GUI the same appropriate was taken in the way sections were broken up into panels how they were created and added to a main panel. However this UI was less complex and required less components (please see the below screen shots to see both client and server GUI's).
```
    code snippet 1

      private JPanel getTopPanel() {
        JPanel topPanel = new JPanel(new BorderLayout());
        topPanel.setPreferredSize(new Dimension(0, 105));
        topPanel.setBackground(new Color(13, 101, 253));
        topPanel.setBorder(BorderFactory.createMatteBorder(2, 2, 2, 2, (new Color(224, 3, 69))));
        ImageIcon iconLogo = new ImageIcon("images/logo.jpg");
        JLabel logo = new JLabel(iconLogo);
        topPanel.add(logo, BorderLayout.CENTER);
        return topPanel;
    }
```

```
    code snippet 2
    mainPanel.add(getTopPanel(), BorderLayout.NORTH);
    mainPanel.add(getMiddlePanel(), BorderLayout.CENTER);
    mainPanel.add(getBottomPanel(), BorderLayout.SOUTH);
```
![Image of Client UI. \label{figure 1}](04_assets/04_system_design/clientGUI.PNG){width=60% height=60%}

![Image of Server UI. \label{figure 1}](04_assets/04_system_design/serverGUI.PNG){width=60% height=60%}
