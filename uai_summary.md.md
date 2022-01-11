# Uncertainty in AI

## Chapter 1: introduction and probability

### Goal of the course
![](uai_summary.md/image16.png)
* Modelling: a formal representation on how the world behaves.
* Inference: answer question about the world by evaluating the model.
* Learning: construct or improve the model on the world. Use data to improve structure or parameters of which the world consists.
* Decision making: draw conclusions from all of the above to use in the real world.


### Probability
#### Normalisation
![](uai_summary.md/image28.png)
If you look at a probability density function, either discrete or continuous, the sum over all of the possible options should be 1.

#### Rules of calculation with probability
Derived from set theory:
![](uai_summary.md/image29.png)

#### Marginalisation
When there are multiple dimensions x and y, the marginal over x is the sum of each option for x for every option of y.
![](uai_summary.md/image35.png)

### Bayes rule
If two probabilities are dependent, evidence on one will influence the probability of the other. This is formalised in Bayes rule:
![](uai_summary.md/image37.png)

#### Conditional dependence
![](uai_summary.md/image45.png)
When two sets of variables X and Y are conditionally independent, there exists a set of variables Z, given which the two sets are independent. These variables Z can be seen as “in between” X and Y in a Markov network, cutting them off from each other.

![](uai_summary.md/image46.png)
This does not mean that both variables X and Y can be marginalised over Z and will then be independent. 

### Usage in science
#### Prior, likelihood, posterior, evidence paradigm
![](uai_summary.md/image52.png)
This can be used to infer odds on parameters based on observations.
For instance, you can calculate the odds of a known parameter theta, based on new observations D.
#### Most probable posteriori
![](uai_summary.md/image53.png)
By using a MAP assignment, this can be used to infer the most probable parameter theta in the light of the data.

## Chapter 2: Introduction to graphs and Bayesian networks
### Introduction to graphs

#### Paths and directed paths.
![](uai_summary.md/image60.png)
A path is a set of edges which leads from a start node to an end node without respecting edge direction.
Directed path is a path which does respect edge direction.

#### Cycles and loops
![](uai_summary.md/image61.png)
Cycle respects edge direction, loop does not respect edge direction.

### Directed acyclic graphs
#### Definition
![](uai_summary.md/image62.png)
Subset of graphs. Acyclic graph -> without _cycles_.

#### Relationships within DAG’s
![](uai_summary.md/image63.png)
* Ancestor of Xi: set off nodes with a directed path to Xi.
* Descendants of Xi: set of nodes with a directed path leading to them from Xi.
![](uai_summary.md/image64.png)
* Parents: ancestor with single directed edge in path.
* Children: descendent with single directed edge in path.
![](uai_summary.md/image66.png)
* Neighbours of Xi: nodes directly connected to X, not holding into account edge direction.
* Clique: fully connected subset of nodes, not holding into account edge direction.
* Maximal clique: clique which cannot be extended by adding nodes.
![](uai_summary.md/image67.png)
* Connected graph: any node can be reached from any other node, without taking into account edge direction.
* Singly-connected graph: there is only one _path_ from any node a to any other node b: no loops.
* Multiply connected: inverse off a tree.

### Benefits of structure
![](uai_summary.md/image69.png)
The properties of DAG and conditional probability can be used to decrease computational load of queries. In a large network, calculating a query, like for instance calculating a marginal probability from a joint, will have great computational complexity. 
This is due to the great number of entries in a joint, which has an order of O(a^n) for a the number of options for each dimensions. A joint probability of 10 binary variables contains 1024 entries. Computing a marginal would require summation over 9^9 entries.

![](uai_summary.md/image70.png)
In a DAG, a joint probability can be factorised using Bayes rule. If you look at the number of entries in each of the coloured probability tables and add these up, it will be clear that this number is less than 2^5.

### Conditional independence in belief networks
To utilise these properties, it is important to know the rules of when two variables are dependent or independent given another variable.
![](uai_summary.md/image96.png)
If a variable in the evidence is in between two variables A and B, these variables are independent. _Except when it is a collider._ In (d), knowing C will mean that one option of B would have different probabilities for A than another option for B.

If variable in between is not in the evidence, this relation is inverted. This is clear from the visual graph:
![](uai_summary.md/image99.png)
Obviously, in (b) B is dependent on A, as there is a direct graph between them. In 

### Connection graph
Shows wether two variables are dependent on each other, by drawing a graph between them.
Method for constructing them:
![](uai_summary.md/image113.png)
Keep links with colliders in the conditioning set.
Cut links with colliders not in the conditioning set.
![](uai_summary.md/image114.png)
Cut links with with non-colliders in the conditioning set.
Keep links with non-colliders not in the conditioning set.
Paths between variables means dependence.

#### Markov equivalence
![](uai_summary.md/image128.png)
Same skeleton and same set of immortalities -> same conditional independence statements.

### Uncertain evidence
![](uai_summary.md/image135.png)
Uncertain evidence will influence probability of dependent variables, but only as much as relative to their certainty.

### Hidden Markov models
![](uai_summary.md/image142.png)
There is a true state, which influence the probability of finding something in a certain measurement. This true state also influences the consecutive states.

On these models, some important special queries can be done:
![](uai_summary.md/image143.png)
* Filtering: what is the probability a current state, given all previous observations.
* Smoothing: what is the probability of a state in the past, given all observations up until now.
* Viterbi: what is the most probable path of all hidden states until now given the complete evidence.

## Inference
### Sum product
Based on the idea of message passing
![](uai_summary.md/image294.png)

Variable from variable to factor is equal to the product of incoming messages.
Factor to variable message is equal to the sum of the products of the probability of a value given the incoming variable and the incoming message of that variable.

![](uai_summary.md/image297.png)
First, the leaves nodes are initialised to 1 and the leave factors to their values.
Order is picked, dependent on the factor which should be calculated. If only 1 marginal need to be calculated, chose this one as the root node.




























