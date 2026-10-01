# Country Atlas

An interactive Streamlit experience for exploring country development indicators and the saved K-Means country groups.

## Run locally

From PowerShell in this folder:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
streamlit run app.py
```

Open the local URL printed by Streamlit, usually `http://localhost:8501`.

## Data and model

The app reads `Country-data.csv` from this folder. If that file is unavailable, it downloads the public Kaggle dataset `rohan0301/unsupervised-learning-on-country-data` through `kagglehub`.

Cluster assignments are generated with the included `final_scaler.joblib` and `final_kmeans_model.joblib`. The saved model uses two clusters and expects `log1p`-transformed `gdpp` and `income` values before scaling. The app does not provide a file-upload workflow or retrain the model.

## Explore

- **Field:** Rotate and zoom the Three.js country feature-space, change its axes, and filter the view by model cluster.
- **Analysis:** Explore feature distributions, correlations, 2D/3D PCA projections, silhouette score, and cluster profiles.
- **Country:** Inspect a country’s indicators relative to the current cohort median.
- **Records:** Search, sort, paginate, choose visible fields, and export the filtered records as CSV.

The 3D renderer and fonts load from public CDNs, so an internet connection is needed for those visual assets. The local CSV and model files are used directly when present.

## Project files

- `app.py` — Streamlit app, data loading, model predictions, and analysis views.
- `scene.py` — Embedded Three.js country visualization.
- `Country-data.csv` — Country development indicators.
- `final_scaler.joblib` — Saved feature scaler.
- `final_kmeans_model.joblib` — Saved K-Means model.
- `requirements.txt` — Python dependencies.
