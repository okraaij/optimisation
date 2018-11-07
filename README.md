# Optimisation
Routing, Inventory and Supply Chain optimisation using heuristics

## Overview

- This repository contains several of the (Traveling Salesman Problem) projects I have previously participating in working on for the MSc Business Analytics at the University of Edinburgh. 
- These projects revolved around solving TSP-LIB (see: [TSP-LIB](https://comopt.ifi.uni-heidelberg.de/software/TSPLIB95/)) EUC-2D (n ≤ 500) instances by using heuristics
- The MATLAB implementation is provided for
  - The following 7 construction heuristics:
    - the Nearest Neighbour (NN) algorithm
    - the Nearest Merger (NM) algorithm
    - the Clarke & Wright (C&W) Savings algorithm
    - Insertion Procedures
      - Cheapest Insertion (CI)
      - Farthest Insertion (FI)
      - Nearest Insertion (NI)
      - Arbitrary Insertion (AI)
   - The following 4 Classical Local Search (CLS) algorithms:
    - Random Descent (2-opt)
    - Random Descent (3-opt)
    - Steepest Descent (2-opt)
    - Steepest Descent (3-opt)

## Explanation of terms

A heuristic aims to generate high quality solutions but cannot guarantee to find the optimal solution.

A construction heuristic is a type of heuristic defined by Kahng and Reda (2004) as an alternative to an exact solution that performs a sequence of operations until a valid tour is obtained, at which point the heuristic stops and reports the constructed tour. 

A Classical Local Search (CLS) algorithm is a type of heuristic that “operates using a single state and its set of neighbours” (Nunes De Castro, 2002). 

A neighbourhood structure defines the set of solutions than can be reached from a given solution in one single step of a local search process. This single step is commonly called a move, which is a basic operation that transforms a given solution into another one. 
In its simplest form, an initial solution - in this case provided by the NN procedure - and a transition mechanism is employed to generate a neighbour of this solution. If this neighbour is an improvement to the current solution or leads to an improvement to the objective function value (the total distance traveled in the TSP instance), the current solution - commonly referred to as the seed solution - is replaced by the neighbour generated. This process is repeated until there is no better neighbour that can be found. 


## Explanation of techniques

#### Nearest Neighbour (NN)
- Starts with an empty solution, randomly selects a starting point and repeatedly extends the current solution by selecting the nearest node to the last node selected. This process is repeated until each node in the TSP instance has been visited once only, resulting in a complete unique tour being generated. 
#### Nearest Merger
- Starts with n sub-tours, each containing one node. Then, it finds the two closest sub-tours, where the distance between any pair of nodes in the selected two sub-tours is minimal. After that, it merges the two selected sub-tours based on minimum insertion cost criterion. This process repeats until each node in the instance has been included in one complete tour.
#### Clarke & Wright Savings Algorithm
- A commonly studied greedy heuristic that selects a central node as starting point. The algorithm then computes the savings that can be obtained by linking two nodes rather than visiting them individually. Based upon the highest amount of savings, two nodes are linked together. This process continues until a complete tour has been created.
#### Insertion Procedures 
All of the insertion procedures start with a sub-tour and iteratively determine which of the remaining nodes shall be inserted into the sub-tour next (the selection step) and where (between which two nodes) it should be inserted (the insertion step).
- Farthest Insertion 
    - Expands the current sub-tour by inserting the remaining nodes, which have the maximum distance from any node in the current sub-tour. Where the selected node should be inserted is based on the minimum insertion cost criterion.
- Cheapest Insertion 
    - Determines simultaneously which node not already in the sub-tour should join the sub-tour next and where it should be inserted, using the minimum insertion cost criterion.
- Arbitrary Insertion
    - Selects randomly a node not already in the sub-tour to join the sub-tour and inserts it using the minimum insertion cost criterion.
- Nearest Insertion
    - Selects the node which has the minimum distance from any node in the current sub-tour and inserts it using the minimum insertion cost criterion.
