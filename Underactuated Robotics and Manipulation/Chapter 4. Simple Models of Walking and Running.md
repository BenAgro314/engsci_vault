TARGET DECK: Main Deck

Define **limit cycle** #fc 
A **limit cycle** is an periodic orbit that is a limit set of the dynamical system; they can be stable (the limit set of neighboring trajectories as time goes to infinity) or unstable (the limit set of neighboring trajectories as time goes to negative infinity). (a **limit set** is the state a dynamical system reaches after an infinite amount of time has passed). Alternatively: a **limit cycle** is a closed in phase space having the property that at least one other trajectory spirals into it either as time approaches infinity (stable) or as time approaches negative infinity (unstable).
<!--ID: 1620867965016-->

Define orbital stability #fc 
For every small $\epsilon >0$, we can find a $\delta > 0$ such that if $\text{min}_\tau ||\mathbf x(t_0) - \mathbf x ^*(\tau)|| < \delta$  then $\forall t, \; \text{min}_\tau ||\mathbf x(t) - \mathbf x ^*(\tau)||  < \epsilon$. Note that $$ \text{min}_\tau ||\mathbf x(t_0) - \mathbf x ^*(\tau)|| $$ is the minimum distance from the orbit. Intuitively this is saying: we can find a $\delta$ such that when the initial state $\mathbf x(t_0)$ is closer than $\delta$ to the orbit, for all time the state will be closer than some arbirary epsilon.
<!--ID: 1620910652741-->


What is an invarient set in a dynamical system #fc 
The largest set $\mathcal G$ such that $\mathbf x(0) \in \mathcal G \implies \forall t > 0 , \mathbf x(t) \in \mathcal G$. The largest invarient set need not be connected.
<!--ID: 1620910652773-->


If we find an invarient set in the state space that containes no fixed points, what must be true about this set? #fc 
It must contain a closed orbit. 
<!--ID: 1620910652777-->


Can a gradient potential field have closed orbit? #fc 
No. Neither can a lyapunov function that whoes derivative is negative semi-definite.
<!--ID: 1620910652779-->


What is a Poincare map? #fc 
Consider a dynamical system with $\dot{\mathbf x} = \mathbf f (\mathbf x),\; \mathbf x \in \mathbb R^n$. Define an $n-1$ dimensional *surface of section* $S$ that is transverse to the flow (all trajectories starting on $S$ flow through it, not parallel. The Poincare map is a mapping from $S$ to itself:
$$\mathbf x_p[n+1] = \mathbf P (\mathbf x_p[n])$$
where $\mathbf x_p[n]$ is the state of the system at the $n^{th}$ crossing of the surface of section. $t_c[n]$ is the return time. The return time for a fixed point on $S$ is defined to be zero. 
<!--ID: 1620910652783-->


If $\mathbf P(\mathbf x_p)$ exists for all $\mathbf x_p \in S$, and if there is a (stable or unstable) fixed point $\mathbf x_p^8$ on $\mathbf P$, what does that mean for a limit cylce? #fc 
There exists a unique periodic orbit $\mathbf x^*(t)$ which passes through $\mathbf x^*_p$ that is a (stable or unstable) limit cycle. (see staircase method)
<!--ID: 1620910652785-->


Exponential stability on a 1 dimensional Poincare map #fc 
The absolute value of slope at the fixed point is less than one (where $f$ crosses the line $y = x$). (recall staircase method)
<!--ID: 1620910652788-->


Staircase method for 1D Poincare map #fc 
Start on the line $y = x$. Got vertically to line of interest, then go horizontally to line $y = x$. Repeat. 
<!--ID: 1620910652791-->

What is a prismatic joint? #fc 
A prismatic joint provides a linear sliding movement between two bodies, and is often called a slider.
<!--ID: 1621165381971-->


