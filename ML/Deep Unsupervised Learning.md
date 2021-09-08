TARGET DECK: Main Deck

In maximum likelihood fitting with deep unsupervised learning, how is $p_{\theta}$ represented? #fc 
As a neural network. $\theta$ is the parameters of the neural network.
<!--ID: 1625405957087-->


What is a baysian network? #fc 
It is a direted acyclic graph whose nodes represent the variables in a basian sense: observable quantities. Edges represent conditional dependencies: nodes that are not connected are conditionally independent of one another. Each node has an associated probability function that takes the particular values of the parent node variables and outputs the probability of the variable represented by the node. 
<!--ID: 1625405957119-->


What is the chain rule for probability? #fc 
$$P(A \cap B \cap C) = P(A | B \cap C) P(B | C) P(C)$$
<!--ID: 1625405957122-->


What is an autoregressive model? #fc 
A bayes net structure with the conditional distributions modeled by neural networks.
<!--ID: 1625405957125-->


Why do we model the conditional distribution $p_{\theta}(x_i | \text{parents}(x_i))$ with multiple neural networks, and then use the chain rule to construct $p_\theta(x_i)$? #fc 
Because this is a far easier way to ensure that the probabilities are normalized for each neural network (it only has to output a value from 0 to 1).
<!--ID: 1625405957127-->


What is the name for a model of the form:
$$\log{p_\theta(x)} = \sum_{i=1}^d \log p(x_i | x_{1:i-1})$$ #fc
An *autoregressive* model. Aka a *chain rule* model
<!--ID: 1625405957130-->


What is a *logit*? #fc 
The inverse of a sigmoid function.
<!--ID: 1625405957133-->


Say we have two random variables $x_1$ and $x_2$. How could you model $p(x_1, x_2)$? #fc 
Note $p(x_1, x_2) = p(x_1) p(x_2 | x_1)$. We first fit a histogram to $x_1$ to obtain $p(x_1)$. Then we use a multilayer perceptron to model $p(x_2 | x_1)$, with logits layers followed by a softmax layer. However, this approach is limited because the number of parameters scales as $O(d)$, where $d$ is the dimension of the data (here $d = 2$). 
<!--ID: 1625405957135-->

How can a recurent neural network (RNN) be used to more efficiently predict $x_i$ given $x_{1:i-1}$, only taking in $x_{i-1}$ as an input? #fc 
The RNN first takes in $x_1$ as an input and generates a prediction for $x_2$, while also maintaining an internal state (based on all inputs). Then upon the next input $x_2$, it will use that input and the internal state to generate the next output. This results in parameter sharing between the inputs, because regardless of the input, the input -> hidden state transition has one set of parameters. (so does curr hidden state to next hidden state, and curr hidden state to curr output)
<!--ID: 1625408632487-->


Visualize a RNN for predicting the next character given the previous character (and a hidden state). Where are the parameters stored/shared? #fc 
![[Pasted image 20210704095129.png]]
<!--ID: 1625408632579-->


In the "rasterization method" for generating images pixel by pixel using an RNN, what is a simple change that can be made to ensure that when the raster changes rows, there is continuity in the image? #fc 
Encode the location of the pixel as part of the input to the neural network
<!--ID: 1625408632590-->


What is a de-noising autoencoder? #fc 
It will take in an image that has had noise added to it, and try and predict the original image.
<!--ID: 1625408632597-->


What does MADE stand for, and what is it used for (hint NNs)? #fc 
Masked Autoencoder for Distribution Estimation. Given input variables $x_{1:n}$, the network outputs $p(x_1), p(x_2 | x_1), ..., p(x_n | x_{1:n-1})$. Using the chain rule, this can be used to reconstruct the joint distribution. 
<!--ID: 1625408632603-->


How is a MADE network constructed to ensure that the outputs conform to the rule
$p(x_1), p(x_2 | x_1), ..., p(x_n | x_{1:n-1})$? Visualize the picture. #fc 
The network consists of two types of layers. Type A layers have no horizontal connections between layers, only "downward connections". Type B layers only have "downward connections" (by downward I mean rowwise downward). Here is a picture:
![[Pasted image 20210704102154.png]]
Note that the structure can be artibrary, because each node pictured could have "internal" nodes, all sharing the same connections.
<!--ID: 1625408632608-->


What is the general rule for masking to create a MADE network? #fc 
Any network should be masked such that the property holds that each output is only dependent on the inputs that came before it.
<!--ID: 1625408632612-->


What is the *bits per dim* measurment? #fc 
Take the negative log likelyhood and average it across the number of pixels. Then divide it by $\log{2}$ (recall the nll is usually computed in natural log, so dividing by log base 2 two converts this into log base 2): in python:
`(nll_val / num_pixels) / numpy.log(2)`
<!--ID: 1625415062912-->


How does a masked temporal convolution differ from MADE? #fc 
This network masks part of the convolution kernel to maintain the $p(x_i | x_{1:i-1})$ structure of the network (although these networks may have a limited receptive field, not taking some $x_i$ that are far back as input). Like a regular convolutional nerual network, the weights are shared across the filters for each layer.
<!--ID: 1625415062943-->


What is the core idea behind pixelCNN? #fc 
1. take a 2d image and order its pixels:
![[Pasted image 20210704120824.png]]
2. Setup the filters between convolutional layers such that the MADE-like autoregressive assumptions are preservered between the inputs and output of the network: $p(x_i | x{1: i-1})$
<!--ID: 1625415062947-->


Visualize the 3x3 filter mask that pixelCNN uses to maintain the MADE-like autoregressive assumptions. #fc 
![[Pasted image 20210704121039.png]]
![[Pasted image 20210704121310.png]]
<!--ID: 1625415062950-->

For vanilla pixelCNN, visualize what the blindspot looks like. #fc 
![[Pasted image 20210704121819.png]]
<!--ID: 1625419601062-->


What is the main idea of GatedPixelCNN? #fc 
To combine two streams of convolutions:
1. the vertical stack: a 2x3 convolution, with the center pixel at the position (1,1). Then, on the last layer, this center pixel is brought down 1 row to maintain the autoregressive assumption.
2. The horizontal stack: a 1D masked convolution that gets the information from the lefthandside of the row wrt the center pixel
These two stacks are combined in such a way the the information is propogated from the vertical stack to the horizontal stack (but not in the other direction)
<!--ID: 1625419601120-->


What is the main idea of PixelCNN++? #fc 
Instead of using a softmax output (of size 256, one for the proability of each possible greyscale value), it uses a parameterized probability density function based on the sum of $K$ pdfs, each derived from the cdf of a sigmoid with midpoint $\mu_i$ and slope $s_i$. To get the discrete probabilities, we take the probability mass under the bin corresponding to the pixel value. PixelCNN++ also has *skip connections* to ensure that pixels can *see* pixels from other rows/columns more effectively 
<!--ID: 1625419601124-->


What are skip connections in a neural network? #fc 
Extra connections between nodes that skip one or more layers
<!--ID: 1625419601129-->


What is a query, $q$, in the context of *attention*? #fc 
A vector, usually generated by previous layers. We want to know what parts of this vector should be paid attention.
<!--ID: 1625419601132-->


What does $A(a, K, V)$  equal, where $K$ are the keys and $V$ are the values? #fc 
$$A(q, K, V) = \sum_i \frac{e^{q \cdot k_i}}{\sum_j e^{q\cdot k_j}} v_i$$
Here $k_i$ and $v_i$ are they key and value vectors that make up the columns of $K$ and $V$.
<!--ID: 1625419601135-->


How can autoregressive image generation be sped up (hint: recall that vanilla models have to generate pixel by pixel, and the generation of the subsequent pixel is conditioned on all previous pixels being generated)? #fc 
Break the image up into sections, and compute them in parrellel by ignoring pixels in the other sections, and only conditioning on previously generated pixels *in the same section*.
<!--ID: 1625419601138-->

How can caching be used to speed up autoregressive image generation? #fc 
Save the calculated values from previous iterations (ie. when past pixels were being generated) and use them when applicable to calculate the next pixels.
<!--ID: 1625533317171-->



What is the input to a graph neural network? #fc 
A feature description for every node summarized as an $N \times D$ feature matrix ($N$: number of nodes, $D$: number of input features), a feature description of each edge, and a representation of the graph structure in a matrix form (usually an adjacency matrix)
<!--ID: 1625533317207-->


What is the ouput of a graph neural network? #fc 
An $N \time F$ feature matrix, where $N$ is the number of nodes and $F$ is the number of output features per node
<!--ID: 1625533317211-->


What is a word embedding? #fc 
A representation of a word, typically as a real-valued vector, that encodes the meaning of the word such that the words that are closer in the vector space are expected to be similar in meaning. Neural networks  are (can be) used to generate word embeddings.
<!--ID: 1625533317214-->


If an RNN takes input #1 and hidden state #0 as its inputs on the first step, what does it generate and what will be its input on the next step? #fc 
It generates hidden state #1 and ouput #1, and takes as a next input: Input #2 and hidden state #1
<!--ID: 1625533317216-->


What two major parts make up a sequence to sequence model (like in machine translation)? #fc 
An **encoder** and **decoder**. 
<!--ID: 1625533317219-->


What does the encoder pass to the decoder in sequence to sequence models? #fc 
A context. With attention, this is the final hidden state of the encode after processing all tokens (word embeddings) in it input.
<!--ID: 1625533317222-->


At each time step, what does the encoder get as input and produce as output? #fc 
It gets a word embedding as input and process a hidden state as ouput (a context vector)
<!--ID: 1625533317225-->


In attention seq2seq models, what is different about the information passed between encoder and decoder? #fc 
The encode passes all hidden states (not just the last one) to the decoder
<!--ID: 1625533317227-->


Given multiple contexts, how does an attention decoder determine the context vector at a given time step? (2 steps) #fc
1. look at the encoder hidden states, and the current decoder hidden state, and give each one a score based on the time step (each hidden state is associated with a word)
2. multiply each hidden state by its softmaxed score, and sum them together to get the final context for that time step
<!--ID: 1625533317229-->



















