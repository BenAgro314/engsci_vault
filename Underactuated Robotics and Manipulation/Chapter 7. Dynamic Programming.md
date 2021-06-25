TARGET DECK: Main Deck

What is optimal control? #fc 
A control design process that uses optimization. The fundamental idea in optimal control is to formulate the goal of control as the  long term optimization of a scalar cost function.
<!--ID: 1621463355063-->


What is the double-integrator system (it's dynamical equations)? #fc 
$$\ddot{q} = u, \; |u| < c$$ for some constant $c$
<!--ID: 1621463355083-->


Typical state quadratic cost forumation (on $\mathbf x$) #fc
$$\int \mathbf x^T(t) \mathbf Q \mathbf x(t) \; dt$$
where $\mathbf Q$ is positive definite.
<!--ID: 1621463355089-->


Typical effort quadratic cost formulation (on $\mathbf u$) #fc
$$\int \mathbf u^T(t) \mathbf R \mathbf u(t) \; dt$$
where $\mathbf R$ is positive definite.
<!--ID: 1621463355093-->


Bang-bang control policy for time minimization of the double integrator #fc 
Maximal control input until a critical point, then breaking until target is reached.
<!--ID: 1621463355096-->


General form of additive cost for an instantaneous cost function $l()$ #fc 
$$\int_0^T l(x(t), u(t))\, dt$$
<!--ID: 1621463355099-->


What is a finite and infinite horizon problem #fc 
For an additive cost problem
$$\int_0^T l(x(t), u(t))\, dt$$
If $T=\infty$, then this is an infinite horizon problem. Else, it is a finite horizon problem.
<!--ID: 1621463355101-->


The graph search formulation of optimal control #fc 
A set of states $s_1, s_2, ...$ (nodes) and actions $a_1, a_2, ...$ (edges) governed by the dynamics:
$$s[n+1] = f(s[n], a[n])$$
$l(s,a)$ denotes the cost of taking action $a$ in state $s$. 
<!--ID: 1621463355104-->



What is the *cost to go* in dynamic programming (thing of this in the context of optimal control as graph search) #fc
The cost that will be acumulated in running the controller from the current state to the goal. We can find the shortest path by recursively solving for the optimal cost to go (the cost to go of the optimal controller).
<!--ID: 1621463355106-->


What is the **Value iteration algorithm** and its convergence properties. How do you extract the optimal control policy from this? #fc 
$$\hat{J}^*(s_i) \impliedby \text{min}_{a \in A} [l(s_i, a) + \hat{J}^*(f(s_i, a))]$$
This is guarentied to converge to the optimal cost to go plus some constant factor. If the graph has a goal state with zero-cost self transition then this cost function represents the weighted shortest distance to the goal. The optimal control policy is 
$$\pi^*(s_i) = \text{argmin}_a\left[l(s_i, a) + J^*(f(s_i, a))\right]$$
<!--ID: 1621463355108-->


Which equations, if satisfied, have $J^*$ and $\pi^*$  as optimal cost to go and controller repectively? #fc 
The *Hamilton-Jacobi-Bellman* (HJB) equation:
$$0 = \min_u \left[ l(\mathbf x, \mathbf u) + \frac{\partial J^*}{\partial \mathbf x} f(\mathbf x, \mathbf u) \right]$$ 
$$\pi^*(\mathbf x) = \text{argmin}_{u} \left[ l(\mathbf x, \mathbf u) + \frac{\partial J^*}{\partial \mathbf x} f(\mathbf x, \mathbf u)\right]$$
Here $\dot{ \mathbf x} = f$ and $l$ is the instantaneous cost function. 
<!--ID: 1621463355112-->



What is the sufficieny theorem? #fc 
Consider a system $\dot{\mathbf x} = f(\mathbf x, \mathbf u)$ and an infinite horizon additive cost $\int_0^T l(\mathbf x, \mathbf u) \, dt$, with $f$ and $l$ continuous functions, and $l$ a strictly positive definite function that obtains zero only when $x = \mathbf x^*$. Suppose $J(\mathbf x)$ is a positive definite solution to the HJB equation:
$$0 = \min_u \left[ l(\mathbf x, \mathbf u) + \frac{\partial J^*}{\partial \mathbf x} f(\mathbf x, \mathbf u) \right], \quad \forall \; \mathbf x$$ 
and that $\pi (\mathbf x)$ is the minimizer for all $\mathbf x$. Then, under some technical conditions on the existance and boundedness of solutions, we have that $J(\mathbf x) - J(\mathbf x^*)$ is the optimal cost to go and $\pi$ is an optimal policy. 
<!--ID: 1621463355114-->


Derivative of: vector by scalar, scalar by (column) vector, and vector by vector. #fc 
Vector by scalar: take the derivative of each component.
Scalar by (column) vector: take the partial derivative with repect to each vector componenet and arrange in a row vector. (transpose of the gradient of the scalar with respect to the vector)
Vector by vector: Jacobian matrix
<!--ID: 1621463355117-->


What is a markov decision process #fc 
At each time step, the process is in some state $s$, and the decision maker may choose any action $a$ that is available in state $s$. The process responds at the next time step by randomly moving into a new state $s'$, and giving the decision maker a corresponding reward/incuring a specified cost.
<!--ID: 1621463355119-->


Value iteration algorithm for a markov decision process (MDP) #fc 
$$\hat{J}(s) \impliedby \min_a \left[ l(s,a) + \sum_{s'} Pr(s'|s,a)\hat{J}(s')\right]$$
<!--ID: 1621463355121-->


