chapter_9

# Lecture 9: Integrating learning and reasoning
## Content
![](chapter_9/image462.png)
Artificial intelligence is not just about probability. It is also about using logic and learning. 
This chapter will handle integration of logic and probability.


## SAT-solving
![](chapter_9/image468.png)
Sat solving, finding a model for a set of conditions, is hard.

A bayesian network can be encoded as a set of formula’s, therefore finding a model is equally hard.
![](chapter_9/image471.png)

![](chapter_9/image472.png)
3 kinds of problems exist in the SAT world: SAT, /#SAT and WMC. these three will be handled.


### /#SAT
How many models exist which satisfy the set of conditions / bayesian network?

## WMC
Given a prior probability of each variable having a certain value, what is the weight of each model?
![](chapter_9/image474.png)
Here elaborated for a probability of 0.5 for each boolean variable.


## Knowledge compilation
If a network can be compiled into a circuit, inference is much cheaper. This compilation is very expensive though. 
![](chapter_9/image485.png)
Semirings are used to give meaning to nodes in the circuit.

![](chapter_9/image493.png)
With these semirings, the above BN is encoded and inferences can be performed much faster.
![](chapter_9/image494.png)
Above is an example of inference on a circuit.

More complicated semirings can be used to perform actions like max-product or gradient based inference.
![](chapter_9/image497.png)

Compilation of these circuits is expensive.

### Negation normal form
Circuits need to be in negation normal form for querying:
![](chapter_9/image503.png)
* Determinism: disjuncts are logically disjoint (cannot be true at the same time).
![](chapter_9/image504.png)
* Decomposable: conjuncts do not share variables

![](chapter_9/image505.png)
* Smooth: disjoints mention the same set of variables


![](chapter_9/image513.png)



## Problog
![](chapter_9/image521.png)
Version of prolog which can work with probabilities.

### Inference in problog
![](chapter_9/image529.png)
Steps needed: like in logic, it needs to be rewritten to ground logic.
Compiled into a circuit.
Evaluate query


![](chapter_9/image533.png)
Final result.


#bioinformatics/uai/summary