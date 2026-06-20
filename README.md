# 🌍 Earthquake Clustering — DBSCAN Algorithm

Unsupervised machine learning project applying **DBSCAN (Density-Based Spatial Clustering of Applications with Noise)** on 782 earthquake records — automatically detecting clusters and identifying outlier seismic events.

---

## 🎯 Problem Statement

Group 782 earthquakes (2001–2023) using a density-based approach that can:
- Find clusters of **arbitrary shape**
- Automatically detect **noise/outlier** earthquakes (label = -1)
- No need to specify number of clusters in advance

- **Dataset**: 782 earthquakes (2001–2023), 19 features
- **Algorithm**: DBSCAN

---

## 🔄 ML Pipeline

### Step 1: EDA
- Missing value analysis, correlation heatmap
- Feature distributions, skewness & kurtosis
- IQR outlier detection & boxplots

### Step 2: Drop Irrelevant Features
Removed: `title`, `location`, `net`, `date_time`, `country`

### Step 3: Data Preprocessing
- Median imputation → IQR outlier capping → RobustScaler
- Mode imputation + OneHotEncoding (`alert`, `magType`, `continent`)

### Step 4: Dimensionality Reduction
- **PCA** to 2 components for visualization

### Step 5: DBSCAN Parameter Tuning

| eps | min_samples | Clusters | Noise Points | Silhouette Score |
|-----|------------|----------|--------------|-----------------|
| 2.0 | 4 | 2 | 42 | 0.179 |
| 2.5 | 3 | 1 | some | 0.212 |
| **2.7** | **5** | **1** | some | **0.290** |

### Step 6: Best Model Results (eps=2.7, min_samples=5)
- **Silhouette Score: 0.290** ← best performance
- Label **-1** = noise/outlier earthquakes (not belonging to any cluster)
- Label **0** = main dense cluster of earthquakes

### Step 7: Visualization
- Scatter plot: Magnitude vs Depth colored by cluster
- Core samples highlighted in red

---

## 📊 Key Findings

- **42 earthquakes** identified as noise/outliers with initial parameters
- DBSCAN excels at detecting **anomalous seismic events** that don't fit normal patterns
- Unlike KMeans, DBSCAN doesn't force every point into a cluster

---

## 🛠️ Tech Stack

| Category | Tools |
|----------|-------|
| Language | Python |
| Data Analysis | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn, Missingno |
| Preprocessing | Scikit-learn (SimpleImputer, RobustScaler, OneHotEncoder) |
| Dimensionality Reduction | PCA (Scikit-learn) |
| Clustering | DBSCAN (Scikit-learn) |
| Evaluation | Silhouette Score |

---

## 🚀 How to Run

```bash
pip install pandas numpy matplotlib seaborn scikit-learn missingno ydata-profiling
```

Open `DBSCAN_Clustering_earthquake_week7_sub.ipynb` in Jupyter Notebook and run all cells.

---

## 📁 Project Structure

```
earthquake-dbscan-clustering/
│
├── DBSCAN_Clustering_earthquake_week7_sub.ipynb   # Main notebook
├── earthquake_data.csv                             # Dataset
└── README.md
```

---

## 🔗 Related Projects

- [Earthquake Magnitude Regression](https://github.com/angelaadida/earthquake-magnitude-regression)
- [Earthquake KMeans Clustering](https://github.com/angelaadida/earthquake-kmeans-clustering)
- [Earthquake Hierarchical Clustering](https://github.com/angelaadida/earthquake-hierarchical-clustering)

---

## 👩‍💻 Author

**Angela** — Data Scientist | AI • ML • GenAI • RAG  
📍 Kuala Lumpur, Malaysia  
🔗 [GitHub](https://github.com/angelaadida)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
