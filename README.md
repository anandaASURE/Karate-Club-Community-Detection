# Community Detection in Zachary's Karate Club
## ANANDA JANA | @ IISER TVM

This project finds hidden groups in a famous social network using spectral analysis. Think of it like automatically discovering friend circles in a club.

## What's This About?

Back in the 1970s, a karate club split into two groups after a conflict. This notebook uses math (specifically, eigenvalues and modularity) to automatically detect those groups without knowing the story beforehand.

## What It Does

* Takes the karate club network (34 people, their friendships)
* Uses Newman's algorithm to recursively split the network
* Finds communities by looking at connection patterns
* Tracks how important each person is during the splits
* Shows that the communities were already there (not created by the algorithm)

## The Algorithm

1. Build a "modularity matrix" from the network
2. Find the leading eigenvector (fancy math for "main pattern")
3. Split nodes based on positive/negative values
4. Only keep splits that improve modularity (make communities more distinct)
5. Repeat on each group until no good splits remain

## Files

* `community_detection.ipynb` – Main notebook with all the code and explanations

## What You Need

```bash
numpy
networkx
matplotlib
```

Just install them with:

```bash
pip install numpy networkx matplotlib
```

## How to Run

Open the notebook and run all cells. You'll see:
* Step-by-step splits of the network
* Graphs showing the communities forming
* Plots of how node importance stays stable (proof communities existed)

## Key Finding

The metrics (degree, betweenness, closeness, clustering) barely change as we split the network. This proves the algorithm *discovers* existing structure rather than creating artificial groups.

## Limitations

Sometimes the leading eigenvalue is positive (indicating a possible split), but the eigenvector has all entries with the same sign. In such cases, the sign-based rule fails to form two groups, creating one empty community — a known limitation of the basic spectral method.

## References

Based on Newman's 2006 paper on modularity and community structure. Uses the classic Zachary Karate Club dataset from 1977.

## Note

This is a learning project to understand community detection algorithms. The code prioritizes clarity over performance.
