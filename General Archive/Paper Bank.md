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
	->[Hierarchical Variational Models](https://arxiv.org/pdf/1511.02386) note [[Hierarchical Variational Models]]
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
	->[VAE with a VampPrior](https://proceedings.mlr.press/v84/tomczak18a/tomczak18a.pdf) note [[VAE with a VampPrior|VAE with a VampPrior]]
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

---
# Target discovery
- [Machine learning for target discovery in drug development](https://api.repository.cam.ac.uk/server/api/core/bitstreams/42ab9f1f-ac3e-42a4-afe2-50f11d9f9c06/content)
---
### Single cell
- [Paper List 1](https://github.com/OmicsML/awesome-deep-learning-single-cell-papers)
- [Paper List 2](https://github.com/theislab/single-cell-transformer-papers)
---
### Twitter
- https://x.com/mo_lotfollahi

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
- encode and decode on different subsets
- target discovery?