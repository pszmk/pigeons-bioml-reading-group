The provided intution comes from the optimisation of prior given posterior distributions. Moreover these arguments apply to a regular mixture model capable of representing the same mixture.
I am not so sure about the number of parameters here... 
![[Pasted image 20240719083339.png]]
![[Pasted image 20240719083503.png]]
I am not convinced by the second point as well. Why is it related with high variance? From this formulation we know nothing about the direction - only that it is small when we are close in the latent. Anyways isnt this is the conclusion from the split of the ELBO into compnents? I could split the Sloss for the GM prior and show which part encourages what.

### Model
![[Pasted image 20240719093525.png]]
It may look scary but it is simply a chain rule for the densities that is broken into sum with the logarithm and yields two separate VAEs chained together with separate latent constraints.
![[Pasted image 20240719093606.png]]
## Summary
Seems not like a big deal. Wordy. Presents arguments for simply more complex priors as a support for their specific method. Anyways might be easily implemented.

## Bullet points
- The VampPrior consists of a mixture distribution (e.g., a mixture of Gaussians) with components given by variational posteriors conditioned on learnable pseudo-inputs.
- The model also avoids the usual local optima issues related to useless latent dimensions that plague VAEs.
- VampPrior provides additional gradient signal to the encoder

## Questions
1. 

## References / Note links
1. [[VAE prior]]