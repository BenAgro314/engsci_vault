TARGET DECK: Main Deck

What is a trajectory? #fc 
$x(t), u(t)$ defined on an interval of time, with some initial condition $x_0$
<!--ID: 1622546833955-->

For an instantanous cost, $l(x, u)$, what is the cost formulation for a trajectory from the initial condition $x(t_0) = x_0$ to the final condition $x_f = x(t_f)$? #fc 
$$J_u(x_0) = l_f(x(t_f)) + \int_{t_0}^{f_f} l(x(t), u(t))\, dt $$
<!--ID: 1622546992313-->

What is the optimization problem in trajectory optmization with dynamics $\dot{x} = f(x(t), u(t)$ and instantaneous cost function $l$. (hint: one minimization of a cost, one constraint on $\dot{x}$, and one constraint on $x(t_0)$) #fc 
$$\min_{u(.)} \quad l_f(x(t_f)) + \int_{t_0}^{f_f} l(x(t), u(t))\, dt $$
subject to $\dot{x}(t) = f(x(t), u(t))$ and $x(t_0) = x_0$ for all $t \in [t_0, t_f]$. 
<!--ID: 1622547194713-->

What are some additional constraints one might add to a trajectory optimzation problem? #fc 
Collision avoidance and input limits $u \in [u_{min}, u_{max}]$
<!--ID: 1622547251762-->

"Direct transcription" of the problem
$$\min_{u(.)} \quad l_f(x(t_f)) + \int_{t_0}^{f_f} l(x(t), u(t))\, dt $$
subject to $\dot{x}(t) = f(x(t), u(t))$ and $x(t_0) = x_0$ for all $t \in [t_0, t_f]$. 
to a mathematical program, with linear dynamics $x[n+1] = Ax[n] + Bu[n]$ #fc 
Note that both $u$ and $x$ are decision variables, but $x$ has the explicit dynamics constraint applied to it:
$$\min_{u[.], x[.]} l_f(x[N])  + \sum_{n_0}^{N-1} l(x[n], u[n])$$
subject to 
$$x[n+1] = Ax[n] + Bu[n]$$
$$x[0] = x_0$$
for all $x \in [0, N-1]$ + any additional constraints 
<!--ID: 1622547637463-->

What is direct shooting trajectory optimization, and how is it different from direct transcription? #fc 
Direct shooting does not have decision variables $x[.]$, and instead implicitly represents the dynamical constraints with:
$$x[n] = A^nx[0] + \sum_{k=0}^{n-1} A^{n-1-k}Bu[k]$$
<!--ID: 1622548127239-->

Which option is better direct transcription or direct shooting? #fc 
Trick question, neither is uniformly better than the other.
<!--ID: 1622548664167-->


Which formulation is easier to add state constraints to, direct transcription or direct shooting? #fc 
Direct transcription
<!--ID: 1622548664249-->


Which formulation is easier to parralelize, direct transcription or direct shooting? #fc 
Direct transcription
<!--ID: 1622548664252-->


What is a zero-order hold? #fc 
When a (control) input or variable is held constant over a time period
<!--ID: 1622549162814-->


Is collision avoidance a convex constraint? #fc 
No, it is fundamentally non-convex 
<!--ID: 1622549162858-->


Direct transcription with non-linear dynamics #fc
$$\min_{u[.], x[.]} l_f(x[N])  + \sum_{n_0}^{N-1} l(x[n], u[n])$$
subject to 
$$x[n+1] = f(x[n], u[n])$$
$$x[0] = x_0$$
for all $x \in [0, N-1]$ + any additional constraints 
<!--ID: 1622549162863-->


Update step on $x[n+1]$ for continous time with (in general) non-linear dynamics #fc 
$$x[n+1] = x[n] + \int_{t[n]}^{t[n+1]} f(x(t), u(t)) \, dt, \quad x(t[n]) = x[n]$$
<!--ID: 1622549162868-->

When using the decision variables $x[\cdot], u[\cdot]$ for continuous time scenarios with numerical integration, what changes to the optimization problem might you make to remidy the fact that the time step for the numerical integration method is variable? #fc 
We might make $t[\cdot]$ as decision variables, which is particularly useful if you do not know the duration of the trajectory apriori.
<!--ID: 1622550118890-->


What is the latex command for a lone dot: $\cdot$ #fc 
\cdot
<!--ID: 1622550118926-->


In direct collocation, how are $x(t)$ and $u(t)$ represented (functionally) #fc 
As peicewise polynomials
<!--ID: 1622550118930-->


What is the "sweet spot" for the degrees of $x(t)$ and $u(t)$ as piecewise polynomials in direct collocation #fc
$x(t)$: cubic
$u(t)$: first-order polynomial (linear)
<!--ID: 1622550118933-->


Why is  $x(t)$: cubic and $u(t)$: first-order polynomial (linear) the sweet spot in direct collocation (hint: what are the decision variables?) #fc 
The decision variables are just the sample values of $u$ and $x$ at the break points in the spline. 
<!--ID: 1622550118935-->


In direct collocation at the sweet spot, why can we just use $u$ and $x$ at the break points as decision variables? #fc 
$u$ is linear, so it is fully defined. Using $u$, we can find $\dot{x}$ at the break points. With $x$ and $\dot{x}$ defined at the break points, then the cubic spline in $x$ is fully defined on each time interval
<!--ID: 1622550118938-->


What are collocation points and why are they nessecary ? #fc 
Points (usually chosen to be the midpoints of the interval between break points in the spline) where a derivative constraint is added to $x$ that enforces the dynamics, i.e at the collocation times $t_{c,n}$ we add the constraint: $\dot{x}(t_{c,n}) = f(x(t_{c,n}), u(t_{c,n}))$
<!--ID: 1622554257864-->


How are trajectories represnted in "pseudo-spectral" optimal control? #fc 
As a linear combination of global polynomials.
<!--ID: 1622554257904-->


What does SQP stand for in the domain of mathematical programming? #fc 
Sequential quadratic programming
<!--ID: 1622554257910-->


What is sequential quadratic programming? #fc 
A method for solving non-linear programming problems where a local quadratic approximation is made, and the solve jumps to its minima (on each iteration). 
<!--ID: 1622554257914-->


For the general formulation of a non-linear program: 
$$\min_z c(z) \quad \text{subject to} \quad \phi(t) \le 0$$
what are the names of $c$, $z$ and $\phi$? #fc 
$z$ is a vector of the decision variables, $c$ is a scalar objective (cost) function, and $\phi$ is a vector of constraints.
<!--ID: 1622554257918-->

What is an open-loop controller and a closed-loop controller? #fc 
open-loop: does not use feedback from the system state to obtain the next control output (pre-planned)
closed-loop: uses feedback from the system state to obtain the next control output
<!--ID: 1622554601089-->


What is model-predictive control (MPC) (4 steps)? #fc 
Use trajectory optimizations as a feeback policy: 
1. measure current state
2. optimize a trajectory from the current state
3. execute the first action from the known optmized trajectory
4. let the dynamics evolve, and repeat
<!--ID: 1622554601121-->

What is receding horizon MPC? #fc 
With a horizon is longer than $N$ steps, we can optimize a trajectory over the next $N$ steps, and then step forward and repeat. 
<!--ID: 1622558917964-->


How can we guarentee recursive feasibility of receding horizon MPC? #fc 
Set a constraint that the $x$ value at time step $N$ must be a fixed point $x^*$.
<!--ID: 1622558917995-->


What is the method of lagrange multipliers? We want to find the minimum of a function $f(x) = 0$ subject to the constraint $g(x) = 0$ #fc 
A strategy for finding the local minima and maxima of a function subject to equality constraints. Define
$$\mathcal L(x, \lambda) = f(x) - \lambda g(x)$$
and find the stationary points of $\mathcal L$, considered as a function of $x$ and the lagrange multiplier $\lambda$. The solution of the original problem is always a saddle point of the lagrangian function. 
<!--ID: 1622558918000-->


For a system with dynamics $\dot{x} = f(x, u)$, and we design some \_\_\_\_\_ \_\_\_\_\_\_\_ (\_\_\_\_\_ \_\_\_\_\_) 
$$ z(t) = h(x, u, \frac{d u}{d t}, ... \frac{d^k u }{d t^k})$$
such that we can write $x$ and $u$ purely as a function of $z$ and it's time derivatives, then we say that the system $f$ is \_\_\_\_\_ \_\_\_\_ in the outputs $z$. #fc 
output coordinates (task space),
differentially flat
<!--ID: 1622558918005-->

What is the singular value decomposition of a matrix $A \in m \times n$? #fc
$A$ can be written in the form:
$$A = UDV^T $$
where $U^TU = I$ and $V^TV = I$ and $D$ has entries only along the diagonal. 
<!--ID: 1622804892032-->



What are the singlar values of a matrix $A$? #fc
The values along the diagonal of the matrix $D$ in the singular value decomposition:
$$A = UDV^T$$
<!--ID: 1622804892063-->


How is the condition number calculated for a matrix? #fc 
The ratio of the smallest to largest singular value in the singular value decomposition of a matrix. 
<!--ID: 1622804892066-->


What does the condition number, $C$, of a matrix mean for precision? #fc 
The base $b$ logarithm of $C$ is the estimate of how many base-$b$ digits are lost in solving a linear system with that matrix. In other words, it estimates the worse case loss in precision. For a matrix $A$ the condition number $cond(A)$ is defined as the ratio between the largest and the smallest singular values. When solving a linear system $Ax=b$, the larger the condition number, the more sensitive is the solution $x=A^{−1}b$ to small perturbations of the vector b. Hence, if $cond(A)$ is large, tiny numeric roundings in b can be hugely amplified when solving for $x$.
<!--ID: 1622804892069-->

Numpy function to get the norm of a vector? #fc 
np.linalg.norm()
<!--ID: 1622809529257-->


Numpy function to invert a matrix? #fc 
np.linalg.inv()
<!--ID: 1622809529338-->

Derivative of $x^T \mathbf B$ wrt $x$: #fc 
$\mathbf B$
<!--ID: 1622816771063-->


Derivative of $x^T \mathbf b$ wrt $x$: #fc 
$\mathbf B$
<!--ID: 1622816771125-->


derivative of $\mathbf B x$ wrt $x$: #fc 
$\mathbf B$
<!--ID: 1622816771128-->


Derivative of $x^T \mathbf B x$ wrt $x$: #fc 
$2\mathbf B  x$
<!--ID: 1622816771131-->











