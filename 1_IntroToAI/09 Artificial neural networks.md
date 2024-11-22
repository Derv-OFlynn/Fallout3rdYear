![](https://i.imgur.com/0ddZLd2.png)

Artificial neural nets have a number of properties that make them an attractive alternative to traditional problem-solving techniques. The two main alternatives to using neural nets are to develop an algorithmic solution, and to use an expert system.

Algorithmic methods arise when there is sufficient information about the data and the underlying theory. By understanding the data and the theoretical relationship between the data, we can directly calculate unknown solutions from the problem space. Ordinary von Neumann computers can be used to calculate these relationships quickly and efficiently from a numerical algorithm.

Expert systems, by contrast, are used in situations where there is insufficient data and theoretical background to create any kind of a reliable problem model. In these cases, the knowledge and rationale of human experts is codified into an expert system. Expert systems emulate the deduction processes of a human expert, by collecting information and traversing the solution space in a directed manner. Expert systems are typically able to perform very well in the absence of an accurate problem model and complete data. However, where sufficient data or an algorithmic solution is available, expert systems are a less than ideal choice.

Artificial neural nets are useful for situations where there is an abundance of data, but little underlying theory. The data, which typically arises through extensive experimentation may be non-linear, non-stationary, or chaotic, and so may not be easily modelled. Input-output spaces may be so complex that a reasonable traversal with an expert system is not a satisfactory option.

Importantly, neural nets do not require any a priori assumptions about the problem space, not even information about statistical distribution. Though such assumptions are not required, it has been found that the addition of such a priori information as the statistical distribution of the input space can help to speed training. Many mathematical problem models tend to assume that data lies in a standard distribution pattern, such as Gaussian or Maxwell-Boltzmann distributions. Neural networks require no such assumption. During training, the neural network performs the necessary analytical work, which would require non-trivial effort on the part of the analyst if other methods were to be used.

![](https://i.imgur.com/twGoaWW.png)

![](https://i.imgur.com/oMLfA04.png)

![](https://i.imgur.com/iHpvzon.png)

### <mark style="background: #69E7E4;">Perceptron:</mark>

The perceptron is the simplest form of a neural network. It consists of a single neuron with adjustable synaptic weights and a hard limiter 

<mark style="background: #69E7E4;">Single-layer two-input perceptron:</mark>
![](https://i.imgur.com/No7Ye6d.png)

Can be used to compute AND, OR but not exclusive or ( XOR). This is because it is geometrically equivalent to a hyperplane and the inputs can only be on one side or the other of a plane, XOR would require a region between 2 planes.

### <mark style="background: #69E7E4;">Perceptron Training Algorithm:</mark>

1. Start a training set of inputs x<sub>i</sub> and expected outputs Y<sub>d</sub>.
2. Pick some random values from [-0.5, +0.5] for initial weights w<sub>i</sub>
3. Compute weighted sum and actual output Y with 
![](https://i.imgur.com/tWA1HjU.png)
 and ![](https://i.imgur.com/tNsloBj.png)
4. Compare Y with expected output Y<sub>d</sub> to find the error 
![](https://i.imgur.com/Pl29UxQ.png)
5. Use error to calculate adjustments to ![](https://i.imgur.com/oVig9qO.png)
6. Then update the weights for the next iteration ![](https://i.imgur.com/RuNZGmR.png)
7. Iterate steps 3 to 6 to minimise the error. Then the weights arrived at can be used in your perceptron where
![](https://i.imgur.com/3U9PncB.png)

Know that in Nielsen, the output is 0 if weighted sum ≤ threshold (or weighted sum + bias ≤ 0)

θ is the threshold, η is the learning constant (Negnevitsky calls it α)

(theta θ, eta η and alpha α)

### <mark style="background: #69E7E4;">Logical AND:</mark>

To be completed by the student:
- Threshold θ = 0.2 , 
- learning rate η = 0.1.

![](https://i.imgur.com/jr3btqb.png)

![](https://i.imgur.com/7BpWLJf.png)

### <mark style="background: #69E7E4;">Logical OR:</mark>
To be completed by the student
- Threshold θ = 0.2 , 
- learning rate η = 0.1.

![](https://i.imgur.com/BvHXEYT.png)
![](https://i.imgur.com/yU0PeIq.png)
