# Optimisation
Routing, Inventory and Supply Chain optimisation using heuristics

## Overview

- This repository contains several of the (Traveling Salesman Problem) projects I have previously worked on for the MSc Business Analytics at the University of Edinburgh. 
- Most of these projects revolved around solving TSP-LIB (see: [TSP-LIB](https://comopt.ifi.uni-heidelberg.de/software/TSPLIB95/)) EUC-2D (n ≤ 500) instances by using heuristics
- The code is provided in MATLAB for the following 7 construction heuristics:
  - the Nearest Neighbour (NN) algorithm
  - the Nearest Merger algorithm
  - the Clarke & Wright savings procedure
  - Insertion procedures
    - Cheapest Insertion
    - Farthest Insertion
    - Nearest Insertion
    - Arbitrary Insertion

## Explanation of terms

A heuristic aims to generate high quality solutions but cannot guarantee to find the optimal solution.

A construction heuristic is a type of heuristic defined by Kahng and Reda (2004) as an alternative to an exact solution that performs a sequence of operations until a valid tour is obtained, at which point the heuristic stops and reports the constructed tour. 

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
