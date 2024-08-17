
#### Some stuff about cells
- Let's start with white cells. There is a ton of different types:
	- T-cells is **a type of white blood cell called lymphocytes**. The fights infection-causing pathogens (viruses, bacteria, fungi and parasites) and harmful cells, like cancer cells. eg CD4+, CD8+ 
	- B cells express B cell receptors (BCRs) on their cell membrane.   A lot of types.
	- Sometimes B-cells are activated by T-cells. They are binded together using BCR and it's hard to distinguish between them. That's why sometimes in dataset we have type indicating clusters of B-cells with T-cells.
	- Natural killer cells (large granular lymphocytes). NK cells provide rapid responses to virus-infected cells, stressed cells, tumor cells, and other intracellular pathogens based on signals from several activating and inhibitory receptors.  NK cells can be identified by the presence of CD56 and the absence of CD3 (CD56+, CD3−)
	- Granulocytes
	- Monocytes are _a type of white blood cell in your immune system that destroy germs and bacteria and_ alert other blood cells to help prevent infection. It's the largest type of leukocyte. It's a type of immune cell that is made in the bone marrow and travels through the blood to tissues in the body where it becomes:
		- a macrophage, which engulf and digest pathogens, such as cancer cells, microbes, cellular debris. eg CD14, CD40, CD11b
		- or a dendritic cell (DC), which process antigen material and present it on the cell surface to the T cells. They can be blinded from, for example, HIV. eg cDC, pDC, CD141+, CD 303+, MDDC (matured from monocytes), HP-DC.
	
What's the difference between innate and adaptive immune systems? TODO
- Notes from scGPT:
	- most important ML tasks in biology: 
		- multi-batch integration
		- multi-omics integration (focusing on modalities such as microbiome, proteome etc)
		- cell-type annotation
		- genetic perturbation prediction
		- gene network interference
	-  ML research is rather distributed and focus on specific task
	- it's important to capture both gene and cell level insights
	- scRNA-seq measures transcriptomic acitivites from RNA abundance, which inform on cell identity, stage, and functionality. 
	- there may be the case where the rare cell type with extremly low cell numbers in the reference set.
	- self-attention enables the encoding of intricate interactions between perturbed genes and the responses of other genes

Human Cell Atlases
- vast-scale atlases of single-cell RNA sequencing (scRNA-seq)
	- Human Cell Atlas
	- has tens of milions of cells
	- used for self-supervised objectives and to integrate across different organs and species
	- 