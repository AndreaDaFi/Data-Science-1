# Data Science Final Project
| Name                   | ID      |
|------------------------|---------|
| William Ngo            | 2170924 |
| Salvador Gonzales      | 1909940 |
| Andrea Davila Figueroa | 2268548 |

## Running Locally (no AWS required)

All notebooks have been updated so that S3 download/upload calls are commented out.

### Prerequisites

1. **Install dependencies**
   ```
   pip install -r requirements.txt
   ```

2. **Get the dataset**  
   You need `cleaned/papers.parquet` in the root of the repo. Options:
   - Download it once manually from S3 if you have credentials, or
   - Run `preprocess.ipynb` locally (requires the 4 raw JSON files in `raw/`)

   This will produce `cleaned/papers.parquet` and skip all S3 uploads.

---

### Running individual notebooks

Open each notebook in Jupyter and run all cells.
```

`citation_network.ipynb` requires `outputs/data/paper_clusters.parquet` — run `clustering.ipynb` first.

Output figures are saved to `outputs/figures/<task>/` and data files to `outputs/data/`.

Run these files in order:
```
preprocess.ipynb | outputs/
eda.ipynb | outputs/
clustering.ipynb | outputs/
temporal_classification.ipynb | outputs/
citation_network.ipynb | outputs/
```
---