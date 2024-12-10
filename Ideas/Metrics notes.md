
#### Cell types assignment - classic metrics
- Accuracy, precision, recall (higher is better)
- MacroF1 (higher is better) $MacroF1 = \sum_{c \in C} \frac{F1_c}{N_c}$ where $F1_c = \frac{2 \times precision_c \times recall_c}{percision_c + recall_c}$ where $C$ is a set of classes

#### Clustering metrics
- Louvian clustering (higher is better):
	- **Modularity**:
	    - Modularity is a measure used to quantify the quality of a division of a network into communities.
	    - It compares the density of edges inside communities with the density of edges expected if the network were random.
	    - A high modularity score indicates a division where there are more edges within communities than expected by chance.
	- **Phases of the Louvain Algorithm**: The Louvain method works in two main phases, iterated until no further improvement in modularity can be achieved.
		- **Phase 1: Local Optimization**
		    - Initially, each node in the network is assigned to its own community.
		    - Nodes are then iteratively moved to neighboring communities, where each move is decided based on whether it increases the modularity of the network.
		    - The algorithm attempts to maximize modularity by finding the best local community for each node.
    
	    - **Phase 2: Community Aggregation**
		    - Once no more single-node movements can improve modularity, communities are aggregated into super-nodes, creating a new network of these super-nodes.
		    - Edges between communities are represented as weighted edges between super-nodes.
		    - The process then repeats on this new network, applying the same local optimization process.
#### Single cell integration
- Normalized Mutual Information ((0, 1) range; higher is better) and on them do Louvian clustering with resolutions range(0.1, 2, 0.1), with best score selected. 
- Adjusted Rand Index ((0, 1) range; higher is better): The adjusted rand index (ARI) was employed to assess both the agreement between the annotated labels and the MNI-optimized Louvain clusters. Furthermore, the rand index was adjusted to account for randomly correct labels.
- Average Silhoutte Width ((-1, 1) range; higher is better): assesses the relationship between a cell's within-cluster distances and its distances to the closest cluster boundries. AWS is an average of widths of all cells. 
- Graph connectivity (higher is better): $GraphConn = \frac{1}{|C|} \sum_{c \in C} \frac{|LCC(G_c^{kNN})|}{N_c}$ where $LCC$ is the largest connected component. It quantifies the average proportion of cells within each cell type that are connected through a kNN graph. So for each $c$ we compute size of the $lcc$. 
- Aggregated matrics (higher is better):
	- $AvgBIO = (ARI_{cell} + NMI_{cell} + ASV_{cell}) / 3$ 
	- $AvgBatch = (ASW_{batch} + GraphConn) / 2$
	- $Overall = 0.6 AvgBIO + 0.4 AvgBatch$