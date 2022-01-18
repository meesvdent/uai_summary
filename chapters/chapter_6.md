chapter_6

# Lecture 6: Inference 2

## Max-product
![](chapter_6/Screenshot%202022-01-18%20at%2018.52.13.png)
* Calculate the most probable state for each conditional state on the path.

![](chapter_6/Screenshot%202022-01-18%20at%2018.53.54.png)
* During calculation you can already see which value is most probable: 
	* for C(0), B=1 has a higher probability than b=0.
	* for C(1), B=0 has a higher probability than b=1.

![](chapter_6/Screenshot%202022-01-18%20at%2018.57.43.png)
* Finally you can calculate the marginal over the root node. This gives you the optimal node from this node.
* Backtrack with this value for the root node, extract what the optimal set of variables was.
* Because we already had seen that for C(0) B=1 had a higher probability, we can now choose this value for B.

## Multiply connected graphs
_Sum product or max product is not possible. We can however still use bucket elimination, as this does not do any presumptions on the network. Another option is to perform a loop-cut: look for a set of variables which, will make the network singly connected when you condition on them. Then perform your inference on the conditioned network for all options of the cut-set and afterwards calculate the result from this._

![](chapter_6/Screenshot%202022-01-18%20at%2019.17.01.png)
* In this example the set can be conditioned on A, which creates a singly connected graph.
![](chapter_6/Screenshot%202022-01-18%20at%2019.19.45.png)
* Finally you combine the information of the (in this case) two options for the cutset, leading to the answer.

Conclusion
![](chapter_6/Screenshot%202022-01-18%20at%2019.34.52.png)



#bioinformatics/uai/summary