# Prediction Template Learning
Prediction Template Learning (PTL) is an online machine learning algorithm that makes predictions about the environment to improve itself.

[Theory (Self-Organizing Predictions)](https://github.com/CarsonScott/self-organizing-predictions)

[Learning Algorithm ](https://github.com/CarsonScott/TLearner)

## System Structure
States are stored in state-pairs as "templates". A state-pair represents a state transition from an initial state to the following state. The state templates are adjusted according to some measured error between the ideal (stored) and measured (actual) input. This expectation-maximization process drives the system toward the lowest possible error measurement between ideal and measured states.

The structure is an abstraction of a multilayer perceptron in which the state-pairs correspond with hidden units and the predicted state values with output units. The input layer remains the same (i.e. propagates signals from the environment to the hidden layer).

At each time step the PTL has three main responsibilities. First, the input is compared to a selected state (prediction) from the previous time step. The prediction's state-pair (for which it is the final state) is updated to better resemble the measured input. 
Second, the input is compared to the initial states for each state-pair. The similarities are computed to select the best state-pair, and the final state is set as the prediction for the following time step. 
Finally, the selected state-pair's initial state is compared to the input and updated to better resemble to measured state.

PTL distinguishes itself from MLP's through its learning/adaptation method. The hidden layer is the only adaptable component and is responsible for the network's development as a whole. Hidden units are updated by comparing the predicted initial and final states to the actual states and correcting the error. The adjusted state-pair has a closer resemblence to the measured states, and thus provides more accurate predictions for the future.

## Data
Now for some data collected while running tests. To test PTL's prediction ability, I generated random sequences of inputs and fed it to the algorithm, then calculated and plotted the error at each time step. 

In this test, each input vector is exactly 10 values long, and the sequence is 100 inputs in total.
![Fig. 1](https://github.com/CarsonScott/Prediction-Template-Learning/blob/master/img/figure_1.png)
Fig. 1

As you can see, the error rate decays exonentially and, given enough time to train, converges to zero. This next test also contains a 100-input sequence, however the inputs are now 50 values long instead of 10. 

![Fig. 2](https://github.com/CarsonScott/Prediction-Template-Learning/blob/master/img/figure_2.png)
Fig. 2

This time I've doubled the inputs in a sequence, raising the the total number of patterns the algorithm must learn to two-hundred.

![Fig. 3](https://github.com/CarsonScott/Prediction-Template-Learning/blob/master/img/figure_3.png)
Fig. 3

It takes roughly twice as long to learn double the amount of information from the previous tests. Time spent learning appears to scale linearly with the amount of material that needs to be retained, which reflects the way humans learn.

I raised the input size back up to 50 and kept the length of the sequence at 200.

![Fig. 4](https://github.com/CarsonScott/Prediction-Template-Learning/blob/master/img/figure_4.png)
Fig. 4
