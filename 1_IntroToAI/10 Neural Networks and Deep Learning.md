### <mark style="background: #69E7E4;">Learning:</mark>

Can <mark style="background: #69E7E4;">devise learning algorithms</mark> which can automatically tune the weights and biases of a network of artificial neurons.

this tuning happens in response to external stimuli, without direct intervention by a programmer.

These learning algorithms enable us to use artificial neurons in a way which is radically different to conventional logic gates.

Instead of explicitly laying out a circuit of NAND and other gates, our neural networks can simply learn to solve problems, sometimes problems where it would be extremely difficult to directly design a conventional circuit.

### <mark style="background: #69E7E4;">Sigmoid Neurons:</mark>

How to obtain a learning algorithm?

Suppose we make a small change in some weight (or bias) in the network. What we'd like is for this small change in weight to cause only a small corresponding change in the output from the network.

![](https://i.imgur.com/nmZNtbr.png)

Could figure out how to make a small change in the weights and biases so the network gets a little closer to classifying the image as a "9". And then we'd repeat this, changing the weights and biases over and over to produce better and better output. The network would be learning.

Not what happens with perceptrons

Small change in the weights or bias of any single perceptron in the network can sometimes cause the output of that perceptron to completely flip, say from 0 to 1.

That flip may then cause the behaviour of the rest of the network to completely change in some very complicated way.

Hard to see how small changes can lead gradually to solution.

We can overcome this problem by introducing a new type of artificial neuron called a sigmoid neuron. Same notation as before.

Instead of being just 0 or 1, these inputs can also take on any values between 0 and 1

Output is not 0 or 1. Instead, it's σ(w⋅x+b), where σ is called the sigmoid function.

![](https://i.imgur.com/97wraS6.png)

# <mark style="background: #FF5582A6;">Slide 6 page 3</mark>
