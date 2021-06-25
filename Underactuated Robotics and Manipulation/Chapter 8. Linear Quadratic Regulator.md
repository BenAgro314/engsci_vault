TARGET DECK: Main Deck

Linear quadratic regulator dynamics and cost function  #fc 
Linear dynamics:
$$\dot{x} = Ax + Bu$$
with a cost function
$$l(x,u) = x^TQx + u^TRu$$
Where R is positive definite and Q is positive semi-definite.
<!--ID: 1621612006256-->


Form of the cost to go for LQR #fc 
$$J = x^TSx$$
<!--ID: 1621612006288-->


Optimal control policy ($u$) for LQR #fc 
$$u = -Kx$$ where $$K = R^{-1} B^T S$$
<!--ID: 1621612006292-->


Name (and the equation, bonus) of the equation for finding $S$ #fc 
The algebraic riccati equation:
$$0 = SA + A^TS - SBR^{-1}B^TS + Q$$
<!--ID: 1621612006295-->


Qualitative interpretation of the optimal controller $u = R^{-1}B^TSx$ #fc 
$-Sx$ is in the direction of the steepest descent down the value function. $-B^TSx$ represents the projection of the steepest descent onto the control space: it is the steepest acheivable descent with the control inputs $u$. Finally, the prescaling by $R^{-1}$ biases the direction of the descent to account for the relative weightings on the different control inputs. 
<!--ID: 1621612006298-->


How can LQR be used to stabilize non-linear systems: $\dot{x} = f(x,u)$ #fc 
Choose a fixed point to stabilize about $(x_0, u_0)$ with $f(x_0, u_0) = 0$. 
Define the relative coordinate system:
$\bar{x} = x - x_0$ and $\bar{u} = u = u_0$. We can approximate
$$\dot{\bar{x}} \approx f(x_0, u_0) + \frac{\partial f(x_0, u_0)}{\partial x}(x-x_0) + \frac{\partial f(x_0, u_0)}{\partial u}(u - u_0) = A\bar{x} + B\bar{u}$$
Defining a quadratic cost function in these error coordinates, and solving as before, we find that the optimal control is of the form
$$u^* = u_0 - K(x - x_0)$$
<!--ID: 1621612006301-->


Formulation of finite horizon LQR #fc 
Linear dynamics: $\dot{x} = Ax + Bu$
Finite horizon cost:
$$J = h(x(t_f)) + \int_0^{t_f} l(x(t), u(t))dt$$
where
$$h(x) = x^TQ_fx$$
$$l = x^TQx + u^TRu$$
where all $Q$'s are positive definite and $R$ is positive semi-definite 
<!--ID: 1621612006303-->


Control policy of finite horizon LQR #fc 
Substituting the cost function and dyamics into the HJB equation, we find that:
$$0 = \min_u\left[x^TQx + u^TRu + \frac{\partial J^*}{\partial x}(Ax + Bu) + \frac{\partial J^*}{\partial t}\right]$$
and taking the derivativewe find the optimal control policy is
$$u^* = \frac{-1}{2}R^{-1} B^T\frac{\partial J^*}{\partial x}^T$$
<!--ID: 1621612006306-->



Cost-to-go function form for finite horizon LQR, and the resulting equation for the unknown matrix (and its name) #fc 
Guess
$$J^*(x,t) = x^TSx$$
where $S$ is positive definite. 
This yields the continuous time differential Riccati equations:
$$-\dot{S}(t) = S(t)A + A^TS(t) - S(t) BR^{-1} B^TS(t) + Q$$
after subsituting $J$ and the optimal control policy $u$ into the finite horizon HJB equation.
<!--ID: 1621612006308-->


Local trajectory stabilization for nonlinear systems using LQR #fc 
Assume we have a nominal trajectory $x_0(t), \; u_0(t)$ defined for $[t_1, t_2]$. We define a local coordiante system
$$\bar{x}(t) = x(t) - x_0(t)$$ and $$\bar{u}(t) = u(t) - u_0(t)$$
Then 
$$\dot{\bar{x}} =\dot{x} - \dot{x}_0 = f(x,u) - f(x_0, u_0)$$
This can then be approximated with a first order taylor expansion to:
$$\dot{\bar{x}} = A(t)\bar{x} + B(t)\bar{u}$$
We can define a quadratic cost function in the error coordinates, and stabilize using LQR. Because the coorindate system is moving along the trajectoy, the linearization is valid everywhere along the trajectory. The resulting controller takes the form
$$u^* = u_0(t) - K(t) (x - x_0(t))$$
<!--ID: 1621612006310-->


Problem statement of linear quadratic optimal tracking #fc 
$$\dot{x} = Ax+ Bu$$
$$h(x) = (x - x_d(t_f))^T Q_f (x - x_d(t_f))$$
$$l(x, u, t) = (x - x_d(t))^T Q(x - x_d(t)) + (u - u_d(t))^TR(u-u_d(t))$$
where $Q$ and $Q_f$ are positive semi-definite and $R$ is positive definite. 
<!--ID: 1621612006312-->


Form of cost to go for linear quadratic optimal tracking, and the steps to solve the problem #fc 
$$J^*(x,t) = x^TS_{xx}x + 2x^Ts_x(t)  + s_0(t)$$
Substitute this into the HJB equation, and integrate backwards from the final conditions to find the equations for $S_{xx}$, $s_x$ and $s_0$. 
<!--ID: 1621612006315-->


Derivation of the discrete time riccati equations #fc 
Dynamics:
$$x[n+1] = Ax[n] + Bu[n]$$
and we want to minimize:
$$\min \sum_{n=0}^{N-1} x^TQx + u^TRu$$
The cost to go is given by the bellman equation
$$J(x, n-1) = \min_u \left[ x^TQx + u^TRu + J(Ax + Bu, n)\right]$$
Guessing $$J(x,n) = x^TS[n]x$$, we can find $$u^*[n] = -K[n]x[n]$$ 
where $K$ is a matrix in terms of $R$, $B$, and $S$, and $S$ is given by the riccati difference equation 
<!--ID: 1621612006319-->
