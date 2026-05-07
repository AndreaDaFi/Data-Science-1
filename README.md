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

   To run preprocessing locally, place the four JSON files in a `raw/` folder, then open and run all cells in:
   ```
   src/preprocess.ipynb
   ```
   This will produce `cleaned/papers.parquet` and skip all S3 uploads.

---

### Running individual notebooks

Open each notebook in Jupyter and run all cells, or execute all at once from the **root of the repo** via:

```
jupyter nbconvert --to notebook --execute --inplace src/eda.ipynb src/clustering.ipynb src/temporal_classification.ipynb src/citation_network.ipynb
```

`citation_network.ipynb` requires `outputs/data/paper_clusters.parquet` — run `clustering.ipynb` first.

Output figures are saved to `outputs/figures/<task>/` and data files to `outputs/data/`.

---

### Running all notebooks in order via runner.ipynb

`FilesToRun.txt` controls which notebooks `runner.ipynb` executes. Add entries in the order you want them to run:

```
preprocess.ipynb | outputs/
eda.ipynb | outputs/
clustering.ipynb | outputs/
temporal_classification.ipynb | outputs/
citation_network.ipynb | outputs/
```

Then open and run all cells in `src/runner.ipynb`, or execute it via:
```
jupyter nbconvert --to notebook --execute src/runner.ipynb --output src/runner.ipynb
```
---