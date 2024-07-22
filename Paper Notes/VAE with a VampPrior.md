- VampPrior means getting the component mean parameters from trainable pseudo inputs passed through the encoder.
- The contribution of the paper is modest - they add hierarchy on top of the VampPrior latent
- [implementation](https://github.com/jmtomczak/vae_vampprior)

### Model
![[Pasted image 20240719093525.png]]
It may look scary but it is simply a chain rule for the densities that is broken into sum with the logarithm and yields two separate VAEs chained together with separate latent constraints.
![[Pasted image 20240719093606.png]]
## Summary
Instead of learning the means of the mixture in the trainable prior we learn pseudo inputs which are mapped to the latent space with the encoder.

#### Plusses
- It seems fine to initialize the pseudo inputs with the means of the classes in the input space to remedy under representation of some classes combined with random initialization of the component means.
- Flexible number of components. Just a pseudo input and a forward pass. The we could add the components parameters during training as a mean of the latent representations and gain the same flexibility, but perhaps it would work poorer for out of distribution samples which are not represented by a compact cluster in the latent - then using pseudo input being average in the input space might have more sense.
- Additional learning signal passed through the encoder.
#### Minuses
- Requires forward pass through encoder
- We are getting only mean parameters this way as covarriance would be strange at least to me to get
- The intuition behind the model comes from the optimization of prior given posterior distributions. The optimal prior i a mixture of all posteriors. These arguments apply to a regular mixture model capable of representing the same density. Anyways it seems strange to present it this way, but prior optimization is also a concern so fine.
- I am not so sure about the number of parameters given as an advantage below. It does not seem  true.
![[Pasted image 20240719083339.png]]
![[Pasted image 20240719083503.png]]
- I am not convinced by the second point as well. Why is it related with high variance? From this formulation we know nothing about the direction - only that it is small when we are close in the latent. Anyways isnt this is the conclusion from the split of the ELBO into compnents? I could split the Sloss for the GM prior and show which part encourages what.

Does not seem like a big deal. Wordy paper. Presents arguments for simply more complex priors as a support for their specific method, which is poorly supported with arguments. Anyways might be easily implemented, seems flexible and may express the same .

## Bullet points
- The VampPrior consists of a mixture distribution (e.g., a mixture of Gaussians) with components given by variational posteriors conditioned on learnable pseudo-inputs.
- The model also avoids the usual local optima issues related to useless latent dimensions that plague VAEs.
- VampPrior provides additional gradient signal to the encoder

## Questions
1. 

## References / Note links
1. [[VAE prior]]