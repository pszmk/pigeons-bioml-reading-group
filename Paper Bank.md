# TODO 
- actually this list does not work to well -> we can make a database out of it =D
	- it would be better to define tags and add them to the papers. a filtering option would be great
	- use [Dataview](https://github.com/blacksmithgu/obsidian-dataview) community plugin

If there is corresponding note link it after the paper using [[]] and pointing to the note file - the note does not need to have the same name as the paper and may be more general or specific.
#### Selection procedure
Although the papers are already preselected  here they need to be chose to be examined further and slection procedure is specified:
- `+` is used as a vote for importance of going through a paper, anyone can add any number of votes. overall maximum number of votes is 5.
- papers with the highest number of votes are selected for further analysis and interesting bits are discussed during the meeting / used in research etc..
---
## AE
- [Masked Autoencoders Are Scalable Vision Learners](https://arxiv.org/abs/2111.06377)
- ++[From Variational to Deterministic Autoencoders](https://arxiv.org/abs/1903.12436) RAE
-> [Wasserstein Auto-Encoders](https://arxiv.org/abs/1711.01558) WAE
---
## VAE
- +[Fixing a Broken ELBO](https://arxiv.org/pdf/1711.00464)
-> [InfoVAE: Information Maximizing Variational Autoencoders](https://arxiv.org/abs/1706.02262) note [[InfoVAE Balancing Learning and Inference in Variational Autoencoders]]
- [Semi-supervised Learning with Deep Generative Models](https://arxiv.org/pdf/1406.5298)
- +[VARIATIONAL LOSSY AUTOENCODER](https://arxiv.org/pdf/1611.02731)
- +[Hamiltonian Variational Auto-Encoder](https://papers.nips.cc/paper_files/paper/2018/hash/3202111cf90e7c816a472aaceb72b0df-Abstract.html)
- ### Hierarchy
	- +[Hierarchical Variational Models](https://arxiv.org/pdf/1511.02386) note [[Hierarchical Variational Models]]
	- +[NVAE: A Deep Hierarchical Variational Autoencoder](https://proceedings.neurips.cc/paper/2020/file/e3b21256183cf7c2c7a66be163579d37-Paper.pdf)
	- ++ [Fast and precise single-cell data analysis using a hierarchical autoencoder](https://www.nature.com/articles/s41467-021-21312-2?fromPaywallRec=false)
- ### IWAE
	-> [Importance Weighted Autoencoders](https://arxiv.org/pdf/1509.00519) note [[Importance Weighted Autoencoders]]
	- [Hierarchical Importance Weighted Autoencoders](http://proceedings.mlr.press/v97/huang19d/huang19d.pdf)
	- [On importance-weighted autoencoders](https://arxiv.org/abs/1907.10477)
	- [DEBIASING EVIDENCE APPROXIMATIONS: ON IMPORTANCE-WEIGHTED AUTOENCODERS AND JACKKNIFE VARIATIONAL INFERENCE](https://www.microsoft.com/en-us/research/uploads/prod/2018/04/On-Importance-weighted-Autoencoders-and-Jackknife-Variational-Inference.pdf)
- ### Discrete variables - continuous latent
	- +[Grammar Variational Autoencoder](https://arxiv.org/abs/1703.01925)
	- +[Automatic Chemical Design Using a Data-Driven Continuous Representation of Molecules](https://arxiv.org/abs/1610.02415)
- ### Priors & Posteriors
	->[VAE with a VampPrior](https://proceedings.mlr.press/v84/tomczak18a/tomczak18a.pdf) note [[Paper Notes/VAE with a VampPrior|VAE with a VampPrior]]
	- [Variational Inference with Normalizing Flows](https://proceedings.mlr.press/v37/rezende15.html)
	- +[Stick-breaking variational autoencoders](https://arxiv.org/abs/1605.06197)
	- [Variational inference with Stein mixtures](https://approximateinference.org/2017/accepted/NalisnickSmyth2017.pdf)
	- [Learning approximately objective priors](https://arxiv.org/abs/1704.01168)
	- [Learning priors for invariance](http://proceedings.mlr.press/v84/nalisnick18a.html)
	- + [Nonparametric Variational Auto-encoders for Hierarchical Representation Learning](https://arxiv.org/abs/1703.07027)
	- #### Conditional
		- [Discovering highly potent antimicrobial peptides with deep generative model HydrAMP](https://nature.com/articles/s41467-023-36994-z)
	- ## GMM
		- ++ [Variational Deep Embedding: An Unsupervised and Generative Approach to Clustering](https://www.ijcai.org/proceedings/2017/0273.pdf)
		-  ++[Approximate Inference for Deep Latent Gaussian Mixtures](http://bayesiandeeplearning.org/2016/papers/BDL_20.pdf)
			- różna liczba komponentów w priorze/posteriorze
---
## General look at Generative Modelling
- ### Generalization
	- #### Distribution shift, out of distribution samples detection
		- +[Do deep generative models know what they don't know?](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=cb1ZN7AAAAAJ&citation_for_view=cb1ZN7AAAAAJ:8k81kl-MbHgC)
		- +[Detecting out-of-distribution inputs to deep generative models using typicality](https://arxiv.org/abs/1906.02994)
		- [Beyond Top-Class Agreement: Using Divergences to Forecast Performance under Distribution Shift](https://arxiv.org/abs/2312.08033)
	- #### Regularization
		- [Spectral Norm Regularization for Improving the Generalizability of Deep Learning](https://arxiv.org/abs/1705.10941)
	- #### Robustness
		- #### Masked modelling
		- #### Denoising
---
## Multimodal, multidataset etc.
Sometimes translation is mixed with integration and the papers are not repeated.
- [Multimodal attention-based variational autoencoder for clinical risk prediction](https://ieeexplore.ieee.org/document/10385792/metrics#metrics) 
- +++ [Robust single-cell matching and multimodal analysis using shared and distinct features](https://www.nature.com/articles/s41592-022-01709-7)
- ++++[Biologically informed deep learning to query gene programs in single-cell atlases](https://www.nature.com/articles/s41556-022-01072-x)
- ## Translation
	- +++[scButterfly: a versatile single-cell cross-modality translation method via dual-aligned variational autoencoders](https://www.nature.com/articles/s41467-024-47418-x?fromPaywallRec=false)
	- [Multi-Domain Translation by Learning Uncoupled Autoencoders](https://arxiv.org/abs/1902.03515)
	- paywall [Recovery of missing single-cell RNA-sequencing data with optimized transcriptomic references](https://www.nature.com/articles/s41592-023-02003-w?fromPaywallRec=false)
- ## Domain adaptation
	- +++[Domain-Specific Batch Normalization for Unsupervised Domain Adaptation](https://arxiv.org/pdf/1906.03950)
		- seems not too hard to add it to the current models
		- could be integrated actually with the batch conditioning model which would provide these parameters. but it would not be as straightforward as using conditioning, but would perhaps allow to adjust the parameters better in case of small number of samples in a given dataset
		- how it works when we only fine tune in this way?
- ## Integration - mainly single cell data
	-> omivae [Integrated Multi-omics Analysis Using Variational Autoencoders: Application to Pan-cancer Classification](https://arxiv.org/abs/1908.06278) | babel [BABEL enables cross-modality translation between multiomic profiles at single-cell resolution](https://pubmed.ncbi.nlm.nih.gov/33827925/) | aae [Multi-domain translation between single-cell imaging and sequencing data using autoencoders](https://www.nature.com/articles/s41467-020-20249-2) note [[OmiVAE, BABEL, AAE GAN latent matching]]
	-->[A unified computational framework for single-cell data integration with optimal transport](https://www.nature.com/articles/s41467-022-35094-8?fromPaywallRec=false) note [[A uniﬁed computational framework for single-cell data integration with optimal transport]]
	- ++[Semi-supervised integration of single-cell transcriptomics data](https://www.nature.com/articles/s41467-024-45240-z?fromPaywallRec=false)
	- ++[MAGAN: Aligning Biological Manifolds](https://arxiv.org/abs/1803.00385)
	- ++ [scMoMaT jointly performs single cell mosaic integration and multi-modal bio-marker detection][https://www.nature.com/articles/s41467-023-36066-2?fromPaywallRec=false]
	- ++[Multi-omics single-cell data integration and regulatory inference with graph-linked embedding](https://www.nature.com/articles/s41587-022-01284-4?fromPaywallRec=false)
	- [Probabilistic embedding, clustering, and alignment for integrating spatial transcriptomics data with PRECAST](https://www.nature.com/articles/s41467-023-35947-w?fromPaywallRec=false)
	- [Integration of spatial and single-cell data across modalities with weakly linked features](https://www.nature.com/articles/s41587-023-01935-0?fromPaywallRec=false)
	- + [Paired single-cell multi-omics data integration with Mowgli](https://www.nature.com/articles/s41467-023-43019-2?fromPaywallRec=false)
	- [Scanorama: integrating large and diverse single-cell transcriptomic datasets](https://www.nature.com/articles/s41596-024-00991-3?fromPaywallRec=true)
	- [Online single-cell data integration through projecting heterogeneous datasets into a common cell-embedding space](https://www.nature.com/articles/s41467-022-33758-z)
	- [scCobra: Contrastive cell embedding learning with domain-adaptation for single-cell data integration and harmonization](https://www.biorxiv.org/content/10.1101/2022.10.23.513389v2)
---
### Single cell
- [Paper List](https://github.com/OmicsML/awesome-deep-learning-single-cell-papers)
- 
---
### Twitter
- https://x.com/mo_lotfollahi
### Transformers
- +++++ [REPO WITH SC TRANSFORMER PAPERS](https://github.com/theislab/single-cell-transformer-papers)
- +++++ [scGPT: Towards Building a Foundation Model for Single-Cell Multi-omics Using Generative AI](https://www.biorxiv.org/content/10.1101/2023.04.30.538439v1.full)
- +++++ [scBERT as a large-scale pretrained deep language model for cell type annotation of single-cell RNA-seq data](https://www.nature.com/articles/s42256-022-00534-z)
- [CELLPLM: PRE-TRAINING OF CELL LANGUAGE MODEL BEYOND SINGLE CELLS](https://openreview.net/pdf?id=BKXvPDekud)
- [scmFormer Integrates Large‐Scale Single‐Cell Proteomics and Transcriptomics Data by Multi‐Task Transformer](https://www.researchgate.net/publication/378963194_scmFormer_Integrates_Large-Scale_Single-Cell_Proteomics_and_Transcriptomics_Data_by_Multi-Task_Transformer)
- [Single-Cell Multimodal Prediction via Transformers](https://arxiv.org/pdf/2303.00233)
- [scGREAT: Transformer-based deep-language model for gene regulatory network inference from single-cell transcriptomics](https://www.sciencedirect.com/science/article/pii/S258900422400573X)
### Diffusion
- [scRDiT: Generating single-cell RNA-seq data by diffusion transformers and accelerating sampling](https://arxiv.org/html/2404.06153v1)
## XAI
- 
---
## Latent evaluation
- iwae has some method
---
## AMP (Anti Microbial Peptides)
- [Machine learning for antimicrobial peptide identification and design](https://www.nature.com/articles/s44222-024-00152-x?fromPaywallRec=false)
---
## Concepts
- +[A Kernel Two-Sample Test](https://jmlr.csail.mit.edu/papers/v13/gretton12a.html)