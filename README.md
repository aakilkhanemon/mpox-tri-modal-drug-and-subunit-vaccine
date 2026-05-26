# Systems Pharmacology-Driven Discovery of Tri-Modal Anti-Mpox Therapeutics

This repository contains the complete computational workflow, data pipelines, and scripts for the design and evaluation of novel tri-modal therapeutics targeting the **Mpox virus (MPXV) VP39 methyltransferase**. 

By integrating electronic-level structural refinement with macroscale systems biology, this framework establishes a rigorous pipeline to identify high-affinity lead candidates capable of suppressing viral replication while simultaneously modulating critical host-directed hyper-inflammatory pathways.

---

## 🛠️ Project Architecture & Workflow Modules

The project is structured into distinct computational modules, transitioning from atomic-scale structural rescoring to macroscale network pharmacology.

### 1. Structural Rescoring & Affinity Prediction (`/structural_rescoring`)
To minimize the false-positive rates inherent to classical empirical scoring functions, this module utilizes the deep-learning-based **GNINA** molecular docking engine. 
* **Methodology:** Convolutional Neural Networks (CNNs) are deployed to evaluate structural binding poses, generating empirical docking scores alongside deep-learning affinity predictions (`cnn_score` and `cnn_affinity`).
* **Key Tasks:** Automated structure optimization via OpenBabel and high-throughput ranking of the top lead candidates within the VP39 binding pocket.

### 2. Network Pharmacology & Topology Analysis (`/systems_pharmacology`)
This module maps the macroscale polypharmacological interactome of the prioritized leads to evaluate host-directed mechanism of action and signaling modulation.
* **Methodology:** Functional protein-protein interaction (PPI) networks are dynamically retrieved using the **STRING database API** and reconstructed inside **Cytoscape**. 
* **Key Tasks:** Topological screening using the **cytoHubba** plugin to compute network parameters (betweenness centrality, degree, and bottleneck metrics), isolating vital biological hubs and therapeutic target clusters.

---

## 💻 Repository Directory Structure

```text
├── README.md                           # Master documentation
├── requirements.txt                    # Python environment dependencies
├── structural_rescoring/
│   ├── scripts/                        # GNINA execution and parsing scripts
│   └── data/                           # Optimized protein/ligand structures (.pdbqt, .sdf)
└── systems_pharmacology/
    ├── System_Pharmacology_and_Network_Network.ipynb   # Core network analysis pipeline
    └── network_data/                   # Raw and filtered STRING/Cytoscape exports
