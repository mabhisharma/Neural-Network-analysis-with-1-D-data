# 1-D-data-analysis-with-Neural-Net
Analysis of how Neural Networks transform the data so that non linear classification boundary can be learned

<p>To get a better sense of what’s going on, let’s consider an dataset that’s 1-dimensional: </p>
<p>Class A - [-1/3, 1/3]</p>
<p>Class B - [-1, -2/3] &cup; [2/3, 1]</p>

The representation of the data can be shown as follows -
</br>
<p align="center">
  <img src="/Plots/One-Dimensional-data.png" alt="One dimensional data with two classes" height="300" width="400" />
</p>

<p> I have taken 500 samples from each class. As we can see this One Dimensional data cannot be seperated using a linear boundary. So if we use Neural Network with 2 layers i.e. Hidden Layer and Output Layer (input layer not included in number of layers), with Hidden Layer having only 1 hidden unit, we will not be able to classify this one dimensional data. To classify this one dimensional data we will require minimum 2 hidden units.</p>

# Network Details
<p> In order to classify this particular data we will require minimum 2 hidden units in the hidden layer. So our network becomes</br> Input layer which is one dimensional, Hidden layer with 2 units and Output layer which outputs 0 or 1 classifing the data into Class A or Class B. The activation function we will use in the hidden layer is Tanh and activation function used in the output layer is sigmoid because we want to classify input as 0 and 1. Also to understand what this neural network is doing we will simply store the output from hidden layer. We will use gradient descent procedure to optimize the weights and bias vectors. Now as the hidden layer has 2 units, the input has transformed into 2 dimensional data and which we store output in every gradient descent step. We also store the weights and bias vectors of layer 2. Now see the diagram for the neural network below</p>
<p align="center">
  <img src="/Plots/1-D-NN.PNG" alt="Neural Network for 2 class problem" height="200" width="300" />
</p>
<p>Now if we only consider the hidden layer and output layer, this neural network becomes more like a logistic regression problem where we try to find a linear boundary which is a straight line in our 2-Dimesional (hidden layer) data. So now if we plot our data from hidden units and linear boundary (which is straight line with weights as coefficients and bias as constant in aX1 + bX2 + c = 0 equation) for each gradient decent step we get following output.</p>
<p align="center">
  <img src="/Plots/1-ddata-tranformation.gif" alt="Transformation of 1-D data to 2-D and decision boundary" height="300" width="400" />
</p>
<p>The above GIF clearly demonstrates that we are able to find a linear decision boundary in this 2 dimensional data (hidden layer output). The original data which was one dimensional was projected to the 2-D space using 2 units in the hidden layer. The original data was not linearly seperable but when we projected 2 dimensional space our data became linearly seperable and this is how the neural network learned to classify a non linearly seperable data. </p>

<p>The code for this analysis is my work
# References -
http://colah.github.io/posts/2014-03-NN-Manifolds-Topology/
</p>


# Mathematical model for neural net
For one example \(x^{(i)}\):
\[z^{[1] (i)} =  W^{[1]} x^{(i)} + b^{[1] (i)}\tag{1}\]
\[a^{[1] (i)} = \tanh(z^{[1] (i)})\tag{2}\]
\[z^{[2] (i)} = W^{[2]} a^{[1] (i)} + b^{[2] (i)}\tag{3}\]
\[\hat{y}^{(i)} = a^{[2] (i)} = \sigma(z^{ [2] (i)})\tag{4}\]
\[y^{(i)}_{prediction} = \begin{cases} 1 & \mbox{if } a^{[2](i)} > 0.5 \\ 0 & \mbox{otherwise } \end{cases}\tag{5}\]

Given the predictions on all the examples, you can also compute the cost
\(J\) as follows:
\[J = - \frac{1}{m} \sum\limits_{i = 0}^{m} \large\left(\small y^{(i)}\log\left(a^{[2] (i)}\right) + (1-y^{(i)})\log\left(1- a^{[2] (i)}\right)  \large  \right) \small \tag{6}\]
