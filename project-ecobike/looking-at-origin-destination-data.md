---
title: "Looking at Origin-Destination data"
usemathjax: true
---


When looking at origin-destination (OD) data, we can start looking at how the Ecobici network functions in general. Just as a reminder, we'll consider origin-destination data as the aggregate of all trips, moving across geographic space, flowing from an **origin** (O) to a **destination** (D). Given trips actually start or end at a given station, this is a reasonable representation of how people flow through the Ecobici network.  

Given the limitations that we have on our dataset, we won't be considering the paths that each traveller takes to get to their destination (since we don't have that information at hand). We'll also only be looking at an individual time period (in the meantime - in the future, I might be interested at analyzing this considering stationality, whether by month or by day of week).

## Prelude: considerations to have in mind when looking at OD data

To represent the origin-destination data, we'll be looking at it as a weighted directed adjacency matrix. For context, it basically means the following:

1. **Adjacency matrix**: we'll represent each possible origin-destination trip with a matrix $X$, where each entry $$x_{(i,j)} \in X$$ will represent each (origin, destination) pair.
2. **Weighted**: each entry $`x_{(i,j)} \in X`$ will have a value equal to the total number of trips that happened in the dataset. More frequently transited routes will have a higher importance than less frequently transited ones.  
3. **Directed**: since we noticed [previously](a-first-glance.md#comments) that the inflow at each station is quite different than the outflow, we'll want to take that into consideration. This basically means that the matrix $X$ will not be symmetric (meaning the entry $`x_{(i,j)} \neq x_{(j,i)}`$)

Having all this in mind, then we'll be able to leverage network analysis tools to answer several questions, like the following:

1. Which stations are most influential based on their number of connections?
2. Which stations best bridge between other stations?
3. How strongly can a station influence the total traffic through Ecobici?

## A look at centrality scores

Let's now try and tackle this by looking at how "central" every station in the Ecobici network can be. Below you'll find seven different centrality measures for the Ecobici network:

![Ecobici Centrality Measures](/assets/images/centralities_map.png)

Take your time looking at each centrality measure in detail.

At a quick glance, we can notice the following:

- In general, stations near the geographic centroid of the stations tend to be also more central to the network (which is to be expected, given how they're placed).
- There are several regions that fall somewhat outside of this geographic centroid that are also very important to the network. In particular, two main patterns arise (though you may notice some others):
  
  - There's a line of stations going from north to south that scores relatively high. This line is near Insurgentes (one of the main streets in Mexico City), which also has a bike lane.
  - In the northeastern coverage area, several centrality metrics score highly (in-degree, out-degree, eigenvector, Katz centralities). These are all near Buenavista (which, if you'll [recall](a-first-glance.md#comments), was the busiest station in the full network), which makes sense, given just how many people move through that particular station.
