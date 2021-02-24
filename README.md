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

## [Interpreter](https://github.com/YarinGx/FlightGear-Simulator/tree/main/Flight-Temp/src/interpreter)
