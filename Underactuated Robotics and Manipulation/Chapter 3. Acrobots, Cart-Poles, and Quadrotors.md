TARGET DECK: Main Deck

What is the acrobot #fc 
A two link rigid pendulum that is actuated at the "elbow" joint
<!--ID: 1620751498009-->


A strictly stable (what does this mean?) linearization implies that #fc
there is local exponential stability of the non-linear system 
<!--ID: 1620751498045-->


An unstable linearized system implies that #fc 
The system itself is unstable
<!--ID: 1620751498049-->


Definition of a controllable system #fc 
A system of the form
$$\dot{\mathbf x} = \mathbf f(\mathbf x, \mathbf u)$$
Is called controllable if it is possible to construct an unconstrained input signal $\mathbf u(t), \; t \in [0,t_f]$, which will move the system from any initial state to any final state in a finite interval of time, $0 < t < t_f$.
<!--ID: 1620751498054-->


Controllability of the linear system $\dot{\mathbf x} = \mathbf A \mathbf x + \mathbf B \mathbf u$ assuming $A \in ^n \mathbb R ^n$ has $n$ distinct eigenvalues #fc 
It can be shown through the use of modal coordinates that this system is controllable if and only if:
$$\forall i, \exists j \text{ such that } \beta_{ij} \ne 0$$
where $\mathbf \beta = \mathbf V^{-1} \mathbf B$ and $\mathbf V$ is a matrix with colums of eigenvectors. If this conditions is met, then each control coordinate can influence a modal coordinate (which forms a basis), so the system is controllable. 
<!--ID: 1620751498057-->


Is an underactuated system an uncontrollable system #fc 
No, not necessarily. Underactuated systems cannot follow arbitrary trajectories, but that does not imply that they cannot arrive at arbitrary points in state space. However, the trajectory required to place the system into a particular state may be arbitrarily complex.
<!--ID: 1620751498061-->


What is partial feedback linearization #fc 
Linearizing a portion of the system dynamics with a certain control $\mathbf u$
<!--ID: 1620751498065-->


What is collocated partial feedback linearization #fc 
A controller that linearizes the dynamics of actuated joints.
<!--ID: 1620751498069-->


What is non-collocated partial feedback linearization #fc 
A controller which linearizes the dynamics of unactuated joints.
<!--ID: 1620751498072-->


Condition for non-collocated linearization #fc 
$M_{12}$ has a unique moore-penrose pseudo-inverse, which occurs when $\text{rank } M_{12} = l$, where $l$ is the number of passive degrees of freedom in the system (unactuated joints). This condition is called the property of **Strong Inertial Coupling**
<!--ID: 1620751498076-->


What is the moore-penrose pseudo inverse of $\mathbf A$: #fc
$$ A^+ = A^T(AA^T)^{-1} $$
<!--ID: 1620751517435-->


What is task-space partial feeback linearization #fc 
The task-space $\mathbf y = \mathbf h( \mathbf q ) \in \mathbb R^p$  defines the combination of active and passive joints we would like to control. Define $\mathbf H_1 = \frac{\partial \mathbf h}{\partial	\mathbf q_1 }$, $\mathbf H_2 = \frac{\partial \mathbf h}{\partial \mathbf q_2}$, and $H = [H_1, H_2]$. Then the joints are commanded such that $\ddot{\mathbf q}_2 = \bar{\mathbf H}^+ [\ddot{\mathbf y}^d  - \dot{\mathbf H}\dot{\mathbf q} - \mathbf H_1 M_{11}^{-1} \tau_1]$, where $\bar{\mathbf H} = \mathbf H_2 - \mathbf H_1 \mathbf M_{11}^{-1}\mathbf M_{12}$, and the $+$ indicates a moore-penrose psuedo inverse.
<!--ID: 1620751498080-->


An equivanlent form to the manipulator equation for trivially underactuated systems: #fc
$\mathbf M_{11}\ddot{\mathbf q}_1 + \mathbf M_{12}\ddot{\mathbf q}_2 = \tau_1$
$\mathbf M_{21} \ddot{\mathbf q}_1 + \mathbf M_{22} \ddot{\mathbf q}_2 = \tau_2 + \mathbf u$
where $\mathbf q \in \mathbb R^n$, $n = l+m$,  $\mathbf q \in \mathbb R^l$ represents passive joints, $\mathbf q_2 \in \mathbb R^m$ represents actuated joints, $\tau = \tau_g - \mathbf C\dot{\mathbf q}$, and $M$ is made of the $M_{ij}$ matricies in block form.
<!--ID: 1620751498083-->





