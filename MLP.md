# Introduction #

Multilayer Perceptron (MLP) is probably one of the best known Artificial Neural Networks (ANN) algorithms. Therefore you can find information about it in virtually any machine learning text. For general information see [wikipedia](http://en.wikipedia.org/wiki/Multilayer_perceptron).

In summary, MLP is a feedforward topology which predictions depend on the weight assigned to each neuron connection. It has been shown useful to achieve non-linear discrimination, and it has been widely used in the prosthetic control research.

# Implementation #

Settings such as learning rate (eta) and ANN topology can be done in the main function `ANN_Perceptron`.

  * Automatic reset after a given number of iterations without convergence (set by nRepF)
  * Batch or stochastic training (set by batchTr)
  * The number of hidden layers and hidden neurons can be easily modify in the nHn matrix.
    * 1 hidden layer with 10 neurons -> `nHn = 10`;
    * 3 hidden layer with 10 neurons each -> `nHn = [10 10 10]`;
    * 2 hidden layer with different neurons each -> `nHn = [6 14]`;

NOTE: The number of hidden neurons can be different for each hidden layers. It also can be smaller than the number of input neurons if several layers exist, however `nHn = nIn/2` will cause an error. In any case, a rule of thumb is to use at least the same number of hidden neurons as input neurons.

If you want to edit the number of hidden neurons without restrictions, there need to be some changes in the following functions:
In ANN\_Perceptron change line 52 to this line:

`ANN.w(1:max([nHn nIn nOn]),1:max([nHn nOn]),1:length(nHn)+1) = -1 + rand(max([nHn nIn nOn]),max([nHn nOn]),length(nHn)+1) .* 2;  % weight`

And in Init\_ANN\_Perceptron change ANN.w and ANN.dw to

`ANN.w       = zeros(max([nHn nIn nOn]),max([nHn nOn]),length(nHn)+1);  % weight`

`ANN.dw      = zeros(max([nHn nIn nOn]),max([nHn nOn]),length(nHn)+1);  % capital delta weight or change in weight`

Because nIn should only concern the first dimension (inputlayer). If used in the 2nd dimension of the weight matrix (as in the original code) there will be an error that matrix dimensions don't agree if nHn < nIn.


## Training Algorithms ##

  * Backpropagation (default)
  * Particle Swarm Optimization
    * Not good for over 4 movements

## Default settings ##

Although several algorithms have been implemented to train the MLP, so far the best results have been found with:

Backpropagation
  * Eta = 0.1
  * `nHn = [nIn nIn]`
  * batchTr = 0

# Functions roadmap #
## Training ##

  * `ANN_Perceptron`
    * `InitANN_Perceptron`
    * `EvaluateANN`
    * Training algorithm:
      * Backpropagation, or
        * `Backpropagation`
      * PSO, or
        * `InitPSO_MLP`
        * `PSO_MLP`
          * `Pos2W`
          * `FitnessANN`
            * `EvaluateANN`
      * ...
    * `FastTestANN`
      * `EvaluateANN`
    * `FullTestANN`
      * `EvaluateANN`

## Testing ##

  * `MLPTest`
    * `EvaluateANN`