chapter_5

# Lecture 5: Inference
## Basic principle of inference
![](chapter_5/image192.png)
* Answering questions about the environment, using the distribution.

![](chapter_5/image193.png)
* There exist many methods to perform inference. These exist as it can be expensive to perform inference and every method is optimised for some type of question and model.

### Variable elimination
* An example of where large decreases in computation time can be obtained, is in variable elimination. 
* This can be done when a marginal over variables is calculated.
![](chapter_5/image198.png)
* In this slide a random order is chosen. 
* Because of this, every summation still needs to be calculated. 
* If a smarter order is picked, this could be optimised, as in the following example.

![](chapter_5/image201.png)
* In this example, an optimal order is picked. 
* This leads to three marginals becoming zero and not having to be calculated.
* But how to chose this order? -> 
	* begin with the **leaves which don’t influence the final variable**

## Bucket elimination
_A graphical method for calculating marginals which represents “pushing summations inside_
![](chapter_5/image210.png)
![](chapter_5/image216.png)
* Move down the buckets, at each step performing the summation over the variable in that bucket.
* This can be done either with variable names or actual probabilities from the tables.
* Dependent on the network properties and the chosen ordering, this can be efficient.

## Message passing
_Message passing lies at the basis of many techniques to calculate marginals._

![](chapter_5/image230.png)
* Factorise the joint
* Query: marginal probability of p(a=0)
* Write down the formula for this query
* Push summations inside, by doing this you will decrease the needed summations.
![](chapter_5/image236.png)
In the example, the number of summations is decreased from 7 to 5.

### Application on Markov chains
![](chapter_5/image237.png)
![](chapter_5/image238.png)
Will leed to 2T-1 needed summations if the order is perfect, linear increase instead of exponential!


## Sum product
Based on the idea of message passing -> can only be used on singly connected graphs.
![](chapter_5/image294.png)

Variable from variable to factor is equal to the product of incoming messages.
Factor to variable message is equal to the sum of the products of the probability of a value given the incoming variable and the incoming message of that variable.

![](chapter_5/image297.png)
First, the leaves nodes are initialised to 1 and the leave factors to their values.
Order is picked, dependent on the factor which should be calculated. If only 1 marginal need to be calculated, chose this one as the root node.

## Max-product
![](chapter_5/Screenshot%202022-01-18%20at%2018.52.13.png)
* Calculate the most probable state for each conditional state on the path.

![](chapter_5/Screenshot%202022-01-18%20at%2018.53.54.png)
* During calculation you can already see which value is most probable: 
	* for C(0), B=1 has a higher probability than b=0.
	* for C(1), B=0 has a higher probability than b=1.

![](chapter_5/Screenshot%202022-01-18%20at%2018.57.43.png)
* Finally you can calculate the marginal over the root node. This gives you the optimal node from this node.
* Backtrack with this value for the root node, extract what the optimal set of variables was.
* Because we already had seen that for C(0) B=1 had a higher probability, we can now choose this value for B.

## Multiply connected graphs
_Sum product or max product is not possible. We can however still use bucket elimination, as this does not do any presumptions on the network. Another option is to perform a loop-cut: look for a set of variables which, will make the network singly connected when you condition on them. Then perform your inference on the conditioned network for all options of the cut-set and afterwards calculate the result from this._

![](chapter_5/Screenshot%202022-01-18%20at%2019.17.01.png)
* In this example the set can be conditioned on A, which creates a singly connected graph.
![](chapter_5/Screenshot%202022-01-18%20at%2019.19.45.png)
* Finally you combine the information of the (in this case) two options for the cutset, leading to the answer.

Conclusion
![](chapter_5/Screenshot%202022-01-18%20at%2019.34.52.png)



#bioinformatics/uai/summary