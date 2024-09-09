## Summary

### Embeddings
![[Pasted image 20240818000020.png]]
 Illustration of the embeddings of scBERT. The preprocessed scRNA-seq data are first converted into discretized expression, and then the non-zero expressions are randomly masked. 
 Taking the first gene as an example, the gene embedding $E_{G1}$ (the gene identity from gene2vec falling into the first bin) and the expression embedding $E_{B2}$ (the gene expression falling into the second bin and being transformed to the same dimension as the EG1) are summed and fed into scBERT to generate representations for genes. The representations are then used for pretraining or fine-tuning.
### Architecture
![[Pasted image 20240817235829.png]]
**Self-supervised learning on unlabelled data and fine-tuning on task-specific data**. At the self-supervised pretraining stage, unlabelled data were collected from PanglaoDB. Masked expression embedding and gene embedding were added as input and then fed into the **Performer** blocks. The reconstructor was used to generate outputs. Outputs for masked genes were used to calculate the reconstruction loss. 
At the **supervised fine-tuning stage**, the task-specific scRNA-seq data were input into the pretrained encoder. The output representation then passed a one-dimensional convolution layer and a classifier to generate the cell type prediction. ⊕ represents element- wise addition. The Performer encoder is the component that is shared between the models used in the pretraining and fine-tuning stages. The reconstructor and the classifier are independently and separately employed for the models during the pretraining and fine-tuning processes.
## Bullet points
- 

## Questions
1. 

## References / Note links
1. #pub2022
2. paper: [[scBERT.pdf]]
3. [github](https://github.com/TencentAILabHealthcare/scBERT)