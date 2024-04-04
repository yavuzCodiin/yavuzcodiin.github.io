---
title: Pathfinding with Best First Search Algorithm
published: true
mathjax: true
---

In this post I will talk about pathfinding algorithms, and try to explain how pathfinding works. First I will talk about patfinding algorithms then I will show you best-first search algorithms and how to implement it on our maze which we will create on pygame.

## Table of contents

- [What is Pathfinding?](#what-is-pathfinding)
- [Common Pathfinding Algorithms](#common-pathfinding-algorithms)
- [Algorithm](#algorithm)
    - [Creating Maze](#creating-maze)
    - [Drawing Maze and Path](#drawing-maze-and-path)
    - [Main](#main)
    - [Main Interactive](main-interactive)
     

## What is Pathfinding?

<img src="/images/post-1/what_is_pathfinding.jpg" width="1000" height="500" alt="What is Pathfinding?"/>

Pathfinding is the computational process of finding a path between two points. It is a fundamental concept in computer science, used in various fields such as robotics, video games, transportation, and network data flow. The goal of pathfinding algorithms is to find the most efficient route from the starting point to the destination, often while navigating through possible obstacles and adhering to certain rules or constraints.

* For example, in GPS navigation systems used in cars and smartphones. These systems calculate the shortest or fastest route from your current location to your desired destination.

* In robotics, pathfinding algorithms enable autonomous robots to navigate through environments, from simple vacuum cleaning robots that need to cover an entire floor efficiently without retracing their steps, to more complex industrial robots that move materials between different points in a manufacturing plant. 

* In video games, non-player characters (NPCs) must navigate the game world. Algorithms like A* and its variations are commonly used to calculate paths for characters to move from one point to another, ensuring that they can find their way around obstacles and interact with the player and the environment in a realistic manner.


## Common Pathfinding Algorithms

Where I left
https://www.perplexity.ai/search/pathfinding-algo-blog-Y07jWIAdTyKKg.rHdSpTpA