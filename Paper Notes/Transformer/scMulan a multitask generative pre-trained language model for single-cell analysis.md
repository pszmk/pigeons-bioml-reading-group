## Summary
![[Pasted image 20240819084654.png]]
![[Pasted image 20240819084851.png]]
![[Pasted image 20240819085024.png]]
#### Generative objective
Increase the probability of the bag of genes not yet conditioned on.
![[Pasted image 20240819085727.png]]
#### Pre-training objectives
![[Pasted image 20240819090358.png]]
nll + MSE for value regression
![[Pasted image 20240819091507.png]]
## Bullet points
- ![[Pasted image 20240819093422.png]]
- ![[Pasted image 20240819093453.png]]

## Questions
1. How is selection of genes to be predicted done? How many?
2. Cell type annotation is done by considering only the logits corresponding to celltypes in Entity Prediction head?
3. How is cell representation used for UMAP obtained?
4. Is it better because of different training dataset?

## References / Note links
1. 