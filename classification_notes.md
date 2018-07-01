* One vs. All
	* A way to leverage binary classification
	* Given a classification problem with n possible  solutions, a ‘one v all’ solution consists of N separate binary classifiers - one for each possible outcome
	* During training, the model runs through a sequence of binary classifiers, training each to answer a separate classification question.
1 Is this image an apple? No.
2 Is this image a bear? No.
3 Is this image candy? No.
4 Is this image a dog? Yes.
5 Is this image an egg? No.
	* This approach is fairly reasonable when the total number of classes is small, but becomes increasingly inefficient as the number of classes rises.
	* We can create a significantly more efficient one-vs.-all model with a deep neural network in which each output node represents a different class

* Softmax 
	* Logistic regression means that the sum of the probabilities will be 1.0
	* *Softmax* extends this idea into a multi-class world. That is, Softmax assigns decimal probabilities to each class in a multi-class problem. Those decimal probabilities must add up to 1.0. This additional constraint helps training converge more quickly than it otherwise would.
		* Softmax is implemented through a neural network layer just before the output layer. The Softmax layer must have the same number of nodes as the output layer.
	* FULL softmax - calculates a probability for every possible class
	* Candidate Sampling -  calculates a probability for all the positive labels but only for a random sample of negative labels. For example, if we are interested in determining whether an input image is a beagle or a bloodhound, we don’t have to provide probabilities for every non-doggy example.

* One Label vs Many labels
	* Softmax assumes that each example is a member of exactly one class
	* If an example can be simultaneously a member of multiple classes,
		* softmax cannot be used
		* use multiple logistic regressions


* Softmax Multi-Class
	* Add an additional constraint: require output of all one-vs-all nodes to sum to 1.0
	* The additional constraint helps training converge quickly
	* Plus, allows outputs to be interpreted as probabilities
	* /Single-Label/
		* an example may be a member of only one class
		* constraint that classes are mutually exclusive is helpful structure
		* useful to encode this in the loss
		* use one softmax loss for all possible classes
	* /Multi-Label/
		* An example may be a member of more than one
		* No additional constraints on class membership  
		* One  logistic regression loss for each possible class
	* Full Softmax
		* Brute force, calculates for all classes
	* Candidate Sampling
		* Calculates for all the positive labels, but only for a random sample of negatives


* How do we know if we have a good regression line?
	* Loss
	* The distance between the actual value and the line
	* Loss is always on a zero to positive scale
	* For regression start out with
		* L2 loss, squared error. Takes the square of the difference between the model’s prediction and the actual value
