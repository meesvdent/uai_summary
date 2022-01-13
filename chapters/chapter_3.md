chapter_3

# Lecture 3: Bayesian networks, conditional independence, D-seperation

## Connection graph
Shows wether two variables are dependent on each other, by drawing a graph between them.
Method for constructing them:
![](chapter_3/image113.png)
Keep links with colliders in the conditioning set.
Cut links with colliders not in the conditioning set.
![](chapter_3/image114.png)
Cut links with with non-colliders in the conditioning set.
Keep links with non-colliders not in the conditioning set.
Paths between variables means dependence.

### Markov equivalence
![](chapter_3/image128.png)
Same skeleton and same set of immortalities -> same conditional independence statements.

## Uncertain evidence
![](chapter_3/image135.png)
Uncertain evidence will influence probability of dependent variables, but only as much as relative to their certainty.

## Hidden Markov models
![](chapter_3/image142.png)
There is a true state, which influence the probability of finding something in a certain measurement. This true state also influences the consecutive states.

### Inference questions on HMM’s
On these models, some important special queries can be done:
![](chapter_3/image143.png)
* Filtering: what is the probability a current state, given all previous observations.
* Smoothing: what is the probability of a state in the past, given all observations up until now.
* Viterbi: what is the most probable path of all hidden states until now given the complete evidence.

#bioinformatics/uai/summary