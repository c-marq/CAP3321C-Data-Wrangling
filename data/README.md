# 📁 Datasets

This folder contains datasets used across multiple chapters. Chapter-specific datasets are located in the `data/` subfolder within each chapter's demo, exercise, or lab folder.

---

## Shared Datasets

| Dataset | Description | Used In |
|---------|-------------|---------|
| *Coming soon* | — | — |

---

## Data Sources

All datasets used in this course are either:
- Publicly available datasets
- Synthetic data created for educational purposes
- Licensed for educational use

---

## Working with Data in Colab

When working in Google Colab, you'll typically load data using a URL. For example:

```python
import pandas as pd

# Load from GitHub raw URL
url = "https://raw.githubusercontent.com/[your-repo]/main/data/filename.csv"
df = pd.read_csv(url)
```

Each notebook includes the correct URL for its datasets.

---

## Data Dictionary

Detailed descriptions of each dataset's columns and values are provided in the relevant chapter materials.

---

[← Back to Main README](../README.md)
