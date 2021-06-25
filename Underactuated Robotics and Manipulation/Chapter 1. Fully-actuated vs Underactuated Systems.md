TARGET DECK: Main Deck


General form of second-order control dynamical system #fc
$$\ddot{\mathbf q} =\mathbf f(\mathbf q, \dot{\mathbf{q}}, \mathbf u, t)$$ where $\mathbf q$ is the configuration vector (positions), $\dot{\mathbf{q}}$ is a vector of velocities, and $\mathbf u$ is the control vector.
<!--ID: 1620216279591-->

Define fully actuated #fc 
A second-order control differential equation $$\ddot{\mathbf q} =\mathbf f(\mathbf q, \dot{\mathbf{q}}, \mathbf u, t)$$ is *fully actuated* in state $\mathbf x = (\mathbf q, \dot{\mathbf{q}})$ and at time $t$ if the resulting map of $\mathbf f$ is surjective: for every $\ddot{\mathbf{q}}$ there exists a $\mathbf{u}$ which produces the desired response. Otherwise it is *underactuated* (in $\mathbf{x}$ at time $t$).
<!--ID: 1620258347025-->


Define a surjective function #fc 
In mathematics, a function $f$ from a set $X$ to a set $Y$ is surjective, if for every element $y$ in the codomain $Y$ of $f$, there is at least one element $x$ in the domain $X$ of $f$ such that $f(x) = y$. It is not required that $x$ be unique; the function $f$ may map one or more elements of $X$ to the same element of $Y$.
<!--ID: 1620258347058-->


Dynamical equation if the dynamics are control affine (linear in command torque), and resulting definition of *underactuated* #fc 
$$\ddot{\mathbf{q}} = \mathbf{f}_1(\mathbf q, \dot{\mathbf{q}}, t) + \mathbf{f}_2(\mathbf q, \dot{\mathbf{q}}, t)\mathbf{u}$$
If the system is underactuated:
$$\text{rank}[\mathbf{f}_2(\mathbf q, \dot{\mathbf{q}}, t)] < dim[\mathbf{q}]$$
This means that $\mathbf f_2$ is less than full row rank (the dimension of the column space is less than the dimension of $\mathbf q$, so not all $\mathbf q$'s can be created).
Be careful, because other constraints like $|\mathbf{u}| \le 1$ can also make the system underactuated.
<!--ID: 1620258347061-->


Definition of the rank of matrix $\mathbf A$ #fc 
$\text{rank} = \text{dim row} \mathbf A = \text{dim col} \mathbf A$
<!--ID: 1620258347064-->

A *system* is underactuted if #fc 
it is underactuated for all states and times
<!--ID: 1620265161799-->


Lagrangian definition and dynamic equations #fc 
$$L = T - U$$ where $T$ is the total kinetic energy of the system and $U$ is the total potential energy of the system. 
The dynamic equation is 
$$\frac{d }{dt} \frac{\partial L}{\partial \dot{ q}_i} - \frac{\partial L}{\partial q_i} = Q_i$$
where $Q_i$ is the generalized force corresponding to $q_i$.
<!--ID: 1620265161848-->


Standard form of the manipulator equations #fc 
$$\mathbf M(\mathbf q)\ddot{\mathbf q} + \mathbf C(\mathbf q, \dot{\mathbf q})\dot{\mathbf q} = \tau_g(\mathbf q) + \mathbf B \mathbf u$$. The intertia matrix $\mathbf M(\mathbf q)$ is always uniformly symmetric and positive definite, so it is invertible. $\mathbf C$ captures the coriolis forces, $\mathbf \tau_g$ and $\mathbf B$ maps the control inputs $\mathbf u$ into generalized forces.
<!--ID: 1620265161853-->


If $\text{dim} u < \text{dim} q$ then is the system under or fully actuated? #fc
Under
<!--ID: 1620265161856-->


Feedback control for fully actuated systems #fc 
Using the control $$\mathbf u = \mathbf f_2^{-1}(\mathbf q, \dot{\mathbf q},t)[\mathbf u' - \mathbf f_1(\mathbf q, \dot{\mathbf q}, t)]$$ yields $$\ddot{\mathbf q} = \mathbf u'$$
<!--ID: 1620265161858-->


Define input and state constraints #fc 
A dynamical system described by $$\dot{\mathbf x} = \mathbf f(\mathbf x, \mathbf u, t)$$ may be subject to one or more constraints described by $\phi(\mathbf x,\mathbf u,t) \ge 0$
<!--ID: 1620265161860-->



Holonomic vs non-holonomic constraints #fc 
A nonholonmic constraint is of the form $\phi(\mathbf q, \dot{\mathbf q}, t) = 0$ which cannot be integrated to the form $\phi(\mathbf q,t) =0$ (a holonomic constraint). A nonholonomic constraint does not restric the possible configurations of the system, but the manner in which those configurations can be reached. A holonomic constraint reduces the dof the the system by 1, a holonomic constraint does not. 
<!--ID: 1620265161863-->


A car and train are examples of which types of constraints #fc 
car: holonomic: cannot move directly sideways
train: the track constraint can be written directly in terms of position, with no reference to velocity. The track restricts the possible configurations.
<!--ID: 1620303487449-->


True or False: A fully actuated robot assume any twice differentiable trajectory on it's phase plane #fc 
False
<!--ID: 1620303487490-->


