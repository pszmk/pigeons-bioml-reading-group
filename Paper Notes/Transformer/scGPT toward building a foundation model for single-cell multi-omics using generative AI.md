## Summary
scGPT adds a new way of sequentially predicting a lot of outputs depending of the model's cofidence. They build and train an easily fine-tuned foundation model, which they claim is SOTA (but they compare only with MLP and ). They use in-memory data for the fast access to store datasets. They build model on over 10 million cells.
#### Embeddings
- GENE_TOKENS - assign a number to gene
- CONDITION_EMBEDDING - meta information for each gene separately. For example functional pathways or perturbation experiment alterations.
- EXPRESSION_VALUE_EMBEDDINGS - value binning for expressions
A fundamental challenge in gene expression modeling is the variability in absolute magnitudes across different sequencing protocol. Due to variations in sequencing depths and the presence of sparsely expressed genes, the data scales differ significantly among different batches of sequencing samples. These differences are not easily mitigated with common preprocessing techniques such as transcripts per million (TPM) normalization and log1p transformation 
	![[Pasted image 20240806113334.png]]
	- dependent of M - the number of highly variable genes
- CELL_EMBEDDING - \<CLS\> TOKEN
- INPUT_EMBEDDING: per cell gene (pytorch) embeddings are a sum of gene, condition and binned expression embeddings
	![[Pasted image 20240806114039.png]]
- BATCH AND MODALITY TOKENS
	![[Pasted image 20240806115207.png]]
	![[Pasted image 20240806115345.png]]
	
	
About input tokens: each token in the input embedding can be from one of three groups:
	1. CLS for cell embedding
	2. Known genes with token embedding and expression value embeddings
	3. Unknown genes whose expression values will be predicted. 
#### Generative training
This is really strange. It seems that they are doing generation during training.
They designed Gene Expression Prediction task, as a generative self-supervised objective to iteratively preduct gene expression values of unknown cells from known tokens.

![[Pasted image 20240806115715.png]]
![[Pasted image 20240806124153.png]]
Why don't we leave unmasked the 
![[Pasted image 20240806144145.png]]
During the inference for cell-prompt generation, scGPT generates all genome-wide gene expressions conditioned on the specific cell types. A trained cell embedding is inputted at the first position representing the cell type condition. The whole generation process of thousands of gene expressions is conducted in K iterative steps. For example, in one iteration i ∈ {1, 2, . . . K}, the attention masking mechanism allows attention with all predicted genes from previous 0 to i − 1 iterations. In each iteration, scGPT selects the top 1/K genes from the unknown set with the highest prediction confidence to be included as known genes in the next iteration i + 1. Intuitively, this workflow streamlines the generation of large groups of gene expressions in an auto-regressive manner, where gene expressions with highest prediction confidence are first generated and used to help subsequent rounds of generation. The gene-prompt generation works similarly in an iterative manner. The difference is that it starts with a set of known genes with observed expression values, instead of a cell embedding.
### "Finetuning" Tasks - tdk what they mean by finetuning

Their customised fine-tuning:
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
![[Pasted image 20240806144505.png]]
Ok but gimmie tableki -.-
Asia's comment: Are the clusters more clear in scGPT case? I don't think so. NMI, ARI_ASW is mainly comparable with Harmony. 
![[Pasted image 20240806144407.png]]
Asia: In this case clusters are more visible, but let's not exaggerate. Metrics are better, but there are only two of them so... fine-tuning visibly improves performance for small number of epochs for 10x multiome.  
![[Pasted image 20240806144350.png]]
Asia: ok and?? these plots look like a random thing 
TODO: understand this:
The interactivity between transcription factors, cofactors and target genes underlying a Gene Regulatory Network (GRN) mediates important biological processes. Existing GRN inference methods often rely on correlation in static gene expressions or pseudo-time estimates as a proxy for causal graphs [46]. scGPT, optimized by the generative training of gene tokens, implicitly encodes such relationships in its gene embeddings. The gene embeddings can therefore be applied to construct similarity networks that entail gene-gene interactions. We hereby validate the scGPT’s gene embedding network against known biology, and then explore its applicability to gene program discovery.

### **Metrics**
- Pearson correlation
- $corr(\Delta)$ - measures the correlation based on magnitude of expression change post-perturbation compared to the control. They claim this metric is better in the case where high percent of gene expression counts are zero in the data
- the results are not super good, MLP is better in one case (-.-)

## Bullet points
- M highly variable genes selected
- new in sc mixing of masked and causal generation
- they (allegedly) have good batch correction and is better for adding new data modalities to pre-trained model than from the scratch 

## Questions
1. cell is composed of genes. is the cell type deterministic? i guess not due to noise (batch effect)

## References / Note links
1. #pub2024
2. [biorxiv](https://www.biorxiv.org/content/10.1101/2023.04.30.538439v1.full)
3. [repo](https://github.com/bowang-lab/scGPT/tree/main)
4. 