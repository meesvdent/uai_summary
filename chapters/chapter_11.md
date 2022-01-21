chapter_11

# Lecture 11: dynamic models

## Goal: inference in dynamic models
![](chapter_11/image621.png)
The goal of inference in stochastic dynamic models is to get the probability distribution of the state.

## Markov models
### Markov property
![](chapter_11/image622.png)
* If the future states given all previous states only depend on the present state and not past state, the Markov property holds.
* In reality the state dimensions might get too large to store all of the information in one state. In that case you might chose to let the future states also depend on the previous n-states.

### Query types on dynamic models
![](chapter_11/image625.png)
* Filtering: what is the probability distribution on the present state, given all previous states.
* Smoothing: what is probability distribution of a past state, given states before and after this state.
* Prediction: what is the probability distribution on future states, given all states up until now.

### Order of Markov models
![](chapter_11/image628.png)
* The order of a Markov model is determined by the number of previous states on which the current state depends.
* In first order Markov models, the present is only dependent on one previous step.
* In second order Markov models, the present is only dependent on the previous step and the step before that, given those two steps, given all previous steps.

### Stationary Markov chains
![](chapter_11/image632.png)
* In a stationary Markov model, the transition probabilities are constant and do not chance over time.
* In a discrete first order Markov chain, the following properties hold:
	* chain of state
	* states are discrete
	* each state only depends on the previous state given all previous states
	* transition probabilities are constant in each state

### State transition matrix
![](chapter_11/image635.png)
* When state transition probabilities are constant over time, therefore the model is a stationary model, the state transitions can be visualised in a state transition matrix and graph.

### Stationary hidden Markov model
![](chapter_11/image638.png)
In a stationary hidden Markov model, both the state transition matrix and the emission matrix do not change over time.

## Inference in hidden Markov models
![](chapter_11/image639.png)
* Filtering: probability distribution of the present given all observations.
* Smoothing: probability distribution of a past state, given all observations.
* Prediction: probability distribution of the future, given all observations.
* Likelihood: probability distribution of all observations.
* Most likely hidden path: probability distribution of all previous states, given all observations.

### Forward algorithms
![](chapter_11/image640.png)
* The intuition behind alpha recursion:
	* The probability of the current state given the observation is scales with the probability of the current state marginalised over all previous states, times the probability of each previous state, times the probability of the observation of the current state given the current state.
	* To normalise, you divide by the probability of the data.

### Smoothing
![](chapter_11/image642.png)
For smoothing, you need to add the probability of the future data, given the current state, which is calculated by the beta function.
![](chapter_11/image643.png)
So here the future beta function is given as the probability of the measurements after the goal state, given the current prediction of the goal state.
The beta distribution of the final state is initialised to unity.

### Gamma recursion
![](chapter_11/image645.png)
* A different way of calculating smoothing, results should be the same.
* Correction: p(h_t+1|v_1:t) after the summation sign should be p(h_t|v_1:t)


### Viterbi algorithm
![](chapter_11/image647.png)


## Continuous dynamic models
![](chapter_11/image650.png)
* Difficulty lies in representing the probabilities: no longer a table, but can be any sort of distribution.
* If the distribution can be approximated by a normal distribution, we can use a Kalman filter.
* If the distribution can not be approximated by a normal distribution, we can use a particle filter.

### Terminology and example
![](chapter_11/image652.png)
* We define a state and a goal
* We need a 
	* Prior probability distribution: P(x0)
	* System model: p(x_t | x_t-1, ut)
	* Measurement model: p(y_t | x_t)

![](chapter_11/image657.png)
* Definition of the above requirements for the example.

## Bayes filter
![](chapter_11/image658.png)
* The probability of a step given all previous steps is acquired by calculating the product of the probability of the data given the current state, multiplied by the integral over all previous states over the probability of the current state given the previous state.
* To normalise, divide by the marginal over all possible current states of the probability of the data given those states.


![](chapter_11/image660.png)
* However, to do this you need a representation of the probability distributions, which might not always be available.
* It can also be computationally expensive.

## Kalman filter
![](chapter_11/image662.png)
* Designed for missile tracking.
* Every probability is represented as a multivariate normal distribution.
	* Because of this, only mean and covariance are parameters

### Assumptions
![](chapter_11/image663.png)
To be able to do this, you need to assume that your prior, measurements and transition probabilities can be represented by a gaussian.

![](chapter_11/image666.png)

![](chapter_11/image668.png)
First, you make a prediction based on the state transition formula.


![](chapter_11/image669.png)
Then, you correct it with the measurement formula.

![](chapter_11/image671.png)
To find the most likely state, you perform a least-square like calculation, trying to find the minimal distance between the predicted state and the measured state, both multiplied by their uncertainty.

### Kalman filter pro’s and cons
![](chapter_11/image672.png)


## Particle filter
![](chapter_11/image676.png)
The distinction of Bayesian filters and sample-based filters is that a continuous version of the distinction between the absolute inference we saw for discrete graphical models (with methods based on message passing) and the approximate inference we saw for discrete graphical models (with methods based on discrete / model sampling).

![](chapter_11/image677.png)
Because sampling is used, complex probability distributions can still be represented.

### Sampling
![](chapter_11/image678.png)
* Use importance sampling to get weighted samples
* This could lead to some problems:
 ![](chapter_11/image679.png)
* If one sample gets a very high weight, the others would be irrelevant.
* This can be solved with resampling, which is implemented in bootstrap filtering.

### Bootstrap filter
![](chapter_11/image680.png)
* The algorithm of bootstrap filter:
	* calculate weighted samples
	* Resample with weights as probs (without replacement?)
	* Add unweighted chosen samples to sample set

![](chapter_11/image682.png)
* 



#bioinformatics/uai/summary