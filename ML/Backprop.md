TARGET DECK: Main Deck

What is the expression for the jth component of the error in the last layer $\delta^L_j$ if $C = C(a^L)$, the components of $a^L$ (the output of the last layer), are denoted $a^L_j$ and the weighted inputs to each neuron in the last layer are $z^L_j$? #fc 
$$\delta^L_j = \frac{\partial C}{\partial a^L_j}f'(z^L_j)$$,
where $f$ is the activation function of the neuron.
<!--ID: 1624616701379-->


What is the vector expression for the error of the last layer of neurons, $\delta^L$, in terms of their outputs $a^L$ and their weighted inputs $z^L$ (vectors)? #fc 
$$\delta^L = \nabla_a C \odot f'(z^L)$$
<!--ID: 1624616701393-->

What is the equation for the error $\delta^l$ in terms of $\delta^{l+1}$? #fc 
$$ \delta^l = ((w^{l+1})^T\delta^{l+1}) \odot f'(z^l)$$
where $w$ is the weight matrix, $\delta^{l+1}$ is the error vector for the $l+1$ th later of the network, and $z^l$ is the weighted input to the $l$th layer. 
<!--ID: 1624618368953-->


What is $\frac{\partial C}{\partial b^l_j}$ equal to? (apply chain rule) #fc
$$\frac{\partial C}{\partial b^l_j} = \frac{\partial C}{\partial z^l_j}\frac{\partial z^l_j}{\partial b^l_j} = \delta^L_j$$. Less precisly we can say
$$ \frac{\partial C}{\partial b} = \delta$$, where it is assumed that the $\delta$ is the error for the neuron with the weight $b$. 
<!--ID: 1624618368985-->

What does $\frac{\partial C}{\partial w}$ equal? #fc 
$$\frac{\partial C}{\partial w} = a_{in} \delta_{out}$$
where $a_{in}$ is the activation of the neuron input to the weight $w$ and $\delta_{out}$ is the error of the neuron output from the weight $w$. More precisly we can say that
$$\frac{\partial C}{\partial w^l_{jk}} = a^{l-1}_k \delta^l_j$$
<!--ID: 1624618754579-->

At a high level, what are the 5 steps of backpropogation? #fc 
1. Input (set input $x$ as output of first layer $a^{1}$)
2. Feedforward (finr $a^l$ and $z^l$)
3. Find output error (find $\delta^L$)
4. Backpropogation (find $\delta^l$ from $\delta^{l+1}$)
5. Output (find $\frac{\partial C}{\partial w^l_{jk}}$ and $\frac{\partial C}{\partial b^l_j}$)
<!--ID: 1624620335854-->

What is the first step of backpropogation? #fc 
Set the input $x$ as the output of the first layer $a^1$
<!--ID: 1624620748233-->


What is the second step of backpropogation? #fc 
Using your current weights and biases, compute
$$z^l = w^l a^{l-1} + b^l$$ (weighted input) and
$$a^l = f(z^l)$$ (output of lth layer of neurons)
for all layers $l = 1 ... L$
<!--ID: 1624620748279-->


What is the third step of backpropogation (hint: last layer)? #fc 
Find output error $\delta^L$:
$$\delta^L = \nabla_a C \odot f'(z^L)$$
<!--ID: 1624620748283-->


What is the latex command for $\odot$? #fc
`\odot`
<!--ID: 1624620748285-->


What is the fourth step of backpropogation (hint: backprop)? #fc 
Find the error of each layer (**backpropogation**)
$$\delta^l = ((w^{l+1})^T \delta^{l+1}) \odot f'(z^l)$$
<!--ID: 1624620748288-->


What is the fifth step of backpropogation (hint: last step)? #fc 
Using the computed error at each layer $\delta^l$, find 
$$\frac{\partial C}{\partial b^l_j} = \delta^l_j$$
and 
$$\frac{\partial C}{\partial w^l_{jk}} = a^{l-1}_k \delta^l_j = a_{in} \delta_{out}$$
<!--ID: 1624620748290-->


Using back propogation, what are the 3 steps for gradient descent? (hint: input, backprop, descend) #fc
1. Input a set of training examples
2. For each training example, $x$, set the corrisponding input activation $a^{x,1}$ and do backpropogation to compute $\delta^{x,1}$
	1. feedforward, find $z^{x,l}  = w^l a^{x, l-1} + b^l$ and $a^{x,l} = f(z^{x,l})$
	2. compute the output error $\delta^{x,L} = \nabla_a C_x \odot f'(z^{x,L})$
	3. backpropogate the error $\delta^{x,l} = ((w^{l+1})^T \delta^{x,l+1})\odot f'(z^{x,l})$
3. For each $l = L, ..., 2$, update the weights according to the rule $w^l \to w^l - \frac{\eta}{m} \sum_x \delta^{x,l} (a^{x,l-1})^T$ and the biases according to the rule $b^l \to b^l - \frac{\eta}{m} \sum_x \delta^{x,l}$
<!--ID: 1624621409153-->


