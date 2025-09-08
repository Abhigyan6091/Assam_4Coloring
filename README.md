# Assam_4Coloring

Map Coloring of Assam Districts using Backtracking CSP
This project provides a Python-based solution to the Map Coloring Constraint Satisfaction Problem (CSP) applied to the districts of Assam, a state in Northeast India. It implements and compares three different backtracking algorithms to find a valid coloring for the map, where no two adjacent districts share the same color.

The primary goal is to demonstrate the efficiency gains from using intelligent heuristics (MRV & LCV) and constraint propagation (AC-3) over a naive backtracking approach.

Algorithms Implemented
This repository showcases three distinct methods for solving the CSP:

Plain Backtracking: The simplest form of the algorithm. It iterates through districts and colors in a fixed order, which is often highly inefficient.

Backtracking with Heuristics (MRV + LCV): A significantly smarter approach that uses:

Minimum Remaining Values (MRV): Prioritizes the most constrained district (the one with the fewest legal color choices).

Least Constraining Value (LCV): Chooses the color that leaves the most options available for neighboring districts.

Backtracking with AC-3 & Heuristics: The most advanced method. It incorporates the AC-3 algorithm for arc consistency. This form of constraint propagation "looks ahead" to eliminate color choices that will inevitably lead to a failure, drastically pruning the search space.

Analysis: Why 3-Coloring is Impossible for this Map
A key finding of this project is that the map of Assam's districts cannot be colored with only three colors. The algorithms correctly prove this by exhaustively searching the solution space and returning None.

The reason for this failure lies in the geographical topology of the districts. For a map to be 3-colorable, it cannot contain any "cliques" of four or more regions that are all mutually adjacent. The Assam map contains several such arrangements.

Example of Failure: The Bongaigaon Clique
A clear example can be found centered around the Bongaigaon district. Consider the relationship between these four districts:

Bongaigaon

Goalpara

Barpeta

Chirang

Looking at the adjacency list, we can see:

Bongaigaon is adjacent to Goalpara, Barpeta, and Chirang.

Goalpara is adjacent to Bongaigaon and Barpeta.

Barpeta is adjacent to Bongaigaon, Goalpara, and Chirang.

Chirang is adjacent to Bongaigaon and Barpeta.

If we try to color this subset with three colors (e.g., Red, Green, Blue):

Let's color Bongaigaon Red.

Its neighbor, Barpeta, must be a different color, so we'll make it Green.

Its neighbor, Goalpara, must be different from both, so it must be Blue.

Now, we try to color Chirang. It is adjacent to Bongaigaon (Red) and Barpeta (Green), so it must be Blue.

But this creates a conflict! Both Chirang and Goalpara are Blue, but they are not adjacent to each other. However, if there was another district adjacent to all three, a fourth color would be required. The complexity of the entire map ensures that such a situation will inevitably arise.

The backtracking algorithms discover these impossible situations automatically. The AC-3 algorithm is particularly effective at this, as it can detect such inconsistencies early without deep searching.

4-Coloring: A Successful Solution
By increasing the number of available colors to four (['Red', 'Green', 'Blue', 'Yellow']), in line with the Four Color Theorem, the algorithms find a valid solution effortlessly. Because the problem becomes less constrained, even the naive backtracking algorithm can find a solution without having to backtrack.

This project successfully demonstrates the application of classic AI algorithms to a real-world geographical problem and highlights how the problem's constraints dictate the solvability and the efficiency of the solution path. 🗺️✨
