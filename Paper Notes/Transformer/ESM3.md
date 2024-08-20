## Summary

**skip the main paper, read appendix!**

### **Input Track Processing**
ESM-3 has three separate input tracks for sequence, structure and function, allowing each to be prompted partially or in full. These tracks are processed separately before being combined into a single latent space, making the model not only capable of answering all three tasks, but also grants it an understanding of the protein domain unique only to itself.
![[Pasted image 20240817232308.png]]
### Architecture
- Bidirectional transformers
- ####  **Geometric Attention**
	ESM3 implements a Geometric Attention layer, which is stacked with sequence attention to produce contextual embeddings that consider both. In essence, amino acids are represented as a set of three-dimensional coordinates and put into distance matrices. Amino acids closer to one another get higher attention scores, allowing the model to selectively attend to spatially proximal residues in the protein structure and their potential interactions.

- #### **Chain of Thought Generation**
	In generation, ESM-3 first defines a backbone and works from an iterative-refinement approach that alternates between sequence and structure. This ensures both correct structure and sequence generation, and results in a comprehensive understanding of the entire protein over sequence, structure and function prediction.
	![[Pasted image 20240817232436.png]]
## Bullet points
- l a r g e
- also uses different pre-training prompts
- this paper is so hard to read fr

## Questions
1. 

## References / Note links
1. #pub2024
2. paper: [[esm3.pdf]]
3. [github](https://github.com/evolutionaryscale/esm)
4. [hugging face](https://huggingface.co/EvolutionaryScale/esm3-sm-open-v1)