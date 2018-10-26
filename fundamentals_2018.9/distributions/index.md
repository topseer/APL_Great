# Mathematical Distributions
In the last chapter we talked about *probability*.

In motivating our discussion about probability and how it ties to the real world, we talked about systems or, more specifically, *processes* that generate events that we measure in some way. And while we may understand the process in a qualitative way (Causal Loop Diagrams), we may not be able to simulate the process with sufficient fidelity. We saw this with the coin toss.

Tossing a coin is a deterministic process that is at least well understood in theory but a practical simulation of coin tosses is generally impossible for us. Additionally, even if we had such a simulation, we would not be able to obtain measurements accurate enough to predict the outcome of a specific coin toss. The system may be chaotic (exhibit non-linear dynamics). Thus, the result of the toss, heads or tails, is our only measurable observation of this process. In order to model this process--in our uncertainty or ignorance--we turn to probability.

In the Applications section of the last chapter we started to hint that processes--even very different processes--have enough in common that we can use the same simulation or probability distribution to model them, sometimes only with minor changes.

A good example is a coin toss where we have heads or tails. We can generalize this to any process with an event which is divided into two categories: success or failure. Now, "success" and "failure" are arbitrary designations--what we really mean is that "success" is the observation of interest and the other observation or observations are not. If there is more than one "other" observation, they are all lumped together as "failure". Additionally, although we can model the process using something like a Causal Loop Diagram and we know that there are a lot of factors affecting the outcome, we are often unable to specify them except qualitatively. It turns out there are many such processes.

For example, if you have an online store, you can model a customer clicking on a product or buying a product as a process exactly like a coin toss. Of course, they didn't *arbitrarily* decided to be buy something on your site. They may have searched for something, visited other sites, looked at reviews, received an email from you and/or competitors...all before they purchased from your website. Nevertheless, we can describe this process using the same approach as a coin flip.

Or perhaps we're looking at sports statistics. A basketball player may attempt to make a free throw. They may have practiced for years, been coached, there's the interaction of other players. Or someone taking a new medication. They may have different side effects, co-existing conditions, exposures, etc. Still, we can describe this the same way as the coin flip.

In general, what we're describing here are processes with binary outcomes: purchase or not, basket or not, cure or not. But there are many, many different distributions for different kinds of outcomes and different kinds of variables (qualitative or quantitative). In general, these are called Bernoulli Trials and they're can be characterized by a Bernoulli distribution. And although we won't officially start modeling for a few chapters, a discussion of these very general probability distributions is a good bridge to Statistical Inference in the next chapter.

## Events and Random Variables
When we talked about probability we talked about sets of outcomes or events. For example, the set $A$ with $P(A)$ representing the probability of observing some element of $A$, $a_i$. But A, B, C are just the variables (features, attributes, etc.) from our data: purchase {yes, no} and state {"AR", "AK", "AL",..., "WY"}, etc.

^ do a better job of connecting this to real data.


Expanding this discussion to _data_, we can interpret each column in a data set are the recorded outcome or event from some such possible set of outcomes. The technical name given for this column is **random variable**. Random variable is an awful name because it conjures up the wrong image of probability (an image that leads to fallacies and confusion).

A random variable just a mathemtical formalism that says whenever we observe the value of the variable, the value observed is uncertain because it changes. Think of a system that has as a variable of interest, height. What goes into the height of an adult _homo sapiens_? We can think of parental genetics, biological sex, ancestry, nutrition, childhood diseases, as sort of high level factors influencing adult height. For each observation (person measured) you will not have recorded most or any of these. So although it's a deterministic system, we are ignorant of almost everything that went into the result.

When we observe each realization of the system (a person), we get a different value for height. Now height is a, theoretically, real valued measurement so we're not going to use the same kind of distribution to represent it as we do purchases, baskets and cures. Instead we will model $P(Height)$ by using one of the appropriate _continuous_ distributions. Because height cannot be negative, it is often modeled with a _Log Normal_ distribution.

If we add biological sex (sex) as another random variable (afterall, sex is determined by the workings of a system about which we are also largely ignorant --and even more so for gender, we have a _joint_ probability distribution $P(Height, Sex)$. Often we're more interested in just height _given_ sex and so we will explicitly or implicitly condition on sex and have $P(Height|Sex)$. Once we enter the world of real values, we add another dimension of ignorance. Generally speaking, our rulers, tape measures and scales do not have infinite resolution and so our measurements will often appear to be discrete (for example, if all measurements are in the nearest inch or cm). Sometimes this will not matter and we can treat the values as continuous. Other times it might matter and we'll need to treat them as discrete. We'll talk more about value types in **Exploratory Data Analysis**.

Finally, we also have the problem of the limits of representing floating point numbers in digital computers. We'll ignore this altogether.

## Distributions and Densities
In the discussion on probability, we dealt mostly with discrete outcomes (either quantitative or qualitative). Any such $P(A)$ was called a probability distribution. We also discussed how $P(A|B)$ might represent many probability distributions, one for each possible value of B. More specifically, if A is a discrete random variable, P(A) is called a **probability mass function**, PMF. The heights of the PMF sum to 1 as per Axiom #2.

However, if A has continuous valued outcomes (such as a height measurement), we have a problem because the probability of any given value is zero (or at least infinitesimally small) and while the area under such a function would still be one, it would be indistinguishable from the x axes.

So instead of representing continuous random variables as a probability mass function, they are represented as a **probability density function**. The probability density function (PDF) represents the probability of values in a range as the area under the curve in that range. However, the area under the entire PDF still sums to 1. If the y-axis does not specifically say "Probability Density", one clue that you're dealing with a probability _density_ is that the numbers of the y-axis will very often not look like anything that could possibly sum to 1.

A related concept (which is only well-defined for random variables that can be ordered) is the cumulative mass function (CMF) or cumulative density function (CDF). The CDF shows the probability of observation (realizing) a particular value of A or lower. CDFs are important of exploratory data analysis (EDA) as we will see.

Throughout the book, we will find that probability distributions are good for at least three things:

1. Modeling data - we can use probability distributions to model height, job completion times, flood height.
2. Modeling parameters (signal) - we can use probability distributions to model our uncertainty in the mean height, the completion time rate or the maximum flood height.
3. Modeling noise - we can use probability distributions to model either things like measurement error, the unknown or known unknowns or just "everything else".

And a few others as well as we will have a chance to see.

## Accounting, Summary Statistics, Moments and Loss
## Loss Functions, Statistics and Parameters
## A Bestiary of Mathematical Distributions
We will now set out to generate a large number of important distributions for data science starting with a seemingly innocuous distribution: the uniform distribution.

Need to talk about parameters.

Every distribution has one or more motivating stories about some process that generates it. Because of the Central Limit Theorem (which does not just pertain to the Normal Distribution), there is often more than one way to get to a particular distribution but we will generally tell only one story here.

### Uniform Distribution
We're going to start with the Uniform Distribution. The Uniform Distribution can be discrete (for example, the outcomes of a six-sided die) or continuous (values between 0 and 1). When you use `rand` you are simulating a draw from a Uniform Distribution.

### Bernoulli Distribution
### Exponential Distribution
#### Shifted Exponential Distribution
#### Weibull Distribution
### Binomial Distribution
### Poisson Distribution
#### Zero-Inflated Poisson Distribution
#### can't remember the other one (CS 109 talks about it)
### Statistical Rethinking has another distribution here.
### Normal Distribution
#### Central Limit Theorem
### Log-Normal Distribution
