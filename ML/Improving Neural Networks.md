TARGET DECK: Main Deck

Why do we use cross entropy loss as opposed to MSE? #fc 
Because MSE suffers from small
$$\frac{\partial C}{\partial w}$$
and 
$$\frac{\partial C}{\partial b}$$
when you have bad initial conditions.
Cross entropy loss does not suffer from this issue.
<!--ID: 1624794760068-->


The activations in the last layer of a neural network are $a_j^L$ and the desired activations are $y_j$. What is the cost as formulated using **cross entropy loss**. The inputs to the neural network are $x$ #fc 
Recall that the cross entropy loss for two probability distributions (true, $p$, estimated $q$):
$$H(p,q) = \sum_x -p\log(q)$$
We take $p \in \{y_j, 1-y_j\}$ and $q \in \{a_j, 1-a_j\}$ as the probability distributions (for all outputs). Then the cross entropy loss is:
$$H(p,q) = \frac{-1}{n}\sum_x \sum_y y_j\log(a_j) + (1-y_j)\log(1-a_j)$$I
Note here that we have averaged across all observations.
<!--ID: 1624794760082-->


For sigmoid activation functions, when should we use quadratic cost vs cross entropy loss? #fc 
We almost always want to use cross entropy loss.
<!--ID: 1624794952368-->


If the weighted inputs to the last layer of a neural network are $z^L_j$, using a softmax function, how are the activations in the last layer computed ($a^L_j$)? #fc 
They are computed as:
$$a^L_j = \frac{e^{z_j^L}}{\sum_k e^{z_k^L}}$$
<!--ID: 1624826918694-->

What is the log likelyhood cost function? #fc 
$$C = - \ln a^L_y$$. where $a^L_y$ is the desired output. If the network outputs 1 for this output (desired), then the cost small. If the network outputs 0, the cost is infinite.
<!--ID: 1625005170746-->



A softmax output layer with log likelyhood loss is very similar to what? #fc 
A sigmoid layer with cross entropy loss.
<!--ID: 1625005170839-->


What output/loss architecture should be used for a neural network if we want to interpret the outputs as probabilities? #fc 
Softmax outut layer with a log-likelihood loss function
<!--ID: 1625005170843-->


For the softmax function $a_k^L = \frac{e^{-z^L_j}}{\sum_k e^{-z^L_k}}$, what is it's derivative with respect to $z_j$ for $j =k$ and $j\ne k$? #fc 
The derivative is
$$a^L_k (\delta_{jk} - a_j^L)$$, where $\delta_{jk}$ is the kronecker delta.
<!--ID: 1625010900788-->


In machine learning, what is the validation set used for? #fc 
We iteratively check the accuracy of the network on the validation data, and early stop if the accuracy starts going down (overfitting).
<!--ID: 1625010900823-->


What is early stopping? #fc 
Stopping training when the accuracy of the network on the validation set starts dropping to prevent overfitting. 
<!--ID: 1625010900827-->


Why use validation data as opposed to test data to choose hyper parameters? #fc 
Because the choice of hyperparameters themselves could be overfit the test data. The validation set is data that can be used to "learn" the best hyperparameters.
<!--ID: 1625011990812-->


For L2 regularization, what is the term that is added to the cost function? #fc
Sum across all the weights squared $w^2$, and divide by 2 times the size of the training set $n$. We also multiply by the regularization parameters $\lambda$.
$$ \frac{\lambda}{2n} \sum_w w^2 $$. 
<!--ID: 1625011990851-->


How is the original cost function $C_0$ modified by L2 regularization? #fc
$$ C = C_0 + \frac{\lambda}{2n} \sum_w w^2 $$
<!--ID: 1625011990855-->


What does regularization do? What role does $\lambda$ play, the regularization parameter? #fc 
Adds a compromise between minimizing the original cost function and finding small weights. The relative importance of these two components is weighted by $\lambda$.
<!--ID: 1625011990857-->


How do $\frac{\partial C}{\partial w}$ and $\frac{\partial C}{\partial b}$ change when we use L2 regularization (in terms of the derivatives of the original cost function $C_0$)? #fc 
$$ \frac{\partial C}{\partial w} = \frac{\partial C_0}{\partial w} + \frac{\lambda w}{n}$$
$$\frac{\partial C}{\partial b} = \frac{\partial C_0}{\partial b}$$. This means we can do normal back propogation, and add the term $\frac{\partial \lambda w}{\partial n}$ for each derivative with respect to a weight.
<!--ID: 1625011990860-->


How does the learning rule (update step) for $b$ and $w$ change with L2 regularization? Use a learning rate of $\eta$. #fc 
$$ b \to b - \eta \frac{\partial C_0}{\partial b}$$ (unchanged)
$$ w \to w - \eta \left(\frac{\partial C_0}{\partial w} - \frac{\lambda}{n} w \right) = \left(  1- \frac{\eta \lambda}{n} \right)w - \eta \frac{\partial C_0}{\partial w}$$
<!--ID: 1625011990863-->


What is the weight decay coefficient? Hint: L2 regularization #fc 
It is the term in front of the weights for their learning rule with L2 regularization:
$$\left(1 - \frac{\eta \lambda}{n} \right)$$
<!--ID: 1625011990865-->

Does a larger training set require a larger or smaller regularization parameter $\lambda$? #fc 
It requires a larger regularization parameter to balance out hte larger $n$ in the weight decay coefficient:
$$( 1- \frac{\eta \lambda}{n} )$$
<!--ID: 1625013125965-->


Does a smaller regularization parameter $\lambda$ result in faster or slower weight decay for a fixed $n$? #fc 
Slower weight decay because the weight decay coefficient is closer to 1:
$$( 1- \frac{\eta \lambda}{n} )$$
<!--ID: 1625013126004-->


Intuitvely, why does regularization improve accuracy and repeatability for a neural network? #fc 
Without regularization, the weight vector can grow very long, making it difficult to explore other regions of the weight space. Regularization allows an algorithm to more easily explore the weight space. 
<!--ID: 1625013126008-->



What is the addative term for L1 regularization? #fc 
$\frac{\lambda}{n} \sum_w |w|$
<!--ID: 1625013126012-->


What is $\frac{\partial C}{\partial w}$ for L1 regularization (initial cost function is $C_0$)? #fc 
$$\frac{\partial C}{\partial w} = \frac{\partial C_0}{\partial w} + \frac{\lambda}{n}\text{sgn}(w)$$
<!--ID: 1625013126016-->

What is the learning rule with L1 regularization? #fc 
$$w \to w - \frac{\lambda \eta}{n}\text{sgn}(w) - \eta \frac{\partial C_0}{\partial w}$$
<!--ID: 1625013382987-->


What is the difference in the regularization effect between L1 and L2? Why? #fc 
Learning rule for L1:
$$w \to w - \frac{\lambda \eta}{n}\text{sgn}(w) - \eta \frac{\partial C_0}{\partial w}$$
Learning rule for L2:
$$ w \to w - \eta \left(\frac{\partial C_0}{\partial w} - \frac{\lambda}{n} w \right) = \left(  1- \frac{\eta \lambda}{n} \right)w - \eta \frac{\partial C_0}{\partial w}$$
L1 applies a constant modification to $w$, regardless of the weight size. This means that large weights are penalized less proportionately to small weights, so the network will tend to concentrate the weights in the high-importance connections, while other weights are driven towards 0. 
<!--ID: 1625013382995-->

What does dropout do to a neural network? #fc 
It randomly deletes a proportion $p$ (usually 0.5) of the hidden neurons (not on the input or output layers) when updating a detwork over a minibatch (updating the weights and biases of the non-deleted neurons).  Then on the next minibatch, the deleted neurons are restored, and a new random subset of the neurons are deleted.
<!--ID: 1625054526842-->


Intuitively, why does dropout work? #fc 
It is almost like training multiple smaller neural networks seperately, and taking their consensus on what the correct answer is. This helps reduce over fitting, because while each subnetwork might overfit to peculiarities in the data, the consensus will not.
<!--ID: 1625054526874-->



What is the issue with normalizing the weights and biases of neurons to gaussians with mean 0 and standard deviation 1? #fc 
The weighted inputs to the next layer $z^{l+1}_j$, whill have a large standard deviation, and thus is likely to be very large or small.  This will cause the neurons in the next layer to saturate, slowing down learning.
<!--ID: 1625054526879-->


How shold you choose to initialize the weights of a neural network? #fc 
For the input layer with $n_{in}$ neurons, use a gaussian with mean 0 and standard deviation $\frac{1}{\sqrt{n_{in}}}$. For thebiases, use a standard normal gaussian distribution. This holds for deeper layers in the network.
<!--ID: 1625054526885-->

e^x limit definition? #fc 
$$\lim_{n\to \infty} \left( 1 + \frac{x}{n} \right) ^n$$
<!--ID: 1625190877169-->


What is a learning rate schedule, and how is it usually set? #fc 
Vary the learning rate across the training. It should usually be larger at the start because the weights will be badly wrong. 
<!--ID: 1625190877319-->

What is the Hessian of a cost function $C$? #fc 
A matrix made up of the entries:
$$\frac{\partial^2 C}{\partial w_j \partial w_i}$$
where $j$ is the row number and $i$ is the column number
<!--ID: 1625272564343-->


How to express $C(w + \Delta w)$ in terms of $C(w)$ using a second order taylor exansion? Hint: hessian. #fc
$$ C(w + \Delta w) = C(w) + \nabla C\Delta w + \frac{1}{2}\Delta w^T H \Delta w$$
Where $H$ is a hessian matrix.
<!--ID: 1625272564380-->


What is the update rule for $w$ using the hessian technique? #fc 
$$w = w - \eta H^{-1} \nabla C$$
where $H$ is the hessian and $\eta$ is the learning rate.
<!--ID: 1625272564383-->



What are the update rules for $v$ and $w$ in momentum-based gradient descent? #fc 
For each $w$ (here representing weights or biases), there is an associated velocity $v$. The update steps are:
$$v \to \mu v - \eta \nabla C$$
$$w \to w + v$$
where $\mu$ is called the momentum parameter
<!--ID: 1625272564386-->


What does a momentum parameter $\mu = 0$ mean? #fc
Very high friction, we are no longer doing momentum based gradient decsent.
<!--ID: 1625272564388-->


What does a high momentum parameter $\mu$ mean? #fc
Very low friction, we can build up "momentum" in gradient decsent, but are also more likely to overshoot.
<!--ID: 1625272564390-->

What is the vanishing gradient problem? #fc 
Gradients tend to decrease as your move backwards layer by layer through a neural network (starting at the output layer). This means that the earlier layers will have a far slower rate of learning.
<!--ID: 1625273841545-->


What is the intuitive cause for the vanishing gradient problem (or exploding grdient problem). Use a toy network with one neuron per layer? #fc 
The gradient of the cost function with respect to a bias (similar form for weight) usually looks like:
$$\frac{\partial C}{\partial b_1} = \sigma'(z_q)w_2\sigma'(z_2)w_3 \; ... \; w_L\sigma'(z_L)\frac{\partial C}{\partial a_L}$$
Upon initialization, it is usually the case that all $|w_j \sigma(z_j)|$ are greater than $1$ or less than $1$, meaning we get exponential growth or decay as the gradient is propogated backwards, at least initially.
<!--ID: 1625361308112-->


With sigmoid neurons, is vanishing or exploding gradient more likely, why. Use a toy network with one neuron per layer? #fc 
vanishing. Recall the terms that are multiplied to find the gradient earlier inthe network are $w_j  \sigma'(w_j a_{j-1} +b_j)$. $\sigma'(z)$ has a maximum at $z = 0$ of $\frac{1}{4}$. If we make $w_j$ large, then $\sigma'$ is also likely to get small, maintaining the vanishing gradient.
<!--ID: 1625361308140-->

In a convolutional net, what is the local receptive field of a neuron? #fc 
It is the set of inputs in the images (pixels), that the neuron in question is connected to (via weights, one per neuron, and a bias)
<!--ID: 1625362277162-->


What is the stride length on a convoutional network? #fc 
The number of pixels that the receptive field is "slide" across per neuron in the first hidden layer
<!--ID: 1625362277203-->


How do the weights and biases differ for the neurons in a convolutional neural network? #fc 
The weights and biases are shared for all neurons in the first hidden layer of the network (actually any convolutional layer)
<!--ID: 1625362277207-->


Why does it make sense for a convolutional net to share weights across its feature map? #fc 
Because images are larely translation invarient, so we think that each neuron should be "looking for" the same thing at different locations on the image.
<!--ID: 1625362277211-->


What is a *feature map* in a convolutional network? #fc 
It is a map from one layer (eg the input layer) to the next. The weights and bias define the feature map, and are also said to define a *kernel* or *filter*.
<!--ID: 1625362277214-->


What is a pooling layer in a CNN? #fc 
It is a layer of neurons the "summarizes" or "pools" the output information from the preceding convolutional layer. Each neuron in the pooling layer summarizes the information from some region in the previous layer. and example is max-pooling.
<!--ID: 1625362277218-->

Visualize what a CNN looks like with three (24x24) feature maps and three (12 x 12) pooling layers, and 10 output neurons. How are the output layers connected? #fc 
![[Pasted image 20210704063458.png]]
Every ouput neuron is connected to every neuron in the 3 x 12 x12  max pooling layers.
<!--ID: 1625405957138-->


How are consecutive convolution-pooling layers connected in a CNN? #fc 
Each neuron in the second convolutional-pooling layer leans from its receptive field in all of the $N$ "images" produced by the previous cooling layer. (imagine that the convolutional layer is connected to an $N$ dimensional color input layer).
<!--ID: 1625405957141-->


































