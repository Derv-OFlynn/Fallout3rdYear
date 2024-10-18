### <mark style="background: #69E7E4;">Neural Networks & Deep Learning - Nielsen</mark>

<mark style="background: #69E7E4;">NN vs conventional program</mark>
- In conventional coding, we tell the computer what to do, breaking big problems up into many small, precisely defined tasks that the computer can easily perform
- By contrast, in a neural network we don't tell the computer how to solve our problem. Instead, it learns from observational data, figuring out its own solution to the problem at hand.

### <mark style="background: #69E7E4;">Underlying Principle:</mark>

Better to obtain a solid understanding of the core principles of neural networks and deep learning, rather than a hazy understanding of a long laundry list of ideas.

Learning a library can have immediate payoff but technologies come and go

If you understand the core ideas well, you can rapidly understand other new material

Book is not a tutorial in how to use some particular neural network library

### <mark style="background: #69E7E4;">Mathematics - how much?</mark>

![](https://i.imgur.com/ko6fmQX.png)

### <mark style="background: #69E7E4;">Some History:</mark>

In 1989, Yann LeCun et al. applied the standard backpropagation algorithm, which had been around since 1970, to a deep neural network with the purpose of recognizing handwritten ZIP codes on postal mail. Training required 3 days.

The impact of deep learning in industry began in the early 2000s, when CNNs already processed an estimated 10% to 20% of all the checks written in the US, according to Yann LeCun.

Industrial applications of deep learning to large-scale speech recognition started around 2010.

Advances in hardware have driven renewed interest in deep learning. In 2009, Nvidia was involved in what was called the “big bang” of deep learning, “as deep-learning neural networks were trained with Nvidia graphics processing units (GPUs).” That year, Google Brain used Nvidia GPUs to create capable DNNs.

While there, Andrew Ng determined that GPUs could increase the speed of deep-learning systems by about 100 times. In particular, GPUs are well-suited for the matrix/vector computations involved in machine learning.

GPUs speed up training algorithms by orders of magnitude, reducing running times from weeks to days

In March 2019, Yoshua Bengio, Geoffrey Hinton and Yann LeCun were awarded the Turing Award for conceptual and engineering breakthroughs that have made deep neural networks a critical component of computing.

### <mark style="background: #69E7E4;">Chapter 1 Extract:</mark>

Using neural nets to recognise handwritten digits

![](https://i.imgur.com/eAHoZiV.png)

In each brain hemisphere, humans have a primary visual cortex, also known as V1, containing 140 million neurons, with tens of billions of connections between them.

Human vision involves not just V1, but an entire series of visual cortices - V2, V3, V4, and V5 - doing progressively more complex image processing.

The difficulty of visual pattern recognition becomes apparent if you attempt to write a computer program to recognize digits like those above. What seems easy when we do it ourselves suddenly becomes extremely difficult.

Simple intuitions about how we recognize shapes - "a 9 has a loop at the top, and a vertical stroke in the bottom right" - turn out to be not so simple to express algorithmically.

Neural networks approach the
problem in a different way.

The idea is to take a large number of handwritten digits, known as training examples.

Then develop a system which can learn from those training examples.

![](https://i.imgur.com/jiqoaYK.png)

In other words, the neural network uses the examples to automatically infer rules for recognizing handwritten digits.

Furthermore, by increasing the number of training examples, the network can learn more about handwriting, and so improve its accuracy.

MNIST 70,000 28 by 28 pixel images

Here in chapter 1, 74 lines of code achieves 96% accuracy

Improvements in later chapters – 99%

Recognising handwritten digits is challenging but not too difficult in terms of design and computational power

### <mark style="background: #69E7E4;">Perceptrons:</mark>

Developed in the 1950s and 1960s by the scientist Frank Rosenblatt, inspired by earlier work by Warren McCulloch and Walter Pitts

More common today to use other models of artificial neurons, the main neuron model used is one called the <mark style="background: #69E7E4;">sigmoid neuron</mark>.

A perceptron takes several binary inputs, x1,x2,..., and produces a single binary output:
![](https://i.imgur.com/vwNFXFx.png)

### <mark style="background: #69E7E4;">Perceptron rule:</mark>

Rosenblatt proposed a simple rule to compute the output, introduced weights

<mark style="background: #69E7E4;">Weighted sum:</mark>
![](https://i.imgur.com/fESB2ge.png)

![](https://i.imgur.com/QwxXH9I.png)

### <mark style="background: #69E7E4;">How to think of a perceptron:</mark>

You can think about the perceptron is that it's a device that makes decisions by weighing up evidence

E.g. a cheese festival in your city. You like cheese, and are trying to decide whether or not to go to the festival.

Make your decision by weighing up three factors
- Is the weather good x1
- Does friend want to go with you x2
- Public transport availability x3

### <mark style="background: #69E7E4;">Cheese festival example:</mark>

You like cheese very much, but no way would you go in bad weather, even with friend and if public transport available.

model this kind of decision-making by choose a weight w<sub>1</sub>=6 for the weather, and w<sub>2</sub>=2 and w<sub>3</sub>=2 for the other conditions.

w<sub>1</sub> = 6 means weather matter more than other factors

Suppose you choose a threshold of 5

Then perceptron implements the desired decision-making model, outputting 1 whenever the weather is good, and 0 whenever the weather is bad.

Suppose we instead chose a threshold of 3. Then what?

### <mark style="background: #69E7E4;">Multi-layer Perceptrons MLP:</mark>

Single perceptron isn't a complete model of human decision-making.

Example illustrates is how a perceptron can weigh up different kinds of evidence in order to make decisions.

Seem plausible that a complex network of perceptrons could make quite subtle decisions.

![](https://i.imgur.com/qdQwPTY.png)

In this network, the first column of perceptrons - what we'll call the first layer of perceptrons - is making three very simple decisions, by weighing
the input evidence.

In 2nd layer, each perceptron is making a decision by weighing up the results from the first layer of decision-making.

Second layer can make a decision at a more complex and more abstract level than perceptrons in the first and so on.

Thus a many-layer network of perceptrons can engage in sophisticated decision making.

### <mark style="background: #69E7E4;">Dot Product + Bias:</mark>

Can simplify the way we describe perceptrons

<mark style="background: #69E7E4;">Write:</mark>
![](https://i.imgur.com/O144d3j.png)

<mark style="background: #69E7E4;">Dot product:</mark>
![](https://i.imgur.com/Nszlhgx.png)

<mark style="background: #69E7E4;">Then:</mark>
![](https://i.imgur.com/8MPJO1T.png)

Can think of the bias as a measure of how easy it is to get the perceptron to output a 1. Or to put it in more biological terms, the bias is a measure of how easy it is to get the perceptron to <mark style="background: #69E7E4;">fire</mark>

<mark style="background: #69E7E4;">Perceptron as Logic NAND:</mark>

Another way perceptrons can be used is to compute the elementary logical functions we usually think of as underlying computation, functions such as AND, OR, and NAND (not AND).

<mark style="background: #69E7E4;">For example:</mark>
![](https://i.imgur.com/YOKoUPe.png)

Shows that we can use perceptrons to compute simple logical functions.

### <mark style="background: #69E7E4;">Universal computation:</mark>

NAND gate is universal for computation, that is, we can build any computation up out of NAND gates and hence of perceptrons.

<mark style="background: #69E7E4;">For example, to add two bits:</mark>
![](https://i.imgur.com/wqN9SWc.png)

### <mark style="background: #69E7E4;">Adding with Perceptrons:</mark>

To get an equivalent network of perceptrons we replace all the NAND gates by perceptrons with two inputs, each with weight −2, and an overall bias of 3.

![](https://i.imgur.com/eDthl9x.png)

### <mark style="background: #69E7E4;">Adding two bits:</mark>

Can simplify to:

![](https://i.imgur.com/mlZNoWR.png)

### <mark style="background: #69E7E4;">Input layer:</mark>

Conventional to draw an extra layer of perceptrons - the input layer -to encode the inputs:
![](https://i.imgur.com/Y1h3TUk.png)

We see that perceptrons are also universal for computation.

Powerful but are they merely a new type of NAND gate?

### <mark style="background: #69E7E4;">Learning:</mark>

Can devise <mark style="background: #69E7E4;">learning algorithms</mark> which can automatically tune the weights and biases of a network of artificial neurons.

This tuning happens in response to external stimuli, without direct intervention by a programmer.

These learning algorithms enable us to use artificial neurons in a way which is radically different to conventional logic gates.

Instead of explicitly laying out a circuit of NAND and other gates, our neural networks can simply learn to solve problems, sometimes problems where it would be extremely difficult to directly design a conventional circuit.