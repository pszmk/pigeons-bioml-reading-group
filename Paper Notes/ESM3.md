## Summary

**skip the main paper, read appendix!**

### Input Track Processing
There are 7 unique input tracks to ESM3: (a) **sequence** (amino acid tokens), (b) **structure coordinates**, (c) **structure tokens**, (d) **8-class secondary structure labels (SS8)**, (e) **quantized solvent-accessible surface area (SASA)** values, (f) **function keyword tokens** and (g) **residue (InterPro) annotation binary features**.

![[Pasted image 20240905141856.png]]

There are two additional tracks used during pretraining only: (h) per-residue confidence (pLDDT) and (i) averaged confidence (pLDDT). At inference time, these values are fixed, and these tracks are equivalent to adding a constant vector z_plddt.
### Geometric attention
In short we rotate the Q, K according to backbone frames relative rotation matrix - this is invariant to reference frame as when changing reference rotation we would multiply the relative rotation matrices by the same matrix which would cancel out in dot product.
![[Pasted image 20240906133936.png]]
![[Pasted image 20240906134454.png]]
#### Tokenizing structure
How are we processing the input of shape $L \times 16 \times d$ in transformer -> I assume it is by calculating attention only for the sequences of length $16$  as flattening to $(L \times 16) \times d$ and reshaping after computation does not make sense since relative distances refer to the token of index $i$. To improve training and inference efficiency, we encode all local structure graphs within a protein in parallel. In practice, this means that given a batch of B proteins with average sequence length L, then the inputs to the structure encoder will have shape BL × 16 × d.
![[Pasted image 20240906143403.png]]
![[Pasted image 20240906144607.png]]
![[Pasted image 20240906144709.png]]
#### Decoding Structure Tokens Into Atom Coordinates
![[Pasted image 20240907115708.png]]
![[Pasted image 20240907115725.png]]
When using a VQ-VAE to learn discrete representations which maximize reconstruction quality, it is common to train in the autoencoder in two stages (76). In the first stage, the encoder and codebook is learned with a relatively small and efficient decoder. In the second stage, the encoder and codebook are frozen and a larger or otherwise more computationally expensive decoder is trained to maximize reconstruction quality.
![[Pasted image 20240907145221.png]]
![[Pasted image 20240907145301.png]]
#### Structure prediction losses for stage 1 of VQVAE training
![[Pasted image 20240907145612.png]]
The arrows below define vectors.
![[Pasted image 20240907145920.png]]
6 not 9 as we are disregarding trivial diagonal of pairwise dotproducts
![[Pasted image 20240907151648.png]]
![[Pasted image 20240907151844.png]]
![[Pasted image 20240907151905.png]]
- **C_alpha (C_α)** is the central carbon atom in an amino acid that is bonded to the amino group (NH₂), the carboxyl group (COOH), a hydrogen atom, and the side chain (R group) specific to each amino acid.
- **C_beta (C_β)** is the first carbon atom in the side chain of an amino acid, attached directly to the C_alpha. It’s a key part of the side chain structure for all amino acids except glycine, which has no side chain and therefore no C_beta atom.
Inverse folding loss predicts position in the sequence actually.
![[Pasted image 20240907151924.png]]
#### Structure prediction losses for stage 2 of VQVAE training
In the second stage of VQ-VAE training, the encoder and codebook are frozen and a new, deeper decoder is trained. This second stage of training has multiple purposes. First, a larger decoder improves reconstruction quality. Second, augmented structure tokens from ESM3 are added to enable learning pAE and pLDDT heads. Third, we add sequence conditioning and train with all-atom geometric losses to be able to decode all-atom protein structures. Fourth, we extend the context length of the decoder to be able to decode multimers and larger single chain proteins.

### 1. **pAE (Predicted Aligned Error)**:
   - **Purpose**: pAE quantifies the predicted positional error between pairs of residues in the predicted protein structure. It gives an estimate of how much error there might be in the relative positions of two residues in the 3D structure.
   - **Interpretation**: Lower pAE values indicate that the predicted relative position of two residues is likely more accurate, while higher values suggest less confidence in their relative positioning.
   - **Usage**: The pAE is particularly useful for understanding the uncertainty or confidence in specific regions of the protein structure, especially in long-range interactions where residues are far apart in the sequence.
   - **Loss Function**: The pAE loss would be used in training models to minimize the discrepancy between the predicted and actual aligned positions of residues, improving the overall accuracy of pairwise distance predictions.

### 2. **pLDDT (Predicted Local Distance Difference Test)**:
   - **Purpose**: pLDDT is a per-residue confidence score that estimates how well the local geometry of each residue in the predicted structure matches the actual protein structure. It gives an idea of how confidently the model predicts the local structure around each residue.
   - **Interpretation**: pLDDT values range from 0 to 100. Higher pLDDT values (closer to 100) indicate higher confidence in the local structural prediction of that residue, while lower values suggest lower confidence.
   - **Usage**: The pLDDT score is used to assess the reliability of different regions of the predicted protein structure. Regions with high pLDDT scores are more likely to be accurately modeled, whereas regions with low scores may need further refinement or have inherent flexibility.
   - **Loss Function**: In training, the model minimizes the loss related to pLDDT by improving the predicted local geometry of each residue, encouraging more accurate and confident predictions of residue positions and bond angles.

Both losses complement each other in the training of protein structure prediction models. While pAE focuses on the global alignment and positioning of residues in the protein, pLDDT focuses on the accuracy of local structural details.

The structure token decoder was trained in three stages: 2A, 2B, 2C detailed in Table S2. The purpose of stage 2A is to efficiently learn decoding of all-atom structures. Enhanced training efficiency is achieved by keeping a short context length and omitting the pAE and pLDDT losses, which are both memory-consuming and can be in competition with strong reconstruction quality. In stage 2B, we add the pAE and pLDDT losses. These structure confidence heads cannot be calibrated unless structure tokens are augmented such that ESM3-predicted structure tokens are within the training distribution. To this end, for stages 2B and 2C we replace ground truth structure tokens with ESM3-predicted structure tokens 50% of the time. In stage 2C, we extend context length to 2048 and upsample experimental structures relative to predicted structures.
### Architecture
- Bidirectional transformers
- ####  **Geometric Attention**
	ESM3 implements a Geometric Attention layer, which is stacked with sequence attention to produce contextual embeddings that consider both. In essence, amino acids are represented as a set of three-dimensional coordinates and put into distance matrices. Amino acids closer to one another get higher attention scores, allowing the model to selectively attend to spatially proximal residues in the protein structure and their potential interactions.

- #### **Chain of Thought Generation**
	In generation, ESM-3 first defines a backbone and works from an iterative-refinement approach that alternates between sequence and structure. This ensures both correct structure and sequence generation, and results in a comprehensive understanding of the entire protein over sequence, structure and function prediction.
	![[Pasted image 20240817232436.png]]

![[Pasted image 20240907174429.png]]
![[Pasted image 20240907174606.png]]
![[Pasted image 20240907174652.png]]
![[Pasted image 20240907174729.png]]
![[Pasted image 20240907175252.png]]
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