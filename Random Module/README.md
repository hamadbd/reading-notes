## Python Random Module
You can generate random numbers in Python by using random module.

Python offers random module that can generate random numbers.

These are pseudo-random number as the sequence of number generated depends on the seed.

If the seeding value is same, the sequence will be the same. For example, if you use 2 as the seeding value, you will always see the following sequence.
```
import random
random.seed(2)

print(random.random())
print(random.random())
print(random.random())
```

## List of Functions in Python Random Module
| Function	| Description |
| ----------- | ----------- |
seed(a=None, version=2)|	Initialize the random number generator
getstate()|	Returns an object capturing the current internal state of the generator
setstate(state)|Restores the internal state of the generator
getrandbits(k)|	Returns a Python integer with k random bits
randrange(start, stop[, step])|	Returns a random integer from the range
randint(a, b)|	Returns a random integer between a and b inclusive
choice(seq)|	Return a random element from the non-empty sequence
shuffle(seq)	|Shuffle the sequence
sample(population, k)|	Return a k length list of unique elements chosen from the population sequence
random()|	Return the next random floating point number in the range [0.0, 1.0)
uniform(a, b)|	Return a random floating point number between a and b inclusive
triangular(low, high, mode)|	Return a random floating point number between low and high, with the specified mode between those bounds
betavariate(alpha, beta)|	Beta distribution
expovariate(lambd)|	Exponential distribution
gammavariate(alpha, beta)|	Gamma distribution
gauss(mu, sigma)|	Gaussian distribution
lognormvariate(mu, sigma)|	Log normal distribution
normalvariate(mu, sigma)|	Normal distribution
vonmisesvariate(mu, kappa)|	Vonmises distribution
paretovariate(alpha)|	Pareto distribution
weibullvariate(alpha, beta)|	Weibull distribution

# Risk Analysis
points can be taken care of:

- Conduct Risk Assessment review meeting
- Use maximum resources to work on high-risk areas
- Create a Risk Assessment database for future use
- Identify and notice the risk magnitude indicators: high, medium, low.

### Risk Identification
There are different sets of risks included in the risk identification process. Those are as follows:

1- Business Risks: This risk is the most common risk associated with our topic. It is the risk that may come from your company or your customer, not from your project.

2- Testing Risks: You should be well acquainted with the platform you are working on, along with the software testing tools being used.

3- Premature Release Risk: a fair amount of knowledge to analyze the risk associated with releasing unsatisfactory or untested software is required

4- Software Risks: You should be well versed with the risks associated with the software development process.

## The perspective of Risk Assessment
There are three perspectives of Risk Assessment:

1- Effect 
2- Cause 
3- Likelihood 

- Effect – To assess risk by Effect. In case you identify a condition, event or action and try to determine its impact.
- Cause – To assess risk by Cause is opposite of by Effect. Initialize scanning the problem and reach to the point that could be the most probable reason behind that.
- Likelihood – To assess risk by Likelihood is to say that there is a probability that a requirement won’t be satisfied.

Now, heading forward, the question that would be hovering over your mind is, how actually shall we perform risk analysis? Well, here is your solution!