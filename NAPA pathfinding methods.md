---
title: NAPA pathfinding methods
created: '2021-07-06T06:28:12.339Z'
modified: '2021-07-06T10:13:49.805Z'
---

# NAPA pathfinding methods

- The pathfinding algorithm is a modified A* that calculates the shortest distance using a grid made for a particular voyage
- The heuristic used in the algorithm is the haversine distance between the vessel and its destination
- Grid is constructed either with static speed (alternative route with constant speed) or static course (shortest route with variable speed) in mind. 
- Grid is either static or dynamic. The dynamic grid is constructed so that the variables in the previous node affect the following nodes. Isochrone method is one example of a dynamic grid. It can be modified to account for minimum fuel cost by adjusting engine revolutions to the ETA. 
- Some grid construction methods are developed that account for variable time and course. These dramatically increase the computational time and is not viable for real users. Moreover paradoxically more complex calculations can lead to more uncertain results. Thus the 
- Each grid waypoint contains information on its position and metocean (meteorological/oceanographical) and operational conditions in the given point.
- The ship captain should first make a preliminary route for the ship and estimate the time of arrival. After this the optimization algorithm calculates potential sailing are from this.
- Course optimization grid relies on calculating the alternative waypoints by having them be perpendicular to the shortest route. 
- The amount of waypoints grows exponentially as the voyage increases. Some pruning is needed to get rid of badly performing waypoints.
- Course optimized routes tend to perform relatively well. However there is a chance that they will perform much worse than a great circle route.


