chapter_10

# Lecture 10: sampling techniques
## Basic sampling techniques
### Univariate sampling from discrete distributions
![](chapter_10/image576.png)
* Order the values by their probability
* Calculate cumulant up to each value
* When random number between last and next, this is the value.

### Univariate sampling from continuous distributions
![](chapter_10/image579.png)
* Same principle for continuous distributions

### Rejection sampling
![](chapter_10/image581.png)
* Create proposal distribution close to real distribution: f(x)
* sample from it: x
* sample u between 0 and f(x)
* if u < real(x) -> take the sample
* otherwise reject
	* the more rejections, the less efficient.

## Multivariate sampling
![](chapter_10/image583.png)
* Enumerate
* Add counts to options
* Draw from counts
-> not efficient -> this is why ancestral sampling exists.

### Ancestral sampling
![](chapter_10/image587.png)
* Start at root, sampling from their distribution.
* Using this sample, sample from its children.
	* In case of evidence: throw away the sample if it doesn’t agree with evidence.
![](chapter_10/image591.png)
Example of throwing away a sample because of evidence.

![](chapter_10/image589.png)
Using these samples, you can answer queries by counting or MAP.

## Gibs-sampling
![](chapter_10/image598.png)
* Start with random sample
* Change one variable, conditional on others, with a random number

* This causes the samples to be dependent on previous samples:
	* Use burn in: start recording after k-samples
	* Only record every k’th sample
	* Risk of getting stuck at local minimum.


### Importance “sampling”
![](chapter_10/image605.png)
* Calculate weights to transform samples from one distribution into value of another distribution.
* <x>p(x) = sum(xl * wl)

## Particle filter
![](chapter_10/image611.png)
Above importance sampling is used in particle filters.

### Conclusion
![](chapter_10/image614.png)





#bioinformatics/uai/summary