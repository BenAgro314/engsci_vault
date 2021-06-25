TARGET DECK: Main Deck

Basic (continuous and discrete) differential equations governing a stocastic system #fc 
$$\dot{\mathbf x(t)} = f(\mathbf x(t), \mathbf u(t), \mathbf w(t))$$
or
$$\mathbf x[n+1] = \mathbf f(\mathbf x[n], \mathbf u[n], \mathbf w[n])$$
Where the input $\mathbf w$ is from some random process. 
<!--ID: 1621165381916-->


Additive noise formulation for a discrete stocastic system #fc 
$$\mathbf x[n+1] = \mathbf f(\mathbf x[n], \mathbf u[n]) + \mathbf w[n]$$
<!--ID: 1621165381948-->


Zero-mean gaussian white noise process #fc 
$$\forall n, \; E[w[n]] = 0, \; E[w[i]w[j]] = \delta_{ij}\sigma^2$$
where $\delta_{ij}$ is the kronecker delta. 
<!--ID: 1621165381951-->



Master equation for **continuous-state Markov process** #fc 
$$p_{n+1}(x) = \int_{-\infty}^{\infty} p(x|x') p(x') dx'$$
Where $p_n{x}$ is the probability density function for $x$ at time step $n$, and $x'$ is the x value at the previous time step. 
For multivariate distributions:
$$ p_{n+1}(\mathbf x) = \int_{\mathcal X} p(\mathbf x| \mathbf x', \mathbf u ) p_n(\mathbf x')d\mathbf x'$$
<!--ID: 1621165381954-->


What is a **stationary distribution**? #fc 
The probability distrubtion that the state of a system converges to.
<!--ID: 1621165381956-->



Gaussian distribution with mean $\mu$ and standard deviation $\sigma$ #fc 
$$ f(x) = \frac{1}{\sqrt{2\pi\sigma^2}}e^{\frac{-(x-\mu)^2}{2\sigma^2}}$$
<!--ID: 1621165381959-->


