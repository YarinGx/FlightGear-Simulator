# FlightGear-Simulator
**<p text align="center">[End of Semester Project Video](https://www.youtube.com/watch?v=98-JCjLGAwg&ab_channel=YarinGridish)<p>**
Introducing our final project of the end of course of Java Programing, Building and designing GUI and desktop application for flight simulator using JavaFX
We implemented in this project with emphasis on design patterns and programming principles such as SOLID and GRASP, and finally developing our own JavaFX desktop application.

---

## [Server](https://github.com/YarinGx/FlightGear-Simulator/tree/main/Flight-Temp/src/server_side)
In this section we wrote a general server, which can be used over and over again in various projects.
In order for the server to be re-usable, there must be a seperation between the server's functionality and the rest of the code. 

Therefore, we defined the functionality of the server as an interface,
and each project can have different classes that will implement the same functionality in different ways.

### Caching
The project also has a caching system,
for it might take a lot of time to calculate some solutions.
It would be redundant to calculate a solution for a problem that we already solved.
Instead, we created a save solution functionality to save the calculations we already solved.

### Our Solver Algorithm
Given a graph, it could solve it using [A-star](https://en.wikipedia.org/wiki/A*_search_algorithm) algorithm (which is already implemented in this project based on [Dijkistra](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm) algorithm using manhattan distances) or any other search algorithm.
In our case given a graph with weights, the algorithm will run the search algorithm, and as an output it will return the shortest path to the target.
We created a Bridge Design Pattern to create a seperation between the problem and the solution of this problem. Making it generic to solve different problems.

---

## [Interpreter](https://github.com/YarinGx/FlightGear-Simulator/tree/main/Flight-Temp/src/interpreter)
The project is a GUI of a flight simulator by which you can control.

One of its features is running a script, which is basically a kind of custom programming language that can handle the plane.
For this purpose, we wrote an interpreter,for interpret a custom language into code commands  which allows you to connect to the simulator, open a server, and run various commands that control the plane and sample its data.

The first stage that happens in the interpretation process is ``Lexer``.

The Lexer takes the string as it is, and converts it to a logical distribution according to commands and parameters that can run later on with a Scanner.

The next stage is the ``Parser`` stage, which begins converting the "array" created by the Lexer into commands and executes them.

However, since the script is only supposed to control the plane, we don't want that the interpreter will have to deal with connecting to server and running the simulator, in case there are syntactic errors or incorrent entries that might be discovered in the middle of the script.

So, before we start running the commands, we will make sure that a ``Pre-Parser`` will pass the initial scan on the script and check for Syntax errors, such as incorrect parameters or irrational values.

---

## MVVM Architecture

In this project we chose to use the **MVVM architecture**.

We have the View layer that is responsible for the presentation, for example the 
input from the user. The View is also responsible for producing the graphics and has the code-
behind - for example, functions that are activated when we press a button, which are called
event-oriented programming.

* **Model** – Responsible for our business logic, such as algorithms and data access.
* **View Model** – It passes commands from the View to the Model, and its purpose is to
separate the View from the Model.
* **Data Binding** – We can wrap variables such as those in the View, and then when we change
something in the text, it will automatically changed in the ViewModel.

For the MVVM architecture to work, we'll have to wrap the different components together. 
This is done by the Observer Pattern, which binds the different components together, and notify them about changes that are made or needed to be made as required by the operator. 

---

## Design and Functionality of the App

* **Connect** – The Connect button will open a popup window and by entering ip and port we will connect to the flight simulator. The app will connect to the simulator as a client, this will also enable the use of all the functionality of the application.

* **Load data** – The Load Data button will open a folder of CSV files that are used as maps. When a CSV file is loaded then a map of the uploaded data is displayed. The map will be displayed in colors based on the height of each point in the map, the lower the area the color will be red and the higher the area the color will be greener. We will sample from the simulator the exact location of the aircraft, as a result, an icon will be displayed in the same location on the map.

* **Calculate path** - The Calculate path button will open a popup window and by entering ip and port we will connect to a server that solves search problems (A server that I built on milestones 1-3). Clicking on any point on the map will set a destination for the aircraft, and the server will calculate the cheapest route to that point.

* **Load + Autopilot** – Loads the script with the airplane commands and thanks to the Interpreter that I built, the plane goes into autopilot mode and executes the commands in the script.

* **Manual** – The manual button will move the aircraft from autopilot mode to manual mode where the user controls the aircraft with the joystick.

---

### Instructions
```scala
1.Download FlightGear - open source flight simulator
2. Download copy of the project
3. Open the Application directory
4. Edit the file location of Server.jar in the runServer.bat
5. Edit the file location of Client.jar in the runClient.bat
6. run runServer.bat
7. run runClient.bat
8. run FlightGear.exe
```
---

## Built With
* [Eclipse](https://www.eclipse.org/downloads/packages/release/kepler/sr1/eclipse-ide-java-developers) - Java IDE
* [Scene Builder](https://gluonhq.com/products/scene-builder/)  - Scene Builder 8.5.0

---
## Authors
* **Yarin Gridish** - [Profile on LinkedIn](https://www.linkedin.com/in/yarin-gridish-1411791a0/)
* **Ofry Zarfaty** - [Profile on LinkedIn](https://www.linkedin.com/in/ofry-zarfaty-b85b10146/)
