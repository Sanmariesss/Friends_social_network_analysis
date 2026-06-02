# Friends TV Show — Social Network Analysis

**Course:** Social Network Analysis — Luiss Guido Carli

**Team:** Sabina Nurseitova, Assima Amangeldina, Ziyi Dong, Ceyla Kaya

**Type:** Network Analysis | Graph Theory | Team Project

---

# Introduction

This project analyzes the social dynamics of characters from the TV show *Friends* using social network analysis techniques. The dataset consists of character interactions throughout the entire show, represented as a weighted undirected graph where nodes are characters and edges represent interactions between them.

The project covers a wide range of network analysis concepts — from basic metrics like degree and density, to advanced topics like community detection, link prediction, and influence propagation simulation.

---

# Dataset

- **Source:** Friends TV show character interactions
- **File:** `friends_episodes.txt`
- **Size:** 747 nodes (characters) × 1,610 edges (interactions)
- **Graph type:** Weighted, undirected

---

# Methods

## Tools and Environment
- **Language:** Python 3
- **Libraries:** `NetworkX`, `Matplotlib`, `community` (python-louvain)
- **Environment:** Jupyter Notebook
- **To install dependencies:** `pip install networkx matplotlib python-louvain`

## Project Structure by Week

### Week 1–3 — Graph Construction & Basic Metrics (`week1-3.ipynb`)
- Built the graph from `friends_episodes.txt`, assigning edge weights based on interaction frequency
- Visualized the full graph and a subgraph filtered by highest edge weights
- Computed key metrics:
  - **Nodes:** 747 | **Edges:** 1,610
  - **Average degree:** 4.31 (each character interacts with ~4 others on average)
  - **Density:** 0.0058 (very sparse — only 0.58% of possible interactions occurred)
- Calculated **average clustering coefficient** and **transitivity** using both built-in NetworkX functions and manual implementations
- Identified **closeness centrality** as the key local metric — Joey emerged as the most central character

### Week 5 & 7 — PageRank, K-Shell & Link Prediction (`week5_and_7.ipynb`)
- Computed **PageRank** (α = 0.15) — Joey again ranked highest, confirming his central role
- Implemented **k-shell decomposition** from scratch to identify core subgraphs (maximum k = 18; visualized k ≥ 12 and k ≥ 15)
- Performed **link prediction** using five indices: Common Neighbors (CN), Jaccard Index (JI), Adamic-Adar (AA), Preferential Attachment (PA), and Resource Allocation (RA)
- Invented a custom **Prediction Score** = CN + JI + AA + PA + RA
- Key finding: Joey and Joshua had the highest prediction score (3.572), suggesting a strong likelihood of interaction despite never being close friends in the show

### Week 6 — Community Detection (`week6.ipynb`)
Compared three community detection algorithms:

| Method | Communities | Modularity | Time |
|---|---|---|---|
| Girvan-Newman | 39 | 0.3923 | 1040.34s |
| **Louvain** | **10** | **0.4069** | **0.06s** |
| Label Propagation | 21 | 0.0495 | 0.03s |

**Louvain** was the most effective — highest modularity with the fastest runtime. Results saved in `louvain_partition.gexf`.

### Week 9 — Random Graph & Preferential Attachment (`week9.ipynb`)
- Computed full network metrics: average degree, clustering coefficient, diameter, transitivity, centrality measures
- Generated a **Preferential Attachment (PA) random graph** to model scale-free network behavior
- Compared PA graph properties against the original Friends graph to validate the model

### Week 10 — Influence Propagation Simulation (`finalweek10.ipynb`)
- Implemented a custom **Episodic Weighted Fractional Threshold Model** to simulate character activation across the network
- Main characters (Rachel, Ross, Chandler, Monica, Phoebe, Joey) were assigned manually tuned thresholds based on relationship closeness
- Simulated multiple scenarios by varying:
  - **Initial activators** (e.g. Ross & Rachel vs. Joey & Chandler)
  - **Activation threshold** (5, 10, 20)
  - **Decay rate** (0.7, 0.9, 1.0)
- Results visualized as color-coded graphs showing activated vs. inactive characters

---

# Results

- Joey was consistently identified as the most central character via closeness centrality and PageRank
- The network is sparse but has a recognizable core structure — the 6 main characters form a tightly connected hub
- Louvain community detection produced the most meaningful groupings (10 communities, modularity = 0.41)
- Link prediction revealed Joey and Joshua as the most likely unformed connection (score = 3.572)
- Influence propagation showed that higher decay values and lower thresholds dramatically increase the reach of activation across the network

---

# How to Run

1. Clone the repository
2. Install dependencies: `pip install networkx matplotlib python-louvain`
3. Place `friends_episodes.txt` in the same folder as the notebooks
4. Run notebooks in order:
   - `intro_and_conclusion.ipynb`
   - `week1-3.ipynb`
   - `week5_and_7.ipynb`
   - `week6.ipynb`
   - `week9.ipynb`
   - `finalweek10.ipynb`

---

## Repository Structure

```
├── intro_and_conclusion.ipynb   # Project introduction and conclusions
├── week1-3.ipynb                # Graph construction, basic metrics, centrality
├── week5_and_7.ipynb            # PageRank, k-shell, link prediction
├── week6.ipynb                  # Community detection comparison
├── week9.ipynb                  # Random graph & preferential attachment
├── finalweek10.ipynb            # Influence propagation simulation
├── friends_episodes.txt         # Dataset
├── louvain_partition.gexf       # Louvain community detection output
└── README.md
```
