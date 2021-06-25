TARGET DECK: Main Deck

What is the RRT algorithm #fc 
RRT: Rapidly exploring random tree:
start with a point in the configuration space, $q_0$, and a goal region $\mathcal G$. Randomly sample a new point in the configuration space, and connect that point with an edge to the nearest point on the existing tree, if that connection and the randomly sampled point are within valid parts of the configuration space. Repeat until goal is reached, then find shortest path along the tree. Most implementations also include a maximum distance between the sampled point and the closest point, limiting the growth rate of the tree. This algorithm is inherently more likely to grow towards unsearched areas of the configuration space
<!--ID: 1621463355123-->


What is a Voronoi region? #fc 
Each existing node in the RRT has a *voroni region*. If a new node is sampled in this region, the node associated with this region will be connected to the new node. 
<!--ID: 1621463355125-->


