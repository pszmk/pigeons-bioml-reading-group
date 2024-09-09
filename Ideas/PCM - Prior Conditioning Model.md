
## Bullet points
#### Prior Conditioning Model
- INPUT
	- a set of known prior conditions
- OUTPUT
	- (most likely, in the basic case) GM prior parameterized by the components probabilities, their means and covariance matrices
- handles consistency constraints between condition induced priors
- most likely a set modelling model
	- e.g. transformer model

## Consistency constraint between condition induced priors
Let $p(z|c)$ be a prior conditioning model (PCM) with $z$ a latent space element and $c$ a condition, $p(c_1)$ a probability/density of a set of conditions $c_1$. 

Ideally given two sets of conditions $c_1$, $c_2$  we would like the following constraint to hold:
1. Marginalization
$$p(z|c_1) = \int_{c_2} p(z, c_2|c_1) d c_2 = \int_{c_2} p(z | c_1, c_2) \cdot \frac{p(c_1, c_2)}{p(c_1)} d c_2 = \frac{1}{p(c_1)} \cdot \mathbb{E}_{c_2 \sim p(c_1, c_2)} \left [ p(z | c_1, c_2) \right ] = \mathbb{E}_{c_2 \sim p(c_2 | c_1)} \left [ p(z | c_1, c_2) \right ] $$
In this form sampling $c_2 \sim p(c_2 | c_1)$ is required.

When given $c_1$ and $c_2$ together and using PCM $p( z | c_1, c_2)$ for prior nll we are training PCM specifically conditioned on $c_1$ and $c_2$ co-occurring. We could consider $p( z | c_1)$ and $p( z | c_2)$ as other PCMs.
#### Dropping conditions
Intuitively when provided $c_1, c_2$ condition sets we would like the likelihood of the latent variable $z$ be high for all $p( z | c_1, c_2)$, $p( z | c_1)$ and $p( z | c_2)$.

For a nll term $p(z|C)$ consider dropping with probability $p_{drop}$ each single condition $c$ then in expectation nll for each possible $p(z | C^s)$, where $C^s \subseteq C$, will be sampled with probability $\mathbb{P}[ K = | C^s | ]$ for $K \sim  (1 - p_{drop})^K \cdot p_{drop}^{| C | - K}$. Consequently we may write $C^s \sim \text{Drop}(C)$, where $\text{Drop}(C)$ is the stochastic dropping procedure. Note, that:
$$ \sum_{C^s \subseteq C} -\log p(z | C^s) =  \sum_{C^s \subseteq C} \left[ -\log p(z | C^s) \cdot \frac{\mathbb{P}[ K = | C^s | ]}{\mathbb{P}[ K = | C^s | ]} \right ] = \mathbb{E}_{C^s \sim \text{Drop}(C)} \left [ -\log p(z | C^s) \cdot \frac{1}{\mathbb{P}[ K = | C^s | ]} \right ]$$

#### Show, that for $C^s$ marginalization condition is met when the training incorporates loss term $\sum_{C^s \subseteq C} -\log p(z | C^s)$ or what follows from it -> attempts failed

Given $C^s$ consider $C$ such that $C^s \subseteq C$ then $p(C^s) = \int_C d p(C)$ by marginalization.
Recall the marginalization condition $$p(z|C^s) = \frac{1}{p(C^s)} \cdot \mathbb{E}_{ C \setminus C^s \sim p(C \setminus C^s \cup C^s)} \left [ p(z | C) \right ] = \frac{1}{p(C^s)} \cdot \mathbb{E}_{ C \sim p(C)} \left [ p(z | C) \right ]$$since $p(C | C^s) = \frac{p(C, C^s)}{ p( C^s) } = \frac{p(C)}{ p( C^s) }$ 

---
Assume $x_c$ determines some $C$ then $p(C) = \int_{x} d p(x)$. Consequently $$\mathbb{E}_{p(x)} [ f(C) ] = \mathbb{E}_{p(C)} [ f(C) ]$$
$\sum_{C^s} - \log p(z | C^s) \cdot p(C^s) = \sum_{C} p(C) \cdot \sum_{C^s \subseteq C} - \log p(z | C^s)$

We assume, that the prior $p(z)$ is conditioned on $x$ only via $C$ induced by $x$ (known ones) meaning that $p(z|C, x) = p(z|C)$ <-verify. Then given $f(C) = \sum_{C^s \subseteq C} - \log p(z | C^s)$

$$\mathbb{E}_{p(x)} [ \sum_{C^s \subseteq C} - \log p(z | C^s) ] = \mathbb{E}_{p(C)} \left[ \sum_{C^s \subseteq C} - \log p(z | C^s) \right ]$$

$$ -\mathbb{E}_{p(x)} \left [ \, \mathbb{E}_{q(z | x)} \left [ \, \log p(z | C) \, \right ] \, \right ] = $$

write that the probability of C is the integrated probability of all samples having this condition


### Special case
Gaussian mixture with PCM providing component logits.
## Questions
1. How to produce the induced latent prior? 
	- inputting just the tokens for the present conditions (may lead to bias - not training nonpresent condition tokens)
	- we would like to train other tokens as well
	- for gradual conditioning we could weight the condition tokens with sigmoid or sthg unbounded, but almost vanishing
	- prior inducing model
	- a model with **fixed number** of GM components
	- a model with **varying number** of GM components
	- e.g. an autoregressive model outputting varying number of GM components
	- e.g. discrete codebook of GM parameters (simplify to mean vectors) outputting
	- the probability of the smples from the posterior should be bound to the probabilities of the components
	- how to control when to stop adding components in a differentiable manner?
2. What about creating a model, which is able to infer the conditions on its own if lacking?
3. How to  constrain the latent priors to prevent some kind of latent collapse, stable training, meaningful induced priors for "simillar" conditions

## References / Note links
1. 