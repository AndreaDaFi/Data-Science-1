# Data Science Final Project
| Name                   | ID      |
|------------------------|---------|
| William Ngo            | 2170924 |
| Salvador Gonzales      | 1909940 |
| Andrea Davila Figueroa | 2268548 |

## Running Locally (no AWS required)

All scripts have been updated so that S3 download/upload calls are commented out. 

### Prerequisites

1. **Install dependencies**
   ```
   pip install -r requirements.txt
   ```

2. **Get the dataset**  
   You need `cleaned/papers.parquet` in the root of the repo. Options:
   - Download it once manually from S3 if you have credentials, or
   - Run `preprocess.py` locally (requires the 4 raw JSON files in `raw/`)

   To run preprocessing locally, place the four json files in a `raw/` folder, then:
   ```
   python src/preprocess.py
   ```
   This will produce `cleaned/papers.parquet` and skip all S3 uploads.

---

### Running individual scripts

Run each script from the **root of the repo**:

```
python src/eda.py
python src/clustering.py
python src/temporal_classification.py
python src/citation_network.py
```

`citation_network.py` requires `outputs/data/paper_clusters.parquet` — run `clustering.py` first.

Output figures are saved to `outputs/figures/<task>/` and data files to `outputs/data/`.

---

### Running all scripts in order via runner.py

`FilesToRun.txt` controls which scripts `runner.py` executes. Add entries in the order you want them to run:

```
preprocess.py | outputs/
eda.py | outputs/
clustering.py | outputs/
temporal_classification.py | outputs/
citation_network.py | outputs/
```

Then run:
```
python src/runner.py
```
---