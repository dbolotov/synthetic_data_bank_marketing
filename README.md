# Synthetic Data Generation — Bank Marketing Dataset

View the rendered notebook [here (using nbviewer)]

Synthetic data generation workflow in a Jupyter notebook, using [SDV](https://sdv.dev/) on the [UCI Bank Marketing dataset](https://archive.ics.uci.edu/dataset/222/bank+marketing).

Generates synthetic tabular data that preserves the statistical properties of the original dataset and runs validation checks.

## Model

`CopulaGANSynthesizer` — hybrid approach combining Gaussian copula marginal fitting with CTGAN-based joint distribution learning. Four synthesizers were evaluated (GaussianCopula, CTGAN, TVAE, CopulaGAN); see the notebook for details.

## Results

| Metric | Score |
|--------|-------|
| Column Shapes | 0.88 |
| Column Pair Trends (numeric) | 0.80 |
| Column Pair Trends (categorical) | 0.67 |
| Data Validity | 1.00 |
| Data Structure | 1.00 |
| New Row Score | 1.00 |
| Nearest-Neighbor Privacy | 0.35 |

## Setup
```bash
pip install -r requirements.txt
```

Then open `synthetic_data_gen_bank.ipynb` in Jupyter.

## Data

UCI Bank Marketing dataset (10% subset, 4,119 rows). Original source: [Moro et al., 2014](https://archive.ics.uci.edu/dataset/222/bank+marketing). Licensed under CC BY 4.0.

## Outputs

Running the notebook saves the following to `outputs/`:
- `synthetic_data.csv` — generated synthetic dataset
- `copulagan_synthesizer.pkl` — fitted synthesizer
- `metadata.json` — SDV table metadata