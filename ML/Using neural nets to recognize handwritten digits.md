TARGET DECK: Main Deck

What is a perceptron and how does it work? #fc 
A perceptron is a type of neuron which has binary inputs
$$ x_1, x_2, ... $$
and weights for those inputs
$$w_1, w_2, ... $$
and the single binary output is 1 if the weighted sum of the inputs 
$$\sum w_i x_i$$ 
is greater than or less than a threshold value. 
<!--ID: 1623804721333-->



Dot product and bias notation for expressing a perceptron output. #fc 
$$ \text{output} = \begin{cases} 0 \text{ if } w \cdot x + b \le 0 
					\\ 1 \text{ if } w \cdot x + b > 0\end{cases}$$
$b = -\text{threshold}$ is known as the *bias*
<!--ID: 1623804721365-->


What is a sigmoid neuron? #fc 
It has inputs $\mathbf x$ that are in the range of $[0,1]$, weights $\mathbf w$ in the range of $[0, 1]$, and a bias $b$. The output is in the range of $[0,1]$ and it is determined by the function:
$$\sigma(\mathbf x \cdot \mathbf w + b)$$
where 
$$\sigma(z) = \frac{1}{1 + e^{-z}}$$
is called the *sigmoid* or *logistic* function.
<!--ID: 1623804721370-->


What is another name for the *sigmoid* function (and what is it)? #fc 
The *logistic* function:
$$\sigma(z) = \frac{1}{1 + e^{-z}}$$
<!--ID: 1623804721373-->

What is the shape of the sigmoid funtion $\sigma(z)$? #fc 
An *S* shaped curve that approaches 0 as $z \to -\infty$ and 1 as $z \to \infty$. See pic: 
![[Pasted image 20210615205747.png]]
<!--ID: 1623805453632-->


What is the activation function of a neuron? #fc 
The activation function is $f$, and the output is determined by
$$\text{output} = f(\mathbf w \cdot \mathbf x + b)$$
<!--ID: 1623805453666-->


What is a hidden layer in a neural network? #fc 
A layer that is neither input nor output
![[Pasted image 20210616061122.png]]
<!--ID: 1623840858390-->



What is a feedforward neural network? #fc 
The output of one neuron is the input to the next, and there are no loops
<!--ID: 1623840858420-->



What model of artifical neural networks allows for the possibility of feedback loops? #fc 
Recurrent neural networks, where some neurons fire for a limited duration of time.
<!--ID: 1623840858425-->


What is the work for a state of inactivity or dormancy (hint: q)? #fc 
quiescent
<!--ID: 1623840858430-->


What does *quiescent* mean? #fc 
A state of inactivity or doramncy 
<!--ID: 1623840858434-->


Two other names for a cost function. #fc 
Objective function or loss function
<!--ID: 1623840858439-->


What is a cost function? #fc 
It is a non-negative function of the weights and biases (parameters) of a neural network (and the desired output and actual output of the network), that quantifies how far away from the desired output the network is.
<!--ID: 1623840858443-->


What would the MSE cost function look like for a dataset for classifying $n$ images, with an input variable $x$ to the neural net, a desired output $y(x)$, and an actual output $a(x)$?
$$C(w, b) = \frac{1}{2n} \sum_x || y(x) - a(x) ||^2$$

We want to minimize a function $C(v)$. We are currently at the value $v_0$. What next value of $v$ should we choose so as to "move downhill" towards a local minima? Consider a learning rate of $\eta > 0$. #fc 
We should choose $\Delta v = -\eta \nabla C$ so $v_1 = v_0 - \eta \nabla C$
<!--ID: 1623840858448-->


What is the learning rate in gradient descent? #fc 
It is the small positive number $\eta$ which is multiplied by the gradient of the objective function $C$ to find the differential change in the inputs that will move the objective function downhill.
<!--ID: 1623840858451-->


If the learning rate $\eta$ is choosen to be too large, what problem could this have? #fc 
Recall that for the objective function $C(v)$, the direction downhill is approximately given by:
$$\Delta C = \nabla C \cdot \Delta v$$
but this approximatino only holds for small $\Delta v$. So if we choose
$$\Delta v = -\eta \nabla C$$
like in gradient descent, then there is the rist that if $\eta$ is too large, than $\Delta C$ will not be negative. 
<!--ID: 1623841396444-->


If the learning rate $\eta$ is too small, what issue could arise? #fc 
The network could learn too slowly
<!--ID: 1623841396494-->


What is the cauchy-schwartz inequality? #fc 
For any inner product denoted by $\cdot$
$$(u \cdot v)^2 \le (u \cdot u)(v \cdot v)$$
<!--ID: 1623842900216-->


Gradient descent rule in terms of the components of the weights $w_k$ and biases $b_l$ of a neural network (update rule). #fc
$$w_k \to w_k' = w_k - \eta \frac{\partial C}{\partial w_k}$$
$$b_l \to b_l' = b_l - \eta \frac{\partial C}{\partial b_l}$$
<!--ID: 1623842900256-->


What is stocastic gradient descent, and why is it needed? #fc 
For all of the $n$ training data inputs $x$, to find the gradient of the cost function we compute an average of the gradients for each input and average them:
$$\nabla C = \frac{1}{n} \sum_x \nabla C_x$$
However this can take too long for many peices of training data. Instead, we pick a *mini-batch* of size $m$ from the dataset, and assume that it's average approxmates $\nabla C$:
$$\nabla C \approx \frac{1}{m}	\sum_{j=1}^m \nabla C_{X_j}$$
<!--ID: 1623842900262-->


What is a minibatch? #fc 
It is a subset of the entire training dataset that is used for stocastic gradient descent.
<!--ID: 1623842900265-->


What is an epoch? #fc 
An epoch is completed when the training has worked through enough randomly chosen minibatches to cover the entire original dataset.
<!--ID: 1623842900268-->


The learning rate is an example of a (hint: starts with an h) #fc 
Hyperparameter
<!--ID: 1623890340685-->


What are deep neural networks? #fc 
Neural networks with 2 or more hidden layers.
<!--ID: 1623890340718-->

What is 2D convolution? #fc 
You have a kernel matrix
$$ \begin{bmatrix} a & b & c \\
d & e & f \\
g & h & i
\end{bmatrix}$$
(in this case it is 3x3). This kernel matrix has its rows and columns flipped. Then it is "slid" across the image, and the pixel values undergo a weighted sum, the result of which is a pixel of the new image with that weighted value at the center. 
<!--ID: 1624447191503-->

What does `nn.Dropout2d(p = 0.5)` do to a tensor? #fc 
It randomly zeros out channels of the tensor with a probability `p`. For example if you have a tensor of the shape `(N, C, H, W)`, we select and $(i,j) \in (N,C)$, and zero out the images of shape $(H,W)$.
<!--ID: 1624448011553-->


What does `nn.functional.dropout(p = 0.5)` do to a tensor? #fc 
Randomly zeros out values in the tensor with probabilty $0.5$. 
<!--ID: 1624448011595-->

What does `nn.Conv2d(input_channels, output_channels, kernel_size)` do to a tensor of shape `(N, C, H, W)`? #fc 
It applies a 2d convolution to the images of shape `(H, W)`, where the items in the kernel are learned parameters.
<!--ID: 1624449172127-->


What is max pooling? #fc 
Slide a kernel over an image, set the resultant pixel value to the maximum value under the kernel. 
![[Pasted image 20210623073744.png]]
<!--ID: 1624449172162-->


What is negative log likelihood? #fc 
$L = -log(p_k)$ where $p_k$ is the output of the softmax function
$$p_k = \frac{e^{f_k}}{\sum_j e^{f_j}}$$.
You also know it as the **information content** of a particular event (ie. less likely yield more information (high negative log likelyhood)).
<!--ID: 1624449172165-->



What is the softmax function, and why is it usefull (take a vector input)? #fc
For each element in the vector (denoted $f_{y_i}$, because the softmax is usually applied to the last lay of a neural net, after a forward pass), the softmax function does:
$$ S(f_{y_i}) = \frac{e^{f_{y_i}}}{\sum_j e^{f_{y_j}}}$$
which both normalizes the elements of the vector between 0 and 1, and makes the whole vector sum to 1. It can therefor be though of as a probabilty. 
<!--ID: 1624449172168-->

The notation $w^l_{jk}$ is used to denote which weight in a neural network? #fc 
The weight for the connection between the $k^{th}$ neuron in the $(l-s)^{st}$ layer to the $j^{th}$ neuron in the $l^{th}$ layer.
<!--ID: 1624452589052-->


The notation $b^l_j$ is used to denote what in a neural network? #fc 
The bias for the $j^{th}$ neuron in the $l^{th}$ layer of the neural network.
<!--ID: 1624452589089-->

For an activation function $f$, activation $a_j^l$, biases $b^l_j$, and weighted $w^l_{jk}$, what is the activation of the $l^{th}$ layer? #fc
$$a_j^l = f(\sum_k w^l_{jk} a^{l-1}_k + b^l_j)$$
or in full matrix form
$$a^l= f(w^l \cdot a^{l-1} + b^l)$$, where in the last equality, $f$ is the vectorized version of the function
<!--ID: 1624452999801-->


How does the weight matrix $w^l$ relate to the individual weights $w^l_{jk}$? #fc 
The $j^{th}$ row and $k^{th}$ column of $w^l$ is equal to $w^l_{jk}$.
<!--ID: 1624452999866-->


Howe does the bias vector $b^l$ relate to the individual viases $b^l_j$? #fc 
The $j^{th}$ entry in $b^l$ is $b^l_j$.
<!--ID: 1624452999869-->


What is the hadamard product, $\odot$ of two vectors? #fc 
The elementwise product of those vectors.
<!--ID: 1624498096051-->


How is the error in the jth neuron of the lth layer defined? #fc 
$\delta^l_j = \frac{\partial C}{\partial z^l_j}$, where $z^l_j = \sum_k w^l_{jk} a^{l-1}_k + b^l_j$  is the weighted input to activation function for the $j$th neron in the $l$th layer.
<!--ID: 1624498096083-->


What is the intution behind the definition for the error of the jth neuron in the lth layer being $\delta^l_j = \frac{\partial C}{\partial z^l_j}$ #fc 
If $\delta$ is small, it means that the cost is at a local minima wrt the weights and biases associated with that neuron -> the error is small, and visa versa.
<!--ID: 1624498096089-->






