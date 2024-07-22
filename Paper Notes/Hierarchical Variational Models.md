![[Pasted image 20240719132501.png]]
![[Pasted image 20240719132526.png]]
![[Pasted image 20240719114421.png]]
![[Pasted image 20240719132436.png]]
![[Pasted image 20240719132631.png]]
![[Pasted image 20240719140907.png]]
Note, that in the below sketch of ELBO derivation for the entropy we are not taking the expectation over $q(\lambda | z)$ not $r(\lambda | z; \phi)$ as done in regural derivation to get the expectation over the joint distibution of $\lambda$ and $z$.
![[Pasted image 20240719140737.png]]
![[Pasted image 20240719150127.png]]
![[Pasted image 20240719150759.png]]
![[Pasted image 20240719150809.png]]
 
## Summary

## Bullet points
- 

## Questions
1. How the dependence between latent variables is induced exactly by introduction of the hierarchy?
	1. Perhaps there is only marginal independence of z's in the mean field part, but adding the prior over mean field parameters allows for not necessarily factorized $q_{HVM}(z;\theta) = \int q(\lambda;\theta)\prod_i q(z_i|\lambda_i) d\lambda$
		1. ikd exactly what it really is, but there is sthg called *shrinkage effect*. at first glance it is about the $\theta$ controlling the density over $\lambda$ and leading to relation between $z_i$'s as they are drawn from the distributions parameterized by $\lambda_i$'s 
	2. Hmm what is actually the shrinkage effect? - the chat agreed -  not sure weather it is corrct though
		1. The term "shrinking" in this context refers to placing the density over the variational parameters ($\lambda$) to a more structured set, which introduces dependencies among the latent variables.  In more detail: 
			1. **Mean-field Inference**: Each latent variable $z_i$ is treated independently, and the variational parameters $\{\lambda_1, \ldots, \lambda_d\}$ are fitted to match the posterior marginal for each latent variable separately. This leads to a factorized variational distribution $q_{MF}(z; \lambda) = \prod_{i=1}^d q(z_i; \lambda_i)$, which often fails to capture dependencies between latent variables.
			2. **Hierarchical Variational Models (HVMs)**: Instead of treating the variational parameters independently, HVMs introduce a prior distribution $q(\lambda; \theta)$ on the variational parameters. This prior induces a dependency structure among the $\lambda_i$s. The variational distribution $q_{HVM}(z; \theta)$ is then obtained by integrating out $\lambda$, as shown in the equation:     $$q_{HVM}(z; \theta) = \int q(\lambda; \theta) \prod_{i} q(z_i | \lambda_i) d\lambda$$ This hierarchical approach effectively "shrinks" the variational parameters towards a common structure dictated by the prior. The shrinkage effect means that the variational parameters are not just independently optimized but are influenced by a shared higher-level structure. This structured set over $\lambda$ allows the model to better capture the dependencies among the latent variables, leading to a more accurate approximation of the posterior distribution.  Thus, "shrinking" in this context involves the hierarchical model pooling information across different latent variables, which results in more coherent and structured variational parameters that improve the overall approximation of the posterior.`

## References / Note links
1. 