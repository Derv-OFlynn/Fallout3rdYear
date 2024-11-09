
### <mark style="background: #69E7E4;">Introduction, or how the brain works</mark>

Machine learning involves adaptive mechanisms that enable computers to learn from experience, learn by example and learn by analogy. Learning capabilities can improve the performance of an intelligent system over time. The most popular approaches to machine learning are <mark style="background: #69E7E4;">artificial neural networks</mark> and <mark style="background: #69E7E4;">genetic algorithms</mark>. This lecture is dedicated to neural networks.

A <mark style="background: #69E7E4;">neural network</mark> can be defined as a model of reasoning based on the human brain. The brain consists of a densely interconnected set of nerve cells, or basic information-processing units, called <mark style="background: #69E7E4;">neurons</mark>.

The human brain incorporates nearly 86 billion neurons and about 150 trillion connections, <mark style="background: #69E7E4;">synapses</mark>, between them. By using multiple neurons simultaneously, the brain can perform its functions much faster than the fastest computers in existence today.

Each neuron has a very simple structure, but an army of such elements constitutes a tremendous processing power.

A neuron consists of a cell body, <mark style="background: #69E7E4;">soma</mark>, a number of fibres called <mark style="background: #69E7E4;">dendrites</mark>, and a single long fibre called the <mark style="background: #69E7E4;">axon</mark>.

### <mark style="background: #69E7E4;">Biological neural network:</mark>

![](https://i.imgur.com/6sBC2Ki.png)

A <mark style="background: #69E7E4;">neuron</mark> or nerve cell is an electrically excitable cell that processes and transmits information through electrical and chemical signals. A typical neuron consists of a cell body (soma), dendrites, and an axon.

A <mark style="background: #69E7E4;">synapse</mark> is a structure that permits a neuron to pass an electrical or chemical signal to another neuron. These signals between neurons occur via synapses, specialized connections with other cells. Neurons can connect to each other to form neural networks.

At a synapse, signals are sent from the axon of one neuron to a dendrite of another.

An axon is a long, slender projection of a nerve cell, or neuron, that typically conducts electrical impulses away from the neuron's cell body.

Dendrites are the branched projections of a neuron that act to propagate the electrochemical stimulation received from other neurons to the cell body or soma of the neuron from which the dendrites project. Electrical stimulation is transmitted onto dendrites by the axons of other neurons via synapses which are located at various points throughout the dendritic tree.

Our brain can be considered as a highly complex, non-linear and parallel information-processing system.

Information is stored and processed in a neural network simultaneously throughout the whole network, rather than at specific locations. In other words, in neural networks, both data and its processing are <mark style="background: #69E7E4;">global</mark> rather than local.

Learning is a fundamental and essential characteristic of biological neural networks. The ease with which they can learn led to attempts to emulate a biological neural network in a computer.

An artificial neural network consists of a number of very simple processors, also called <mark style="background: #69E7E4;">neurons</mark>, which are analogous to the biological neurons in the brain.

The neurons are connected by weighted links passing signals from one neuron to another.

The output signal is transmitted through the neuron’s outgoing connection. The outgoing connection splits into a number of branches that transmit the same signal. The outgoing branches terminate at the incoming connections of other neurons in the network.

### <mark style="background: #69E7E4;">Architecture of a typical artificial neural network:</mark>

![](https://i.imgur.com/sF4oKYb.png)

### <mark style="background: #69E7E4;">Analogy between biological and artificial neural networks:</mark>

![](https://i.imgur.com/ktSEFVJ.png)

### <mark style="background: #69E7E4;">The neuron as a simple computing element:</mark>

![](https://i.imgur.com/bajThRP.png)

The neuron computes the weighted sum of the input signals and compares the result with a <mark style="background: #69E7E4;">threshold value</mark>, q. If the net input is less than the threshold, the neuron output is -1. But if the net input is greater than or equal to the threshold, the neuron becomes activated and its output attains a value +1.

The neuron uses the following transfer or <mark style="background: #69E7E4;">activation function</mark>:

![](https://i.imgur.com/MjVULkr.png)

This type of activation function is called a sign function.

### <mark style="background: #69E7E4;">Activation functions of a neuron:</mark>

![](https://i.imgur.com/ISl3VDB.png)

### <mark style="background: #69E7E4;">Can a single neuron learn a task?</mark>

In 1958, Frank Rosenblatt introduced a training algorithm that provided the first procedure for training a simple ANN: a <mark style="background: #69E7E4;">perceptron</mark>.

The perceptron is the simplest form of a neural network. It consists of a single neuron with <mark style="background: #69E7E4;">adjustable</mark> synaptic weights and a <mark style="background: #69E7E4;">hard limiter</mark>.

### <mark style="background: #69E7E4;">Single-layer two-input perceptron:</mark>

![](https://i.imgur.com/otnz3KT.png)

### <mark style="background: #69E7E4;">The Perceptron:</mark>

The operation of Rosenblatt’s perceptron is based on the <mark style="background: #69E7E4;">McCulloch and Pitts neuron model</mark>. The model consists of a linear combiner followed by a hard limiter.

The weighted sum of the inputs is applied to the hard limiter, which produces an output equal to +1 if its input is positive and −1 if it is negative.

The aim of the perceptron is to classify inputs, x1, x2, . . ., xn, into one of two classes, say A1 and A2.

In the case of an elementary perceptron, the n-dimensional space is divided by a hyperplane into two decision regions. The hyperplane is defined by the linearly separable function:

![](https://i.imgur.com/sRGFTpn.png)

### <mark style="background: #69E7E4;">Linear separability in the perceptrons:</mark>

![](https://i.imgur.com/9DMnUoY.png)

### <mark style="background: #69E7E4;">How does the perceptron learn its classification tasks?</mark>

This is done by making small adjustments in the weights to reduce the difference between the actual and desired outputs of the perceptron. The initial weights are randomly assigned, usually in the range [−0.5, 0.5], and then updated to obtain the output consistent with the training examples.

If at iteration p, the actual output is Y(p) and the
desired output is Y<sub>d</sub> (p), then the error is given by:

![](https://i.imgur.com/kJuOMK2.png)

### <mark style="background: #69E7E4;">The perceptron learning rule:</mark>

![](https://i.imgur.com/5PpG9Oz.png)

where p = 1, 2, 3, . . .

<mark style="background: #69E7E4;">α</mark> is the <mark style="background: #69E7E4;">learning rate</mark>, a positive constant less than unity.

The perceptron learning rule was first proposed by Rosenblatt in 1960. Using this rule we can derive the perceptron training algorithm for classification tasks.

### <mark style="background: #69E7E4;">Perceptron's training algorithm:</mark>

<mark style="background: #69E7E4;">Step 1: Initialisation</mark>
- Set initial weights w1, w2,…, wn and threshold θ to random numbers in the range [−0.5, 0.5].
- If the error, e(p), is positive, we need to increase perceptron output Y(p), but if it is negative, we need to decrease Y(p).

<mark style="background: #69E7E4;">Step 2: Activation</mark>
- Activate the perceptron by applying inputs x1(p), x2(p),…, xn(p) and desired output Yd (p). 
- Calculate the actual output at iteration p = 1, where n is the number of the perceptron inputs, and step is a step activation function.
![](https://i.imgur.com/Fxwb5Aw.png)

<mark style="background: #69E7E4;">Step 3: Weight training</mark>
- Update the weights of the perceptron where Dwi(p) is the weight correction at iteration p.
- ![](https://i.imgur.com/fmOfzeu.png)
- The weight correction is computed by the delta rule:
- ![](https://i.imgur.com/HlT6UXp.png)

<mark style="background: #69E7E4;">Step 4: Iteration</mark>
- Increase iteration p by one, go back to Step 2 and repeat the process until convergence

### <mark style="background: #69E7E4;">Example of perceptron learning: the logical operation AND:</mark> 

![](https://i.imgur.com/r1UBywa.png)

### <mark style="background: #69E7E4;">Two Dimensional plots of basic logical operations</mark>

![](https://i.imgur.com/m2K9AaC.png)

A perceptron can learn the operations AND and OR, but not Exclusive-OR.

### <mark style="background: #69E7E4;">Multilayer neural networks</mark>

A multilayer perceptron is a feedforward neural network with one or more hidden layers.

The network consists of an <mark style="background: #69E7E4;">input layer</mark> of source neurons, at least one middle or <mark style="background: #69E7E4;">hidden layer</mark> of computational neurons, and an <mark style="background: #69E7E4;">output layer</mark> of computational neurons.

The input signals are propagated in a forward direction on a layer-by-layer basis.

### <mark style="background: #69E7E4;">Multilayer perceptron with two hidden layers:</mark>

![](https://i.imgur.com/RjyDY4i.png)

### <mark style="background: #69E7E4;">What does the middle layer hide?</mark>

A hidden layer “hides” its desired output Neurons in the hidden layer cannot be observed through the input/output behaviour of the network.

There is no obvious way to know what the desired output of the hidden layer should be.

Commercial ANNs incorporate three and sometimes four layers, including one or two hidden layers. Each layer can contain from 10 to 1000 neurons. Experimental neural networks may have five or even six layers, including three or four hidden layers, and utilise millions of neurons.

### <mark style="background: #69E7E4;">Back-propagation neural network:</mark>

Learning in a multilayer network proceeds the same way as for a perceptron.

A training set of input patterns is presented to the network.

The network computes its output pattern, and if there is an error − or in other words a difference between actual and desired output patterns − the weights are adjusted to reduce this error.

In a back-propagation neural network, the learning algorithm has two phases.

First, a training input pattern is presented to the network input layer. The network propagates the input pattern from layer to layer until the output pattern is generated by the output layer.

If this pattern is different from the desired output, an error is calculated and then propagated backwards through the network from the output layer to the input layer. The weights are modified as the error is propagated.

### <mark style="background: #69E7E4;">Three-layer back-propagation neural network:</mark>

![](https://i.imgur.com/6wgiq11.png)

<mark style="background: #69E7E4;">Step 4: Iteration</mark>
Increase iteration p by one, go back to Step 2 and repeat the process until the selected error criterion is satisfied.

As an example, we may consider the three-layer back-propagation network. Suppose that the network is required to perform logical operation <mark style="background: #69E7E4;">Exclusive-OR</mark>. Recall that a single-layer perceptron could not do this operation. Now we will apply the three-layer net.

### <mark style="background: #69E7E4;">Three-layer network for solving the Exclusive-OR operation</mark>

![](https://i.imgur.com/wgPXtKg.png)

### <mark style="background: #69E7E4;">Learning curve for operation Exclusive-OR:</mark>

![](https://i.imgur.com/4WjJftO.png)

### <mark style="background: #69E7E4;">Final Results of three-layer network learning:</mark>

![](https://i.imgur.com/iiTu2u7.png)

### <mark style="background: #69E7E4;">Network represented by McCulloch-Pitts model for solving the Exclusive-OR operation:</mark>

![](https://i.imgur.com/EZZOUeX.png)

### <mark style="background: #69E7E4;">Decision boundaries:</mark>

![](https://i.imgur.com/gV29LQY.png)

(a) Decision boundary constructed by hidden neuron 3;
(b) Decision boundary constructed by hidden neuron 4;
(c) Decision boundaries constructed by the complete three-layer network

### <mark style="background: #69E7E4;">Accelerated learning in multilayer neural networks</mark>

A multilayer network learns much faster when the sigmoidal activation function is replaced by a <mark style="background: #69E7E4;">hyperbolic tangent</mark>

We also can accelerate training by including a momentum term in the delta rule:
![](https://i.imgur.com/x0BIv8Q.png)

# <mark style="background: #FF5582A6;">SLIDE 21</mark>

