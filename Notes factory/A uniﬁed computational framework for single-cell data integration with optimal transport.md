## Summary
![[Pasted image 20240726133957.png]]
![[Pasted image 20240726135307.png]]
### Incorporating explicitly OT plan of moving the samples as a loss term
![[Pasted image 20240726100004.png]]
![[Pasted image 20240726080902.png]]
![[Pasted image 20240726080942.png]]
![[Pasted image 20240726082226.png]]
![[Pasted image 20240726082247.png]]
### Contrastive modification of the OT based objective
I think this Frobenius product with $F$ prior matrix is done only when finding $T$ matrix to drive up the mass corresponding to the positive pairs. After that their corresponding losses have greater impact on the gradient descent. 
![[Pasted image 20240726083018.png]]
### Loss formulation
![[Pasted image 20240726101058.png]]
## Bullet points
- uses coupled VAE with additional decoders
- dataset specific batchnorm layers
	- how it works when the batch is mixed?
- uses explicit iteratively found solution of the OT at the minibatch level
- source of cell type derived evaluation metrics
- sourse of already implemented "sota" techniques for benchmarking

## Questions
1. 
## References / Note links
1. #multi-modal-integration