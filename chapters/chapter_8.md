chapter_8

# Lecture 8: Learning from partially observable data
## Missing data
![](chapter_8/image404.png)
When data is missing, this needs to be handled to be able to do calculations.

## Types of missingness
### MCAR
![](chapter_8/image405.png)
* Missingness is completely independent from the data.

If MCAR, you can apply the following two strategies to calculate maximum likelihood:
![](chapter_8/image410.png)
* Deletion based methods:
	* Complete case-analysis only takes into account complete rows
	* Available case-analysis takes into account all relevant data.

### Missing at random

![](chapter_8/image412.png)
* There exist a set of variables, which are complete, on which the missingness depends.
* Application of deletion based methods will lead to bias, as the missingness is influenced by the variables

### Missing not at random
![](chapter_8/image416.png)
* The missingness of a variable is directly dependent on the value of the variable itself.
* This makes the network non-identifiable: there exist multiple bayesian networks which can lead to this outcome.
* Because of this, global and local paramet

### Conclusion on different kinds of missing data
![](chapter_8/image421.png)
* If the missingness is independent or d separated from a variable, it can be ignored.
* If the missingness is not independent, we need EM.

## EM-algorithm
![](chapter_8/image424.png)

### Example
![](chapter_8/image440.png)
* Given the following data with missing values

![](chapter_8/image442.png)
* Complete the data by enumerating every option for each missing value
* Write down the associated probability of every option having that set of missing values

![](chapter_8/image443.png)
* Express the formula for the missing values in terms of theta’s, keep it general!

![](chapter_8/image448.png)
* This leads to a list of all the formula for every option of every missing variable.

![](chapter_8/image449.png)
* Next, loop over the different theta’s!
	* Count the weights associated to each theta, for example, row two is a certain value for a=1, therefore you add one to the count. If missing, add the values of the formula.

![](chapter_8/image451.png)
* If theta is a conditional independence, divide by the occurences of the conditional.

![](chapter_8/image455.png)
This will lead to all values of theta, expressed in terms of formula’s for the probabilities of a row in the completed evidence table.


![](chapter_8/image456.png)
* Only at this time do we fill in the values for the last estimate of theta, in this case all were estimated to 1/2. 
* If you fill this in in the formulas, you’ll get the values above. In this example the calculations of the q’s is not shown, but it follows the calculations in slide 44.

* Now use these theta’s to estimate the new q’s, use these to calculate the new theta’s, and so on.



#bioinformatics/uai/summary