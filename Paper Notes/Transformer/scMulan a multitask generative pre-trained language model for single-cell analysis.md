## Summary

Their objective is to create a foundation model that uses metadata and macroscopic information (such as sex, tissue, organ).  They propose combining all data, training task and potential "promts" for transformer into "cell sentences" (c-sentences) (more in Cell representation).

They propose to use 3 pre-training tasks: 1) conditional cell generation, 2) dual hierarchical cell type annotation and 3) metadata prediction. 

#### Cell representation
Example c-sentence:
$(Heart, 0), (Cardiomyocyte, 0), (A2M, 0.2), ..., (CD83, 0.1), (E, 0)$
This representation indicates that the cell originates from the heart, is a cardiomyocyte, and expresses certain genes. The final token $(E, 0)$ marks the end of the c-sentence. All tokens that do not represent gene expressions have values equal to $0$.

#### Objective
The goal is to minimize the negative log-likelihood of:
$P({E - {e_1, e_2, ..., e_i}} | e_1, e_2, ..., e_i; v_1, v_2, ..., v_i)$ where $E$ represents the set of all entities in a c-sentence and ${E - {e_1, e_2, ..., e_i}}$ set of entities not yet conditioned upon and $v_i$ is a value of entity $e_i$. Additionally, regression is used to predict the expression values of unobserved genes.  

#### Pre-training promt
Pre-training is unified by adding task tokens to the c-sentence. For example:
- Cell generation task:
	$(Heart, 0), (g_1, 0.8), (g_2, 0.6), (cell generation, 0)$ 
	should sequentially output:
	$(g_3, 0.5), ..., (g_n, 0.6), (E, 0)$
	Where $(cell generation, 0)$ is a promt. 

- Cell annotation task:
	$(CD3D, 0.7), (CD4, 0.6), ..., (cell type annotation, 0)$ 
	should return
	$(Tcell, 0), (CD4 T cell, 0), (E, 0)$.

#### Pre-training tasks
Using the c-sentence structure, the model is uniformly trained on the following tasks:
- **Conditional Cell Generation**: Conditioned on metadata to generate gene expression values.
- **Dual Hierarchical Cell Type Annotation**: Annotating both coarse-grained and fine-grained cell types.
- **Metadata Prediction**: Predicting the originating organ/tissue and specific region. All available metadata is utilized to enhance performance.

#### Architecture
- **Model type**: decoder-only transformer
- **Configuration**:
	- 20 Transformer decoder blocks
	- each with 20 attention heads
	- hidden layer dimension: 1120
- Additional embedding layers for **entity and value embedding**, and prediction heads for **entity and value prediction**.

## Benefits over scGPT
- Performs zero-shot learning more effectively.
- Unlike scGPT, which trains on a single task using only microscopic information, this model handles multiple tasks and integrates macroscopic information.
- Overall performance metrics show significant improvement.
![[Pasted image 20240817235244.png]]
![[Pasted image 20240817235344.png]]
## Questions
1. why not treat metainformation tokens as a (0, 1)? and then do classification?

## References / Note links
1. [github](https://github.com/SuperBianC/scMulan)
2. paper:  [[scMulan_a_multitask_generative_pre-trained_languag.pdf]]
3. supplement: [[scmulan_supplementary.pdf]]
4. #pub2024 