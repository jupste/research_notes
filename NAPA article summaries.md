---
title: NAPA article summaries
created: '2021-07-08T08:05:07.122Z'
modified: '2021-07-08T08:06:45.766Z'
---

# NAPA article summaries

### Near-Optimal Weather Routing by Using Improved A* Algorithm


- Belman-Ford, Dikstra, A* (haversine based heuristic)
- Grid mapping, 
- eXtreme Gradient Boosting (XGB) regression model was used to predict the SOG
- Feature selection based on Variance Inflation Factor (to drop highly correlated features)


### Effectiveness of 2D optimization algorithms considering voluntary speed reduction under uncertain metocean conditions

- Two-dimensional voyage optimization algorithms can be generally divided into static grid-based (predefined grid) methods and dynamic grid-based (changing grid at various timestamps) methods
- metacean forecasts highly unpredictable and optimizing based on them is hard
- Waypoints include geographical and temporal information
- To reduce number of potential waypoints, algorithm assumes either fixed speed or fixed course
- Number of sub-routes increase exponentially the longer the voyage. Thus the key is to eliminate badly performed sub-routes before execution.
- Pathing using either speed or course optimization (course optimization produces shorter routes which normally means less uncertainty however speed optimization is better at avoiding possible storms). 
- Nodes are waypoints, edges are paths between these and contain metocean conditions, operational conditions and sailing constraints
- Weather uncertainty is taken into account by calculating a scatter on the forecast model by varying the initial environmental inputs into the metocean forecast models.


### On the uncertainties of the weather routing and support system against dangerous conditions

- Transatlantic voyage ~10 days, transpacific ~14 days
- Optimization algorithm can produce fuel-efficient but unreliable paths and to prevent this some limits must be put in place

### Analysis of voyage optimization benefits for different shipping stakeholders
- The faster the ships speed, the shorter the interval for sending dynamic AIS messages. Static AIS messages are send every 6 minutes or on request. Changing the course also makes messages more frequent
-  AIS-data filtering: end of voyage detection, filter out bad data, identify loading conditions and time spend at anchorage, estimate payload 
- Voyages shorter than 1 day have little room for optimization
-  NAPA Voyage Optimization route library
- Ship draught needs to be determined based on ship movements (e.g. oil tanker visits a port in Saudi Arabia it will most likely exit with full load)
- Anchoring areas are determined by  either using available data or finding a large concentration of ships that are stationary


### A Three-Dimensional Dijkstra’s algorithm for multi-objective ship voyage optimization

- Limiting shipping path optimization on either speed or course optimization constrains the problem to a 2d search problem.
- Simplifying the problem to 2d search can cause the solution to be only a local optima based on the available parameters
- By extending the search to 3d we can find the smallest of all the optimas
- 3d search is enabled by combining Dijkstra with a genetic algorithm
- Algorithm uses waypoints and operational conditions and weather conditions in those waypoints to describe the graph (for example U(P_1) describes the operational conditions at the first waypoint)
- Graph G(P,A) where P are the waypoints and A are the edges
- Path is constructed that follows the great circle route (shortest route). Then at each waypoint perpendicular to each waypoint in this route.
- Constructing the graph takes about 4 minutes on normal desktop while implementation of the Dijkstra algorithm only takes a few seconds.
- On the Atlantic eastbound voyages are more straightforward. Westbound voyages benefit more from optimization
-  This is because in the North Atlantic storms always move from west to east
- 3D Dijkstra routes tend to be along the great circle while 2D Dijkstra routes tend to be longer
- Most times calculation of graph nodes is not possible using parallization since the waypoints depend on the previous entries


### Uncertainty in marine weather routing
- Another route modelling approach has involved generating candidate routes using biased Rapidly exploring Random Trees which solve for the minimum energy path using the A* algorithm
- Polynasian canoe seafaring some sort of benchmark of uncertainty, which this paper uses as a case study

