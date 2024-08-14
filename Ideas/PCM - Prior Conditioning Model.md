
## Bullet points
#### Model
- INPUT
	- prior conditions
- OUTPUT
	- (most likely, in the basic case) GM prior parameterized by the components probabilities, their means and covariance matrices
- handles consistency constraints between condition induced priors
- most likely a set modelling model
	- e.g. transformer model

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