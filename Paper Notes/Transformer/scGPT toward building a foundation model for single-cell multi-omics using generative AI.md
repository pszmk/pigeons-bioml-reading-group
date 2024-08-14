## Summary
Add a new way of sequentially predicting a lot of outputs depending of the model's cofidence.
#### Embeddings
- GENE_TOKENS
- CONDITION_EMBEDDING - for each gene separately
- EXPRESSION_VALUE_EMBEDDINGS - value binning for expressions
	![[Pasted image 20240806113334.png]]
	- dependent of M - the number of highly variable genes
- CELL_EMBEDDING - \<CLS\> TOKEN
- INPUT_EMBEDDING: per cell gene embeddings are a sum of gene, condition and binned expression embeddings
	![[Pasted image 20240806114039.png]]
- BATCH AND MODALITY TOKENS
	![[Pasted image 20240806115207.png]]
	![[Pasted image 20240806115345.png]]
#### Generative training
This is really strange. It seems that they are doing generation during training.
![[Pasted image 20240806115715.png]]
![[Pasted image 20240806124153.png]]
Why don't we leave unmasked the 
![[Pasted image 20240806144145.png]]
![[Pasted image 20240806124511.png]]
### "Finetuning" Tasks - tdk what they mean by finetuning
#### Gene Expression Prediction (GEP)
![[Pasted image 20240806132859.png]]
#### Gene Expression Prediction for Cell Modelling (GEPC)
![[Pasted image 20240806133153.png]]
#### Elastic Cell Similarity (ECS) - peculiar
![[Pasted image 20240806133331.png]]
#### Domain Adaptation via Reverse Back-propagation (DAR)
![[Pasted image 20240806134217.png]]
Gradient Reversal layer multiplied the passing gradient by a negative constant only during backprop
Input Data --> Feature Extractor --> Task Classifier
                        |
	                    V
                        GRL
                        |
                        V
	            Domain Classifier
#### Cell Type Classification (CLS)
![[Pasted image 20240806134320.png]]
#### Downstream tasks
![[Pasted image 20240806135845.png]]
![[Pasted image 20240806135902.png]]
##### Celltype Annotation
![[Pasted image 20240806140019.png]]
![[Pasted image 20240806143055.png]]
![[Pasted image 20240806143111.png]]
#### Benchmarking
![[Pasted image 20240806143352.png]]
### Figures
![[Pasted image 20240806144540.png]]
![[Pasted image 20240806144505.png]]![[Pasted image 20240806144407.png]]
![[Pasted image 20240806144350.png]]
## Bullet points
- M highly variable genes selected
- new in sc mixing of masked and causal generation

## Questions
1. 

## References / Note links
1. #pub2024
2. [biorxiv](https://www.biorxiv.org/content/10.1101/2023.04.30.538439v1.full)
3. [repo](https://github.com/bowang-lab/scGPT/tree/main)
4. 