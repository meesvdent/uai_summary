# Chapter 1: introduction and probability

### Goal of the course
![](Chapter%201%20introduction%20and%20probability/image16.png)
* Modelling: a formal representation on how the world behaves.
* Inference: answer question about the world by evaluating the model.
* Learning: construct or improve the model on the world. Use data to improve structure or parameters of which the world consists.
* Decision making: draw conclusions from all of the above to use in the real world.


### Probability
#### Normalisation
![](Chapter%201%20introduction%20and%20probability/image28.png)
If you look at a probability density function, either discrete or continuous, the sum over all of the possible options should be 1.

#### Rules of calculation with probability
Derived from set theory:
![](Chapter%201%20introduction%20and%20probability/image29.png)

#### Marginalisation
When there are multiple dimensions x and y, the marginal over x is the sum of each option for x for every option of y.
![](Chapter%201%20introduction%20and%20probability/image35.png)

### Bayes rule
If two probabilities are dependent, evidence on one will influence the probability of the other. This is formalised in Bayes rule:
![](Chapter%201%20introduction%20and%20probability/image37.png)

#### Conditional dependence
![](Chapter%201%20introduction%20and%20probability/image45.png)
When two sets of variables X and Y are conditionally independent, there exists a set of variables Z, given which the two sets are independent. These variables Z can be seen as “in between” X and Y in a Markov network, cutting them off from each other.

![](Chapter%201%20introduction%20and%20probability/image46.png)
This does not mean that both variables X and Y can be marginalised over Z and will then be independent. 

### Usage in science
#### Prior, likelihood, posterior, evidence paradigm
![](Chapter%201%20introduction%20and%20probability/image52.png)
This can be used to infer odds on parameters based on observations.
For instance, you can calculate the odds of a known parameter theta, based on new observations D.
#### Most probable posteriori
![](Chapter%201%20introduction%20and%20probability/image53.png)
By using a MAP assignment, this can be used to infer the most probable parameter theta in the light of the data.

##