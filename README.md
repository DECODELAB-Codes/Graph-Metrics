# Graph-Metrics-Quantifications

This repository contains a comprehensive collection of Python-based graph metric quantifications applied to functional connectivity networks derived from single-unit neuronal data. These metrics are computed on a per-animal basis and capture distinct aspects of network structure during cognitive tasks such as fear conditioning and extinction.

All analyses are implemented in a single Jupyter notebook and cover the following metrics:

---

## 📊 Metrics Implemented

### 1. **PageRank**
- **Type**: Directed graph
- **Purpose**: Identifies influential neurons based on incoming connections from other high-scoring neurons.
- **Usage Notes**: 
  - Requires one animal per file.
  - Based on NetworkX's `pagerank()` which supports edge weights.
  - Edge weights represent connection strength.

---

### 2. **Weighted Clustering Coefficient**
- **Type**: Undirected graph
- **Purpose**: Measures how tightly each neuron’s neighbors are interconnected.
- **Usage Notes**:
  - Processes multiple animals from a single file using the `'Animal'` column.
  - Uses NetworkX's `clustering()` with weighted edges.

---

### 3. **Weighted Degree Centrality**
- **Type**: Undirected graph
- **Purpose**: Quantifies the total strength of connections per neuron.
- **Usage Notes**:
  - Computes both raw and normalized values.
  - Supports multi-animal files.

---

### 4. **HITS (Hubs and Authorities)**
- **Type**: Directed graph
- **Purpose**: Identifies hub neurons (connect to many authorities) and authority neurons (receive many hub connections).
- **Usage Notes**:
  - Only directionality is used; edge weights are not considered.
  - Uses NetworkX's `hits()` with internal iterative computation.
  - One animal per file.

---

### 5. **Leiden Community Detection**
- **Type**: Undirected graph
- **Purpose**: Detects modular structure by grouping neurons into functionally connected communities.
- **Usage Notes**:
  - Uses the Leiden algorithm via `leidenalg` and `igraph`.
  - Visualizes community structure and edge strengths.
  - One animal per file.
  - Edge weights interpreted as connection strength (higher = more connected).

---

### 6. **Eigenvector Centrality**
- **Type**: Undirected graph
- **Purpose**: Measures a neuron's influence based on the centrality of its neighbors.
- **Usage Notes**:
  - Processes multi-animal files using the `'Animal'` column.
  - Uses NetworkX's `eigenvector_centrality()` with convergence handling.

---

### 7. **Global and Local Efficiency**
- **Type**: Undirected graph
- **Purpose**: 
  - **Global efficiency** reflects network-wide integration.
  - **Local efficiency** reflects neighborhood resilience and clustering.
- **Usage Notes**:
  - Weights represent **normalized functional connectivity** in [0, 1].
  - Distances are computed as `1 - weight` to reflect stronger connections as shorter paths.
  - Operates on the largest connected component of each graph.

---

## 📁 File Structure
graph-metrics/
│
├── Quantifications for graph metrics 5-19-25.ipynb # Main notebook with all graph metric code
├── README.md # Repository documentation
├── requirements.txt # Required Python packages
└── .gitignore # Files/folders to exclude from Git tracking


---

## 🚀 How to Use This Repository

1. **Clone the repository** or download it as a ZIP:
   ```bash
   git clone https://github.com/DECODELAB-Codes/Graph-Metrics.git
   cd Graph-Metrics
2. **Install dependencies (Python 3.8+ recommended):**
   pip install -r requirements.txt
3. **Open the notebook:**
   jupyter notebook
4. **Run each code block to compute the metrics on your data.**
