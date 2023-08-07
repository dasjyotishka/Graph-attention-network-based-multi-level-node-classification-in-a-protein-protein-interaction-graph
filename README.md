# Graph-attention-network-based-multi-level-node-classification-in-a-protein-protein-interaction-graph
This notebook was created as part of an assignment for a course on Advanced Deep Learning at CentraleSupélec offered by Dr. Guillaume Charpiat and Matthieu Nastorg


## Objective

Discovering disease pathways, which can be defined as sets of proteins associated with a given disease, is an important problem that has the potential to provide clinically actionable insights for disease diagnosis, prognosis, and treatment. Computational methods aid the discovery by relying on protein-protein interaction (PPI) networks. They start with a few known disease-associated proteins and aim to find the rest of the pathway by exploring the PPI network around the known disease proteins.

This problem aims to predict, for a given Protein Protein Interaction (PPI) graph, the correct node's labels. It is a node (multi-level) classification task (trained using supervised learning).

## Architecture

We have chosen a special version of Graph Attention Network (GAT) as the architecture of our model inspired by the architecture discussed in Petar Velickovic et al. In the original paper, the authors used a three-layer Graph Attention Network (GAT) model. The first two layers consisted of 4 attention heads computing 256 features (for a total of 1024 features), followed by an ELU nonlinearity. The final layer was used for (multi-label) classification, computing 121 features each, that were averaged and followed by a logistic sigmoid activation. In 2021, Brody et al. showed that by making a slight change in the operation of the GAT, the performance can be further improved. By applying the weight matrix 𝐖 after the concatenation, and using the attention weight matrix 𝐖ₐₜₜ after the LeakyReLU function, the authors claimed that GATv2Conv layer consistently outperforms GATConv layer and thus should be preferred.

## Dataset
We used the Protein-Protein Interaction (PPI) network dataset which includes:

20 graphs for training
2 graphs for validation
2 graphs for testing
One graph of the PPI dataset has on average 2372 nodes. Each node:

50 features : positional gene sets / motif gene / immunological signatures ...
121 (binary) labels : gene ontology sets (way to classify gene products like proteins).

