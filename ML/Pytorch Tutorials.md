TARGET DECK: Main Deck

How to create a pytorch tensor from `data = [[1,2], [3,4]]`? #fc 
`x_data = torch.tensor(data)`
<!--ID: 1623065153784-->


How to create pytorch tensor from a numpy array `np_array`? #fc 
`x_np = torch.from_numpy(np_array)`
<!--ID: 1623065153822-->

How to create torch tensor of zeros? #fc 
`x_zeros = torch.zeros((n, m))`
<!--ID: 1623065470056-->


How to create torch tensor of ones? #fc 
`x_zeros = torch.ones((n, m))`
<!--ID: 1623065470113-->


How to create torch tensor of random values? #fc 
`x_zeros = torch.rand((n, m))`
<!--ID: 1623065470116-->


How to create a new torch tensor of ones from an existing tensor (same shape and datatype)? #fc
`x = torch.ones_like(x_data)`
<!--ID: 1623065470119-->


How to create a new torch tensor of random values from an existing tensor (same shape), but override the datatype with `torch.float`? #fc
`x = torch.rand_like(x_data, dtype = torch.float)`
<!--ID: 1623065470122-->

What are three attributes of a tensor? #fc 
shape, dtype, device (where the tensor is stored - cpu or gpu)
<!--ID: 1623066260331-->


How to check if a gpu (cuda) is available in pytorch? #fc 
`torch.cuda.is_available()`
<!--ID: 1623066260364-->


How to move a tensor to the gpu (cuda)? #fc 
`tensor = tensor.to('cuda')`
<!--ID: 1623066260369-->


How to concatenate the tensors/arrays `a, b, c` in pytorch/numpy over the dimension `dim`? #fc 
res = torch.cat((a,b,c), dim)
res = np.concatenate((a,b,c), dim)
<!--ID: 1623066260375-->

How to get the column of a numpy array or torch tensor? #fc 
`col = tensor[: , col_index]`
<!--ID: 1623066544756-->


How to matrix multiply two torch tensors `A` and `B` (three ways)? #fc
`y = A @ B` or `y = A.matmul(B)` or `torch.matmul(A,B, out = y)`
<!--ID: 1623066544764-->


How to do elementwise multiplication of two torch tensors `A` and `B` (3 ways)? #fc 
`y = A * B`, `y  = A.mul(B)`, `torch.mul(A, B, out = y)` 
<!--ID: 1623066544767-->


How to get the value out of a single element tensor (for example, after summing)? #fc 
`agg = tensor.sum()`
`agg = agg.item()`
<!--ID: 1623066655534-->

How to preform in place operations on a torch tensor? For example, add `5` elementwise to a tensor in place. #fc 
`tensor.add_(5)`
you append a `_` to the end of the operation.
<!--ID: 1623067213535-->


How to turn a torch tensor, `t`, into a numpy array? #fc 
`n = t.numpy()`
<!--ID: 1623067213577-->


What should be noted about creating a numpy array from a torch tensor, or visa versa, on the cpu? #fc
They share the same memory location, so modifying one will modify the other
<!--ID: 1623067213580-->


How to generate a random number from `0` to `a` inclusive in pytorch? #fc 
`torch.randint(a+1, (1,)).item()`
<!--ID: 1623067213583-->

What is the pytorch namespace that provides all of the building blocks to build a neural network (what do you need to import)? #fc 
`from torch import nn`
<!--ID: 1623068062856-->


What is the name of the function that implements the operation of a `torch.nn` on it's input data? #fc 
`def forward(self, x)` where the input value is `x`. 
<!--ID: 1623068062889-->


What does a linear layer of a neural network do: `nn.Linear(in_features, out_features)`? #fc 
Applies the transformation
$$y = xA^T + b$$ where $x$ is the input and $y$ is the ouput.
<!--ID: 1623068062892-->


How to add the transformation $y = xA^T + b$ to a torch nn, where $x \in \mathbb R^n$ and $y \in \mathbb R^m$? #fc 
`nn.Linear(n, m)`
<!--ID: 1623068062895-->

What is a `ReLU` activation function on the input $x$? #fc 
$$\text{ReLU}(x) = \max(0, x) = (x)^+$$
<!--ID: 1623068799656-->


What is the softmax function applied to an $n$ dimensional tensor? Operationally, what is it good for? #fc 
$$\text{Softmax}(x_i) = \frac{\exp(x_i)}{\sum_j \exp(x_j)}$$
It rescales the output tensor so it's values lie between $0$ and $1$
<!--ID: 1623068799668-->

How to apply Softmax in pytorch along dimension `dim` (such that values along `dim` sum to 1)? #fc 
`softmax = nn.Softmax(dim = dim)(tensor_argument)`
<!--ID: 1623068946181-->


What does `nn.Flatten()` do to a tensor of dimensions $(N, a, b, c, ...)$ #fc 
It flattens everything but the first dimension into a 1-D array:
$$(N, a\times b \times c \times ...)$$
<!--ID: 1623068799671-->

How is the information context function defined, $I(x)$? #fc 
$$I(x) = -\log_b [p_X(x)]$$
where $p_X(x)$ is a probability mass function of random variable $X$. $b$ is the *bit*
<!--ID: 1623070844407-->


What is *Shannon Entropy*, $H(x)$? #fc 
It is the expected information content of the measurment of $X$:
$$H(X) = E[I_X(X)]$$, where $I_X$ is the shannon information content of $X$. 
<!--ID: 1623070844445-->


What is the cross entropy of two probability distributions $p$ and $q$ (which support the same $x \in \mathcal X$), $H(p, q)$? #fc 
$$H(p, q) = - \sum_{x \in \mathcal X} p(x)\log(q(x)) = - E_p[\log(q)] $$
<!--ID: 1623070844450-->


What does cross entropy between an estimated probabilty distribution $q$ and a true distribution $p$ quantify (in words)? #fc 
Simply: the difference between two proability distributions.
It measures the average number of bits (base of the logarithm) needed to identify an event drawn from the set if a coding scheme used for the set is optimized for an estimated probability distrubtion $q$ rather than the true distrubtion $p$.
<!--ID: 1623070844454-->
