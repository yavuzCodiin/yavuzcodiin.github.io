---
title: Pathfinding with Best First Search Algorithm
published: true
mathjax: true
---

In this post I will talk about pathfinding algorithms, and try to explain how pathfinding works. First I will talk about patfinding algorithms then I will show you Best-first search algorithms and how to implement it on our maze which we will create on pygame.

## <u>Table of contents</u>

- [What is Pathfinding?](#what-is-pathfinding)
- [Common Pathfinding Algorithms](#common-pathfinding-algorithms)
- [General Process](#general-process)
- [Path Finding](#path-finding)
    - [Creating Maze](#creating-maze)
    - [Algorithm](#algorithm)
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

### <u>Best-First Search</u>
Best-First Search (BFS) is an algorithm used for traversing or searching tree or graph data structures. It starts at a selected node (often the root in the case of trees, or any arbitrary node for graphs) and explores all of the neighbor nodes at the present depth prior to moving on to the nodes at the next depth level. It's called "Best-First" because it expands the frontier between discovered and undiscovered nodes uniformly across the Best of the frontier.

## <u>General Process</u>

<img src="/images/post-1/general_process.jpg" width="1400" height="850" alt="General Process"/>

## <u>Path Finding</u>
In this project, I started by figuring out how to construct a maze. Once I had a grasp on that, I moved on to understanding the pathfinding algorithm and how it could work within the maze I created. My next step was to think about how to visually represent both the maze and the algorithm's pathfinding process. This is where Pygame came into play. I used Pygame to not only create the maze but also to visualize the algorithm in action. Finally, I wanted to make the whole experience interactive, so I added the ability for users to control the visualization, allowing them to move forwards and backwards through the steps of the algorithm. This approach helped me connect all the different parts of my project, from the maze creation to the algorithm implementation and visualization.

- ### <u>Creating Maze</u>
I tried to give well documented clear code and every function has its docstring but I will also add my comments too this is same for other parts of the project too.
 
```python
import copy, random, types
from enum import Enum
```
I first created Cell structure, each cell will have two type, one of them will be `Empty` which our algorithm can move and search through and `Block` for walls of our maze  
```python
class CellType(Enum):
    Empty = 1
    Block = 2
```
We have marks on cells so one will be for `Start` and `End` and `No` for rest 
```python
class CellMark(Enum):
    No = 0
    Start = 1
    End = 2
```
Here cell is initialized each cell will have these attributes `type`, and `mark` as we defined previously, `position`, `count` for counting steps, `path_from` for storing where it came from
```python
class Cell:
    def __init__(self, type = CellType.Empty, pos = None):
        self.type = type
        self.pos = pos
        self.count = 0
        self.path_from = None
        self.mark = CellMark.No
```
A cell network formed by the combination of cell objects
```python
class Cell_Network:
    def __init__(self, board):
        self.board = board
```
With `get_size` we get board's height and width.

<img src="/images/post-1/get_size.jpg" width="450" height="250" alt="Get Size"/>

```python
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
```
We will get our cell position located `at` specified position
```python
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
```
Simply cloning the board
```python
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
```
Clearing the board with specified count for example at the beginning we have infinite possibilities right, so we give count = math.inf to make count of each cell equals to infinity

```python
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
```
We need to make sure if the position is valid point, and that it appears within the boundaries of the board. 

```python
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

We create empty maze with `create_empty_maze` it takes width and height of maze and returns namespace with attributes like `board` which is created by combination of cells, also we have `start` and `end` positions.

```python
def create_empty_maze(x, y): #create empty maze with board, start, end attributes
    """
    
    Create a empty maze and return its structure along with start and end points

    Parameters:
    ----------
    x (int):
        The width of the maze (number of cells horizontally).
 
    y (int):
        The height of the maze (number of cells vertically).

    Returns
    -------
    types.SimpleNamespace
        A namespace with the following attributes:
          - board : list of list of Cell objects
              The maze structure represented as a 2D grid.
          - start : list of int
              The starting coordinates [x, y] in the maze.
          - end : list of int
              The ending coordinates [x, y] in the maze.

    """
    return types.SimpleNamespace(
        board = Cell_Network( [[Cell(type=CellType.Empty, pos=[ix, iy]) for iy in range(y) ] for ix in range(x)] ),
        start=[random.randrange(0, x), random.randrange(0, y)],
        end= [random.randrange(0, x), random.randrange(0, y) ]
    )
```

With `create_wall_maze` we created a whole maze with walls, again it returns namespace with same attributes as `create_empty_maze`.

```python
def create_wall_maze(x, y):
    """

    Create a maze with walls and return its structure along with start and end points.

    Parameters:
    ----------
    x (int):
        The width of the maze (number of cells horizontally).
    y (int):
        The height of the maze (number of cells vertically).

    Returns:
    -------
    types.SimpleNamespace
        A namespace with the following attributes:
            - board : list of list of Cell objects
                The maze structure represented as a 2D grid.
            - start : list of int
                The starting coordinates [x, y] in the maze.
            - end : list of int
                The ending coordinates [x, y] in the maze.
    """
    #board creation
    board = [[Cell(type = CellType.Empty, pos=[ix,iy]) for iy in range(y)] for ix in range(x)]
    
    #wall creation
    for i in range(0,x):
        board[i][int(y/2)].type = CellType.Block
    for i in range(0,y):
        board[int(x/2)][i].type = CellType.Block

    #Wall Opening Creation    
    board[random.randint(0, x/2-1)][int(y/2)].type = CellType.Empty #random opening in the left half of the vertical wall
    board[random.randint(x/2+1, x-1)][int(y/2)].type = CellType.Empty #random opening in the right half of the vertical wall
    board[int(x/2)][random.randint(0, y/2-1)].type = CellType.Empty #random opening in the top half of the horizontal wall
    board[int(x/2)][random.randint(y/2+1, y-1)].type = CellType.Empty #random opening in the bottom half of the horizontal wall

    return types.SimpleNamespace( board = Cell_Network(board),
		start = [random.randrange(0,x/2), random.randrange(y/2+1,y)],
		end = [random.randrange(x/2+1,x), random.randrange(0,y/2)] )
```

I used `add_point` function to calculate the position of neighboring cells. For example if I have [2,3] as position, to move left neighbor I can add [2,3] with [-1,0] 

```python
def add_point(a, b):
    """
    
    Add two points represented by their coordinates.

    This function is typically used to calculate the position of neighboring cells by adding their relative positions to the current cell's position.

    Parameters:
    ----------
    a : list or tuple of int
        The [x, y] coordinates of the first point.
    b : list or tuple of int
        The [x, y] coordinates of the second point, often representing a relative position.

    Returns:
    -------
    list of int
        A list containing the resulting [x, y] coordinates after addition.
    
    """

    return [a[0]+ b[0], a[1]+ b[1]]
```

<img src="/images/post-1/empty_and_walled_maze.jpg" width="850" height="350" alt="Empty & Wall Maze"/>

So this is our maze with `Cell`, `CellMark`, `CellType`, `Cell_Network` we have four classes and they have their attributes so along the way we will use them to create algorithm, finding path and visualizing this let's see how our algorithm works.

### <u>Algorithm</u>

> Greedy BeFS 
> Using a greedy algorithm, expand the first successor of the parent. After a successor is generated:
>1. If the successor's heuristic is better than its parent, the successor is set at the front of the queue (with the parent reinserted directly behind it), and the loop restarts.
>
>2. Else, the successor is inserted into the queue (in a location determined by its heuristic value). The procedure will evaluate the remaining successors (if any) of the parent.

Below you can see how our algorithm works in pseudocode to have more information you can visit [wikipedia](https://en.wikipedia.org/wiki/Best-first_search#Greedy_BeFS)

```rust
procedure GBS(start, target) is:
  mark start as visited
  add start to queue
  while queue is not empty do:
    current_node ← vertex of queue with min distance to target
    remove current_node from queue
    foreach neighbor n of current_node do:
      if n not in visited then:
        if n is target:
          return n
        else:
          mark n as visited
          add n to queue
  return failure
```
Our shortest path algorithm requires a board, a start point, an end point, and the maximum distance allowed for the path. It begins by cloning the board, and then it operates on this cloned version. As previously discussed in the context of the cell network, we initialize each cell's count to math.inf. Next, we mark the start and end points on the board. The first position is added to the open list, which we will use to check the cells, setting the start cell's count to 0. We then define our neighbors as [left, right, down, up]. As long as there are cells in the open list, our function continues to operate. It starts by popping the first cell from the list and designating it as the current position. We retrieve the cell at the current position and proceed to check its neighbors. For a neighbor to be considered, it must be a valid point, and its type must be empty. If these conditions are met, we increment the current cell's count by 1 to determine the distance. If this distance is less than the maximum allowed, we assign this distance to the neighbor's count and record the cell it originated from. Finally, we add the neighbor's position to the open list to continue the search process.

While measuring the distance we will use something called Manhattan Distance, it is named after grid shape of streets in Manhattan and in this streets we can't move diagonally so we either move in x or y never both at the same time, so we can't use euclidean distance.

<img src="/images/post-1/manhattan_distance.jpg" width="850" height="450" alt="Manhattan Distance"/>

This function calculates the distance from start for every cell, not only destination, this is helpful when we think about robots navigation where robot might need to navigate to various points in an environment efficiently. We can use it to calculate the shortest path to any of the nodes. However, if optimization is our priority we'd change the algorithm, when it finds destination it stops.

```python
import my_maze
import math

def fill_shortest_path(board, start, end, max_distance=math.inf):
    """

    Finds and marks the shortest path in a maze from a start point to an end point.

    Parameters:
    ----------
    board (my_maze.Board):
        The board represents the maze structure, where each cell can be empty or a wall.
    
    start (tuple):
        A tuple of two integers representing the starting position (row, column) in the maze.
    
    end (tuple):
        A tuple of two integers representing the ending position (row, column) in the maze.
    
    max_dist (int, optional):
        The maximum distance allowed for the path. If the shortest path exceeds this distance,
        the search is aborted. By default, it is set to `math.inf`, allowing for the maximum
        possible distance.

    Returns:
    -------
    my_maze.Board
        A clone of the original `board` object with the shortest path marked.

"""    
    nboard = board.clone()
    nboard.clear_count(math.inf) #infinite possibilities at start

    nboard.at( start ).mark = my_maze.CellMark.Start
    nboard.at( end ).mark = my_maze.CellMark.End

    open_list = [ start ]
    nboard.at( start ).count = 0
    neighbours = [[-1, 0], [1, 0], [0, 1], [0, -1]]

    while open_list:
        current_pos = open_list.pop(0)
        current_cell = nboard.at( current_pos )
        for neighbour in neighbours:
            ncell_pos = my_maze.add_point(current_pos, neighbour)
            if not nboard.is_valid_point(ncell_pos):
                continue
            cell = nboard.at( ncell_pos )
            
            if cell.type != my_maze.CellType.Empty:
                continue
            
            dist = current_cell.count+1
            if dist > max_distance:
                continue
            
            if cell.count > dist: #math.inf > 1
                cell.count = dist # cell.count = 1
                cell.path_from = current_cell # Records which cell we came from to reach this neighbor
                open_list.append(ncell_pos) #now we will search this This backtracking information
                                            #is used to reconstruct the path once the end cell is reached.
    return nboard
```

We will use backtracking to find shortest path, it works as follows:
1. Start from destination cell.
2. Scan neighbours and pick with lowest number.
3. Repeat the process until you reach start cell.

```python
def backtrack_to_start(board, end):
    """

    Parameters:
    -----------
       board (my_maze.Board):
         The maze board object. The board represents the maze structure, where
         each cell can be empty or a wall.
       
       end (tuple):
         A tuple of two integers representing the ending position (row, column) in the maze.
    
    Returns:
    --------
      list:
        A list of `Cell` objects representing the path from the end position to the start
        position.

    """

    cell = board.at( end )
    path = []
    while cell != None:
        path.append(cell)
        cell = cell.path_from
    
    return path
```

<img src="/images/post-1/finding_path_maze.png" width="850" height="550" alt="Shortest Path"/>

### <u>Drawing Maze and Path</u>
Until here we created structure of our maze, then we created our shortest path finding algorithm now we will visualize them.

```python
import pygame, math
import my_maze

pygame.init()
pygame.display.set_caption("Demo => Path Finding")
cell_font = pygame.font.SysFont(pygame.font.get_default_font(), 25)
```

This function `trans_rect` is designed to move a rectangle by a specified offset without altering its size.

```python
def trans_rect(r, offset):
    """

    This function takes rect( => x, y, w, h <= ) then adjusts the position of rectangle by applying an offset to it
    
    Parameters:
    -----------
        r (list): This parameter represents rectangle.

        offset (list): This parameter represents the offset by which you want to move the rectangle. 
    
    Returns:
    --------
        (list):
            - The new x-coordinate of the rectangle's top-left corner.
            - The new y-coordinate of the rectangle's top-left corner.
            - The original width of the rectangle.
            - The original height of the rectangle
    
    """
    return [r[0]+offset[0], r[1]+offset[1], r[2], r[3]]
```

Our main loop for controlling the application 

```python
def main_loop(ui):
    """
    
    Run the main event loop of the application.

    This function initializes the display, handles user input events, and updates the display based on the user interface (UI) object's draw method. The loop runs indefinitely until the user quits the application or presses the escape key.

    Parameters
    ----------
      ui : object
        An instance of a user interface class that has `step`, `reset`, and `draw` methods.

    Returns
    -------
      None

    """
    
    screen = pygame.display.set_mode((1000,800))

    clock = pygame.time.Clock()
    clock.tick()

    while True:
        event = pygame.event.poll()
        if event.type == pygame.QUIT:
            break
        elif event.type == pygame.KEYDOWN:            
            if event.key == pygame.K_ESCAPE:
                break
            if event.key == pygame.K_LEFT:
                ui.step(-1)
            if event.key == pygame.K_RIGHT:
                ui.step(1)
            if event.key == pygame.K_r:
                ui.reset()
        
        ui.draw(screen)

        pygame.display.update()
        clock.tick(60)
    
    pygame.quit()
```

The Finder class is designed to manage and visualize a board and a path.

```python
class Finder:
    def __init__(self):
        self.board = None
        self.path = None
```

```python
    def set_board(self, board):
        """

        Set the board attribute of the instance.

        Parameters
        ----------
          self : object
            The instance of the class from which this method is called.
        
          board : Board
            The board object to be set for the instance.

        Returns
        -------
          None

        """
        self.board = board
```
```python
    def set_path(self, path):
        """

        Set the path attribute of the instance.

        Parameters
        ----------
          self : object
            The instance of the class from which this method is called.
        
          path : list of tuples/lists
            The path to be set for the instance, typically a list of positions.

        Returns
        -------
          None
        
        """
        self.path = path
```
```python
    def run(self):
        """

        Start the main event loop of the application.

        This method calls the main_loop function, passing the current instance as an argument.

        Parameters
        ----------
          self : object
            The instance of the class from which this method is called.

        Returns
        -------
          None

        """
        main_loop(self)
```

```python
    def draw(self, surface):
        """
        Draw the board and path on the given surface.

        This method draws the board on the provided surface. If a path is set, it also draws the path.
    
        Parameters
        ----------
          self : object
            The instance of the class from which this method is called.
        
          surface : pygame.Surface
            The Pygame surface on which the board and path will be drawn.
    
        Returns
        -------
          None
        
        """
        if self.board == None:
            return
        
        draw_board(surface, surface.get_rect(), self.board)
        if self.path != None:
            draw_path(surface, surface.get_rect(), self.board, self.path)
```
Next I will talk about metrics of board which we will use them to draw our cell, maze, path.

This class will help us to locate specific parts of the board, including the left, top, height, and bottom. Additionally, it will help us to determine cell's x and y coordinates, allowing us to create a cell rectangle.  

```python
class BoardMetrics:
    def __init__(self, area, board):
        self.area = area #area of the board which is surface.rect() object rect<x,y,w,h> board is what we created in my_maze.py
        self.spacing = 3 #spacing for cell's and board
        self.left = area[0] + self.spacing #left is starting position of cell 1 with spacing
        self.top = area[1] + self.spacing  # same for left but for top side
        self.height = area[3] - area[1] - 2 * self.spacing #height of board - 2 spacing from each side
        self.width = area[2] - area[0] - 2 * self.spacing #width of board - 2 spacing from each side
        self.num_y = board.get_size()[1] #board height with number of rows[[][]---]
        self.num_x = board.get_size()[0] #board width with number of columns[[1,2,3,4...]]
        self.cx = self.width / self.num_x #cell's x found by dividing width of board to num of cell's
        self.cy = self.height / self.num_y #cell's y found by dividing height of board to num of cell's
```

<img src="/images/post-1/board_metrics.jpg" width="850" height="450" alt="Board Metrics"/>

