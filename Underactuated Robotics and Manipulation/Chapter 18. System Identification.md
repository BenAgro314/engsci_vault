TARGET DECK: Main Deck

In system identification, what is the algorithm that uses **equation error**? #fc
Equation error minimized one step prediction error:
$$\min_{\alpha} \sum_{n= 0}^{N-2}||f_\alpha(\hat{x}_n, u_n) - \hat{x}_{n+1}||^2_2$$
where we have first estimated the state $\hat{x}_n$ given the input data $u_n, y_n$. **This is the sum of errors between adjacent steps**
<!--ID: 1623020822257-->


In system identification, what is the algorithm that uses **Simulation error**? #fc 
Simulation error captures long term prediction error:
$$\min_\alpha \sum_{n=1}^{N-1} ||x[n] - \hat{x}_n||^2_2$$
subject to
$$x[n+1] = f_\alpha(x[n], u_n), \; x[0] = \hat{x}_0$$
**This is the sum of the squared errors at every step**
<!--ID: 1623020822273-->

The manipulator equations are \_\_\_\_\_\_\_ in the \_\_\_\_\_\_\_ parameters. #fc 
Affine, 
lumped parameters 
<!--ID: 1623022524633-->


What does it mean for the manipulator equations to be affine in the lumped parameters (also state the manipulator equations)? #fc 
The manipulator equations:
$$ M(q) \ddot{q} + C(q, \dot{q})\dot{q} = \tau_g(q) + Bu$$
can be factored into the form:
$$W(q, \dot{q}, \ddot{q}, u)\alpha_l(\alpha) + w_0(q, \dot{q}, \ddot{q}, u) = 0$$
where $\alpha_l$ is a vector of lumped parameters, and $W$ is sometimes reffered to as the data matrix.
<!--ID: 1623022524675-->


What are we trying to optimize in choosing trajectories for system identification (think about the lumped parameter parameterization: $W \alpha_l + w_0 = 0$? #fc
We want a numerically well conditioned least squares optimization problem, which can be achieved by trying to minimize the condition number of $W$. 
<!--ID: 1623022524680-->



