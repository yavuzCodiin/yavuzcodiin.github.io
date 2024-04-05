---
title: Pathfinding with Breadth First Search Algorithm
published: true
mathjax: true
---

In this post I will talk about pathfinding algorithms, and try to explain how pathfinding works. First I will talk about patfinding algorithms then I will show you breadth-first search algorithms and how to implement it on our maze which we will create on pygame.

## <u>Table of contents</u>

- [What is Pathfinding?](#what-is-pathfinding)
- [Common Pathfinding Algorithms](#common-pathfinding-algorithms)
- [General Process](#general-process)
- [Algorithm](#algorithm)
    - [Creating Maze](#creating-maze)
    - [Drawing Maze and Path](#drawing-maze-and-path)
    - [Main](#main)
    - [Main Interactive](main-interactive)
     

## <u>What is Pathfinding?</u>

<img src="/images/post-1/what_is_pathfinding.jpg" width="1000" height="500" alt="What is Pathfinding?"/>

Pathfinding is the computational process of finding a path between two points. It is a fundamental concept in computer science, used in various fields such as robotics, video games, transportation, and network data flow. The goal of pathfinding algorithms is to find the most efficient route from the starting point to the destination, often while navigating through possible obstacles and adhering to certain rules or constraints.

* For example, in GPS navigation systems used in cars and smartphones. These systems calculate the shortest or fastest route from your current location to your desired destination.

* In robotics, pathfinding algorithms enable autonomous robots to navigate through environments, from simple vacuum cleaning robots that need to cover an entire floor efficiently without retracing their steps, to more complex industrial robots that move materials between different points in a manufacturing plant. 

* In video games, non-player characters (NPCs) must navigate the game world. Algorithms like A* and its variations are commonly used to calculate paths for characters to move from one point to another, ensuring that they can find their way around obstacles and interact with the player and the environment in a realistic manner.


## <u>Common Pathfinding Algorithms</u>

### <u>A* (A-Star) Algorithm</u>
The A* algorithm is one of the most popular and widely used pathfinding algorithms, known for its efficiency and accuracy. It combines features of Dijkstra's Algorithm (which focuses on finding the shortest path) and the Best-First-Search, making it highly effective in a variety of scenarios. A* uses a heuristic to estimate the cost from the current node to the goal, reducing the number of nodes it needs to explore. This makes it particularly suitable for applications where a balance between speed and accuracy is crucial, such as in video games or robotic path planning.

### <u>Dijkstra's Algorithm</u>
Dijkstra's Algorithm is a foundational algorithm for finding the shortest path between nodes in a graph. It works by systematically exploring all possible paths, starting from the initial node, and continuously expanding the closest node until it reaches the destination. While it guarantees the shortest path, it can be slower than A* because it doesn't use a heuristic to guide its search.

### <u>Floyd-Warshall Algorithm</u>
The Floyd-Warshall algorithm is a comprehensive algorithm used for finding shortest paths in a weighted graph with positive or negative edge weights (but with no negative cycles). It's capable of finding the shortest paths between all pairs of nodes. While not as commonly used in real-time applications due to its computational complexity, it's extremely powerful for pre-calculating paths or analyzing dense networks.

<img src="/images/post-1/floyd_warshall.jpg" width="1400" height="400" alt="Floyd Warshall"/>|<img src="/images/post-1/floyd_warshall_2.jpg" width="1400" height="400" alt="Floyd Warshall"/>

<img src="/images/post-1/floyd_warshall_3.jpg" width="1200" height="350" alt="Floyd Warshall"/>

### <u>Breadth-First Search</u>
Breadth-First Search (BFS) is an algorithm used for traversing or searching tree or graph data structures. It starts at a selected node (often the root in the case of trees, or any arbitrary node for graphs) and explores all of the neighbor nodes at the present depth prior to moving on to the nodes at the next depth level. It's called "Breadth-First" because it expands the frontier between discovered and undiscovered nodes uniformly across the breadth of the frontier.

## <u>General Process</u>

<img src="/images/post-1/general_process.jpg" width="1400" height="850" alt="General Process"/>

## <u>Algorithm</u>
In this project, I started by figuring out how to construct a maze. Once I had a grasp on that, I moved on to understanding the pathfinding algorithm and how it could work within the maze I created. My next step was to think about how to visually represent both the maze and the algorithm's pathfinding process. This is where Pygame came into play. I used Pygame to not only create the maze but also to visualize the algorithm in action. Finally, I wanted to make the whole experience interactive, so I added the ability for users to control the visualization, allowing them to move forwards and backwards through the steps of the algorithm. This approach helped me connect all the different parts of my project, from the maze creation to the algorithm implementation and visualization.

- ### <u>Creating Maze</u>
```python
import copy, random, types
from enum import Enum
```
```python
class CellType(Enum):
    Empty = 1
    Block = 2
```
```python
class CellMark(Enum):
    No = 0
    Start = 1
    End = 2
```
```python
class Cell:
    def __init__(self, type = CellType.Empty, pos = None):
        self.type = type
        self.pos = pos
        self.count = 0
        self.path_from = None
        self.mark = CellMark.No
```
```python
class Cell_Network:
    def __init__(self, board):
        self.board = board
    
    def get_size(self):
        """

        Get the size of the board. This method returns the dimensions of the board as a list, where the first element is the number of rows (height) and the second element is the number of columns (width).

        Parameters:
        ----------
        self : object
            The instance of the class from which this method is called. It must have a `board` attribute, which is a list of lists representing the grid.

        Returns:
        -------
        list of int
            A list containing two integers:
            - The first integer represents the number of rows(height) in the board.
            - The second integer represents the number of columns(width) in the board.

        """
        return [len(self.board), len(self.board[0])]
    
    def at(self, pos):
        """

        Retrieve the cell object at a specified position in the board.

        Parameters:
        ----------
        self : object
            The instance of the class from which this method is called.
        
        pos : list or tuple of int
            A list or tuple containing the [row_index, column_index] of the cell.

        Returns:
        -------
        Cell
          The cell object located at the specified position.

        """
        return self.board[pos[0]][pos[1]]
    
    def clone(self):
        """
        Clone the board.
        
        Parameters:
        ----------
        self : object
            The instance of the class from which this method is called.

        Returns:
        -------
        Cell_Network
          A copy of the board.

        """
        return Cell_Network(copy.deepcopy(self.board))
    
    def clear_count(self, count):
        """

        Clear the count of each cell

        Parameters:
        -----------
          self (object):
            The instance of the class from which this method is called.

          count (int): The number we want to give all the cell count.
        
        Returns:
        --------
          None  
        
        """
        for o in self.board:
            for i in o:
                i.count = count
                i.path_from = None

    def is_valid_point(self, pos):
        """

        Check if the given position is within the bounds of the board.
    
        Parameters:
        ----------
        self : object
            The instance of the class from which this method is called.
        
        pos : list or tuple of int
            A list or tuple containing the [row_index, column_index] of the cell.
    
        Returns:
        -------
        bool
          True if the position is within the bounds of the board, False otherwise.

        """
        sz = self.get_size()
        return (pos[0] >=0) and (pos[1] >= 0) and (pos[0] < sz[0]) and (pos[1] < sz[1])
```