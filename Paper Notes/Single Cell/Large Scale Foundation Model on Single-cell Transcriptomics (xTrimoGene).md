## Summary
scFoundation can serve as a foundation model for single-cell transcriptomics and achieve state-of-the-art performances in a diverse array of downstream tasks, such as gene expression enhancement, tissue drug response prediction, single-cell drug response classification, and single-cell perturbation prediction.

#### Challenges is sc foundational models:
- First, the gene expression pre -training data needs to encompass a landscape of cells across different statuses and types.
- Second, when modeling each cell as a sentence and each gene expression value as a word, the nearly 20,000 protein-coding genes make the “sentence” exceptionally long,
- Third, scRNA-seq data across different sequencing techniques and laboratories exhibit high variance in sequencing read depth. This technical noise prohibits the model from learning uniform and meaningful representations for cells.
#### Contibutions
- In this study, we address these challenges and designed the first large-scale foundational model scFoundation of 100M parameters working on ~20,000 genes. We collect the largest scRNA-seq data set with over 50 million gene expression profiles for pre-training, covering cells from different statuses and various tissues.
- We develop a read-depth-aware pre-training task that enables scFoundation not only to model the gene co-expression patterns within a cell but also to link the cells with different read depths.

#### xTrimoGene model
![[Pasted image 20240906153158.png]]
We developed a large-scale model, scFoundation, modeling 19,264 genes with 100 million parameters pretrained on over 50 million scRNA-seq data. To the best of our knowledge, this is the largest model parameter size, gene coverage, and data scale in the single-cell field.

Continous expression value encoding as opposed to eg. scGPT, but claim as if it was their contribution.
##### Input to the model
The encoder only accepted embeddings of the non-zero and non-masked expressed genes as input, and the decoder accepted all genes’ embedding (i.e. the encoder processed embeddings and zero and mask embeddings) as input. This architecture gave differential attention and computational resources to zero and non-zero values, thereby achieving the efficient learning of all gene relationships without any selection (e.g., highly variable gene selection).
#### Data source
![[Pasted image 20240906153322.png]]
We constructed a comprehensive single-cell gene expression data set by collecting data from all publicly available single-cell resources, including GEO17, Single Cell Portal, HCA4, EMBL-EBI18, etc. We aligned all data to a consolidated gene list that comprised 19,264 protein-coding and common mitochondrial genes, as identified by the HGNC19. After data quality control (Methods), we got over 50 million human scRNA-seq data for pre-training. The abundant data sources made our pre-training dataset rich in biological patterns. From an anatomical perspective, the data covered more than 100 tissue types under different diseases, tumors, and normal states (Fig. 1A); From a cell ontology perspective, the data encompassed almost all known human cell types and cell states.
### New pre-training task Read Depth Aware Modelling (RDA)
![[Pasted image 20240906153310.png]]
robustness to differing read depths - I guess that, it is not the only source of batch effect though

We developed a new pre-training task called the read-depth-aware (RDA) modeling, which was an extension of masked language modeling16, considering single-cell gene expression data had a high variance in read depth, especially in the large-scale pre-training data. In RDA, we trained the model to predict the masked gene expression of a cell based on other genes’ context. The context was from a counterpart or a low read-depth variant of that cell’s gene expression profile.

We treated the total count of all gene expressions as the measure of one cell’s read depth and defined two total count indicators: T (representing 'target') and S (representing 'source'), corresponding to the total counts of the raw and input samples respectively. We randomly masked the expression values of genes in the input sample and recorded the index of masked genes. Then the model took the masked input sample and two indicators to predict the expression value of the raw sample at the masked index (Fig. 1B). A regression loss was conducted on the predicted and raw gene expression values. This pre-training process enabled the pre-trained model not only to capture the gene-gene relationship within the cell but also to harmonize the cell with different read depths. When used for inference, the number T could control the total count of the output gene expression profiles. Thus, we could feed the cell's raw gene expression to the pre-training model and set the T higher than its total count S to generate a gene expression value with enhanced sequencing depth.

### Downstream tasks
![[Pasted image 20240906153350.png]]
## Bullet points
- Read Depth Aware Modelling

## Questions
1. 

## References / Note links
1. 