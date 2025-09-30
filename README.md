# Dimensionality Reduction — Comparative Study (Breast Cancer & Fashion‑MNIST)

> Reproducible notebook comparing linear & non‑linear dimensionality‑reduction (DR) techniques on two well‑known datasets, with short report and literature reference.

## TL;DR
- **Datasets:** Breast Cancer (tabular), Fashion‑MNIST (images).
- **Methods compared:** PCA, KernelPCA, ICA, t‑SNE, Isomap, LLE, MDS, TruncatedSVD.
- **Key takeaway:** Linear DR (e.g., **PCA/SVD**) performs strongly on the linearly separable **Breast Cancer** data; **t‑SNE/Isomap** yield better class separation on **Fashion‑MNIST** but at higher compute cost.
- **Status:** _Ongoing — actively adding features and improvements._

## Repository structure
```
.
├── DimRE.ipynb              # Main Jupyter notebook: DR experiments & plots
├── hy573Panagiotis.pdf      # Short project report (results & discussion)
├── paper573.pdf             # Reference survey paper (background on DR methods)
└── .gitattributes
```

## Environment
- Python 3.9+
- Packages: `numpy`, `pandas`, `scikit-learn`, `matplotlib`, `seaborn`, `jupyter`
- Optional: `umap-learn` (for UMAP), `tqdm` (progress bars)

```bash
pip install numpy pandas scikit-learn matplotlib seaborn jupyter umap-learn tqdm
```

## Data
- **Breast Cancer**: from `sklearn.datasets.load_breast_cancer()`
- **Fashion‑MNIST**: can be fetched via `tensorflow`/`keras` or pre‑converted `.npz` (see notebook cells).

> The notebook handles loading & standard preprocessing (scaling where applicable).

## How to run
1. Launch Jupyter:
   ```bash
   jupyter notebook
   ```
2. Open `DimRE.ipynb` and run all cells.
3. (Optional) Adjust parameters (e.g., `n_components`, `perplexity`, neighbors) in the configuration cells to reproduce variations.

## Methods
- **Linear:** PCA, TruncatedSVD, MDS, ICA
- **Non‑linear / Manifold:** t‑SNE, Isomap, LLE
- **(Optional)** UMAP for comparison

The notebook includes 2D/3D embeddings, trustworthiness where relevant, and simple downstream classification (LogReg / SVM / RF) on the low‑dimensional features.

## Results (high‑level)
- **Breast Cancer (tabular):** Classical linear DR methods (PCA/SVD/MDS) paired with standard classifiers achieve high accuracy (~0.96–0.98).  
- **Fashion‑MNIST (images):** Non‑linear DR (notably **t‑SNE**) produces clearer class separation and higher downstream accuracy (up to ~0.82 with RF in our runs), at a noticeably higher runtime vs. PCA/SVD.

> See `hy573Panagiotis.pdf` for tables, timing notes, and per‑method commentary.

## Notes & limitations
- t‑SNE is **computationally heavy**; consider subsampling or using UMAP for faster exploration.
- Always compare against a **no‑DR baseline** (scaled features → classifier) to verify that DR helps your task.
- For fair evaluation, apply scaling/transform **inside** a `Pipeline` and report cross‑validated metrics.

## Screenshots / Figures
Embeddings and comparative plots are generated in the notebook and can be exported as PNGs from the cells (e.g., `plt.savefig(...)`).

## Citation
If you build on this work, please cite the accompanying short report and the survey used for background:

- Project report: *Dimensionality Reduction Techniques: A Comparative Study* (`hy573Panagiotis.pdf`).  
- Survey: *Overview and comparative study of dimensionality reduction techniques for high dimensional data*, Information Fusion 59 (2020) 44–58 (`paper573.pdf`).

## License
MIT (or your preferred license). Update the repository license file accordingly.
