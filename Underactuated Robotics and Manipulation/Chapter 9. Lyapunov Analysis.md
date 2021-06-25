TARGET DECK: Main Deck

What is are FLOPS (unit of measurment)? #fc 
FLOPS stands for the number of floating point operations a computer can perform per second 
<!--ID: 1621985379925-->

Informally, what is a *Lyapunov function*, $V$? #fc
It is a positive function related to a system's state that gets smaller over time. It can potentially be used to make a statement about the long term behaviour of the system.
<!--ID: 1621986549981-->

Given a system $\dot{x} = f(x)$, with $f$ continuous, and for some region $\mathcal{B}$ around the origin, if I can produce a scalar, continuously differentiable function such that BLANK (2) conditions are met, then the origin is stable I.S.L. Fill in the blank #fc
$$V(x) > 0, \; \forall x \in \mathcal{B} \backslash \{0\} \quad V(0) =0 $$
and 
$$\dot{V}(x) = \frac{\partial V}{\partial x}f(x) \le 0, \; \forall x \in \mathcal{B} \backslash \{0\} \quad \dot{V}(x) = 0$$
<!--ID: 1621987217400-->


What are the conditions on $\dot{V}$ for local exponential stability? #fc 
$$\dot{V}(x) = \frac{\partial V}{\partial x}f(x) \le -\alpha V(x), \; \forall x \in \mathcal{B} \backslash \{0\}$$
for some $\alpha >0$
<!--ID: 1621987217424--> 

What are the conditions on $\dot{V}$ for local asymptotic stability (attractive and stable i.s.L)? #fc 
$$\dot{V}(x) = \frac{\partial V}{\partial x}f(x) \le 0, \; \forall x \in \mathcal{B} \backslash \{0\}$$
<!--ID: 1621987217428-->

Notation for a positive-definite function or matrix, and a positive semi-definite function or matrix. #fc 
$$V \succ 0$$ for positive definite and 
$$V \succeq 0$$ for positive semi definite 
<!--ID: 1621987376025-->


What is the latex command for the symbol: $\succ$? #fc 
it is "\succ"
<!--ID: 1621987376035-->

What is a level set of the function $f(x)$? #fc 
It is the set of $x$ values where $f(x) = c$, where $c$ is a real valued constant.
<!--ID: 1622028154183-->


What is a sublevel set of the function $f(x)$? #fc 
It is the set of $x$ values where $f(x) \le c$, where $c$ is a real valued constant. 
<!--ID: 1622028154217-->

Inside the subset $\mathcal B$, for every $\epsilon$-ball, I can choose a $\delta$ such that $|x(0)|^2 < \delta \implies |x(t)|^2 < \epsilon, \; \forall t$, by choosing $\delta$ \_\_\_\_\_\_\_ \_\_\_\_\_\_ so that the \_\_\_\_\_\_ set of $V(x)$ for the largest value that $V(x)$ takes in the $\delta$-ball is \_\_\_\_\_\_ \_\_\_\_\_\_\_ within the $\epsilon$-ball. Since the value of $V$ can only \_\_\_\_\_ (or stay constant) with time, this gives stability \_\_\_\_\_\_ #fc
sufficiently small, sublevel, completely contained, decrease, i.s.L.
<!--ID: 1622028481192-->

For a positive definite function $V \succ 0$, what are the nessecary (but not sufficient) conditinos on $V$ (hint: what does $V$ equal at $x = 0$ and what holds when $x \ne 0$)? #fc 
$V(0) = 0$, and $V(x) > 0$ for all $x \ne 0$. 
<!--ID: 1622029234245-->

Definition of a positive-definite function (layman: hint, positivity and nullity). #fc 
A function that maps from a vector space to real values and has the properties:
**Positivity:** $V(x) \ge 0$ forall $x \in \mathcal V$
**Nullity:** $V(x) = 0 \iff x = 0$
(Somtimes include **Monotonicity:** $||x_1|| \le ||x_2|| \implies V(x_1) \le V(x_2)$)
Rigorously:
A function that, for any real numbers $x_1, ..., x_n$, the $n \times n$ matrix
$$A = [f(x_i - x_j)]^n_{i,j=1}$$ is positive semi-definite. 
<!--ID: 1622030002966-->

What is the latex symbol for $\prec$? #fc 
"\prec"
<!--ID: 1622030314290-->


What three conditions must $V$ satisfy for global asymptotic stability about the origin $x = 0$ (hint: one is on $V$, one is on $\dot{V}$ and one is on the behavour of $V$ as $x \to \infty$)? #fc 
$$V(x) \succ 0$$
$$\dot{V}(x) \prec 0$$
$$V(x) \to \infty \text{ whenever } ||x||\to\infty$$
<!--ID: 1622030314329-->

What additional condition on $\dot{V}$ implies global exponential stability about the origin? #fc 
$$\dot{V}(x) \preceq -\alpha V(x)$$
for some $\alpha > 0$. 
<!--ID: 1622030921091-->



What is **LaSalle's theorem**: Given a system $\dot{x} = f(x)$ with $f$ continuous. If we can produce a scalar function $V(x)$ with continuous time derivatives for which we have \_\_\_\_\_ (condition on  $V$) and \_\_\_\_\_ (condition on $\dot{V}$) and \_\_\_\_\_ (condition on the asymptotic behaviour of $V$ as $||x|| \to \infty$), then $x$ will converge to the \_\_\_\_\_\_ (some set with a condition on $\dot{V}$). #fc 
$$V(x) \succ 0$$ ($V$ is positive everywhere except for the origin where it is $0$),
$$\dot{V}(x) \preceq 0$$
($\dot{V}$ is non-positive everywhere),
$$V(x) \to \infty \text{  as  } ||x|| \to \infty$$,
largest invariant set where $\dot{V} = 0$.
<!--ID: 1622030921129-->

Does the "largest invarient set need to be connected"? #fc 
No it does not
<!--ID: 1622034567016-->


What is the largest invarient set for a simple pendulum? #fc 
The union of all the fixed points of the system 
<!--ID: 1622034567060-->

Recall the HJB equation for the optimal control and cost-to-go
$$0 = \min_u [l(x,u) + \frac{\partial J^*}{\partial x}f(x,u)]$$ 
and assume we have solved for the optimal $u = u^*$. This tells us that
$$ \dot{J}^*(x) = \frac{\partial J^*}{\partial x}f(x,u^*) = -l(x,u^*) $$. 
How does this relate to the LaSalle conditions? #fc 
The LaSalle condition on $\dot{V}$ is 
$$\dot{V}(x) \preceq 0$$ 
which is a less stringent requirment. The HJB equation says that in optimal control, we must find a cost-to-go function that matches the gradient $-l(x, u^*)$ exactly. 
<!--ID: 1622034795292-->

What does SDP stand for in the context of optimization? #fc 
Semi-definite programming
<!--ID: 1622040394615-->


Semi-definite programming is a subset of \_\_\_\_\_\_ -- an extremely important class of problems for which we can produce efficient algorithms that are guarenteed to find the \_\_\_\_ \_\_\_\_\_ solution. #fc 
convex optimization,
globally optimal
<!--ID: 1622040394651-->


What is a convex function? #fc 
A real-valued function defined on an n-dimensional inverval is called convex if the line segment between any two points on the graph of the function lines above the graph between those two points
<!--ID: 1622040394655-->


What is convex optmization? #fc 
The study of minimizing convex function over convex sets 
<!--ID: 1622040394658-->

Lyapunov analysis for linear systems: Imagine you have a linear system $\dot{x} = Ax$, and can find a Lyapunov function in the form $V(x) =$ \_\_\_\_\_\_\_ , which also satisfies $\dot{V}(x)=$\_\_\_\_\_\_\_, then the origin is globally asympototically stable. #fc
$$V(x) = x^TPx, \; P = P^T \succ 0$$
$$\dot{V}(x) = x^TPAx + x^TA^TPx \prec 0$$
<!--ID: 1622042547944-->


What is the constraint $p(x)$ is SOS shorthand for, for a polynomial $p(x)$? #fc 
$p(x) \ge 0$ for all $x$, as demonstrated by finding a sum-of-squares decomposition. 
<!--ID: 1622042538391-->


Key connection between Lyapunov functions and invariant sets (hint: sublevel set). #fc 
Any sublevel set of a lyapunov function is also an invariant set.
<!--ID: 1622049552316-->


Given a system $\dot{x} = f(x)$ with $f$ continuous, if we can find a scalar function $V(x) \succ 0$, and a sublevel set
$$\mathcal G :\{ x | V(x) \le \rho\}$$
on which 
$$\forall x \in \mathcal{G}, \; \dot{V}(x) \preceq 0,$$
then $\mathcal G$ is an \_\_\_\_\_\_\_\_. By LaSalle, $x$ will \_\_\_\_\_ to the \_\_\_\_\_\_ on which \_\_\_\_\_\_\_. If $\dot{V} \prec 0$ in $\mathcal G$, then the origin is \_\_\_\_\_\_ and the set $\mathcal G$  is inside the region of attraction of this fixed point. If $\dot{V}(x) \preceq 0$ in $\mathcal G$ and $x=0$ is the only invariant subset of $\mathcal G$ where $\dot{V} = 0$, then the origin in \_\_\_\_\_\_\_  and the set $\mathcal G$ is inside the region of attraction of this fixed point. #fc 
Invariant set,
converge,
largest invarient subset of $\mathcal G$,
$\dot{V} = 0$,
locally asympototically stable,
asympototically stable
<!--ID: 1622050033196-->

What is the difference between *standard* Lyapunov analysis and *common* Lyapunov analysis? #fc 
Common Lyapunov analysis does not fully know the dynamics of the system. There are unknown parameters $\mathbf \alpha$ in the dynamics function $\dot{x} = f_\alpha (x)$, and we want to find a $V$ that "goes downhill" for all possible values of $\alpha$ within out current estimation bounds.
<!--ID: 1622546833938-->




