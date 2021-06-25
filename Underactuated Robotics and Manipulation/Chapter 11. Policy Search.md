TARGET DECK: Main Deck

What is policy search? Consider a parameterized controller with decision variables, and we \_\_\_\_\_\_ over those variables in order to achive a \_\_\_\_\_\_ or \_\_\_\_\_ a preformance objective #fc 
search,
task,
optimize 
<!--ID: 1622822939257-->


In policy search, what is the general form of the control policy: $u = ?$ #fc
$$u = \pi_\alpha(x)$$
where $\alpha$ is a vector of parameters that describe the controller. 
<!--ID: 1622822939284-->


What do we want to minimize in policy each (hint: $E()$)? #fc 
$$\min_\alpha E_{x \in \mathcal X_0}[J_\alpha(x)]$$
where $\mathcal X_0$ is the set of possible initial conditions, and 
$$J_\alpha = \int_0^\infty l(x(t), u(t))\; dt$$
subject to 
$$\dot{x} = f(x,u), \quad u = \pi_\alpha(x), \quad x(0) = x$$
<!--ID: 1622822939287-->



