TARGET DECK: Main Deck

Lagrangian dynamics for a simple pendulum (with generalized force on RHS), and what that generalized force is modelled as under a control torque and a damping torque #fc 
$$ml^2\ddot{\theta}(t) + mgl\sin\theta{(t)} = Q = -b\dot{\theta}(t) + u(t)$$
<!--ID: 1620387616448-->


Five types of stability and their definitions #fc 
1. locally stable in the sense of Lyapunov (i.s.L): a fixed point $x^*$ is locally stable i.s.L if for every $\epsilon > 0$, I can produce a $\delta > 0$ such that if  $||x(0) -x^*|| < \delta$ then $\forall t \; ||x(t)-x^*|| < \epsilon$. 
2. locally attractive: if $x(0) = x^* + \epsilon$ implies that $\lim_{t \to \infty} x(t) = x^*$ i.e. the system is locally attractive if for every $\epsilon > 0$ there exists a $M > 0$ such that for all $t > M, \; ||x(t) - x^*|| > \epsilon$.
3. Locally asymptotically stable: if it is i.s.L and locally attractive. 
4. Locally exponentially stable:  if $x(0) = x^* + \epsilon$ implies that $||x(t) - x^*|| < Ce^{-\alpha t}$ for some positive constants $C$ and $\alpha$. 
5. Unstable: a fixed point is unstable if it is not locally stable i.s.L
<!--ID: 1620387616481-->

Define basin of attraction for locally attractive point $x^*$ #fc 
An interval of $x(0)$ such that it is attracted to $x^*$
<!--ID: 1620489303074-->


Define separatrix #fc 
The manifold separating two basins of attraction.
<!--ID: 1620489303087-->


Define bifrucation #fc 
When varying a parameter, bifrucation is the point at which the number of fixed points changes
<!--ID: 1620489303091-->


Define homoclinic orbit, and what is the holonomic orbit energy for a simple undamped pendulum #fc 
a trajectory of a flow of a dynamical system which joins a saddle equilibrium point to itself. More precisely, a homoclinic orbit lies in the intersection of the stable manifold and the unstable manifold of an equilibrium. $E_0 = mgl$
<!--ID: 1620489303095-->


Energy shaping controller for the (torque limited) simple pendulum #fc 
The total energy of the pendulum is $E  = \frac{1}{2}ml^2\dot{\theta}^2 -mgl\cos\theta$ and the rate of change of the energy is $\dot{E} = u\dot{\theta}$. Defining the desired energy $E_d = mgl$ and $\tilde{E} = E - E^d$ we find that $\dot{\tilde{E}} = u\dot{\theta}$. **Using the controller** $u = -k\dot{\theta}\tilde{E}, \; k > 0$, we find that $\dot{\tilde{E}} = -k\dot{\theta}^2\tilde{E}$ (this is the *error dynamics*). If there is damping in the system, account for this in the controller: $u = -k\dot{\theta}\tilde{E} + b\dot{\theta}$
<!--ID: 1620489303099-->


For the energy shaping controller, what type of equillbirum is the upwards pendulum orientation #fc 
Attractive, but not stable. Small purturbations may cause the system to drive all of the way around the circle in order to once again return to unstable equillibrium. 
<!--ID: 1620489303102-->

Derivative of a vector function $\mathbf f$ with respect to a vector $\mathbf q$ #fc 
It is the jacobian matrix of the coordinates of $\mathbf f$ over the coordinates of $\mathbf q$.
<!--ID: 1620752992534-->




