# MRNet Knee MRI Classification (CECS 553)

Notebook-only workflow for the [Stanford MRNet](https://aimi.stanford.edu/datasets/mrnet-knee-mris) knee MRI dataset: three binary tasks (abnormal, ACL tear, meniscal tear) using a ResNet18 backbone and multi-plane fusion.

## Setup

1. **Data**  
   Download MRNet (registration required) and place it so the project sees:
   - `data/mrnetkneemris/train/` and `data/mrnetkneemris/valid/` (each with `axial/`, `coronal/`, `sagittal/` containing `.npy` files)
   - `data/mrnetkneemris/train-abnormal.csv`, `train-acl.csv`, `train-meniscus.csv`, and `valid-*.csv`

   If your data lives elsewhere, set:
   ```bash
   set MRNET_DATA_DIR=C:\path\to\MRNet-v1.0
   ```

2. **Environment**
   ```bash
   python -m venv .venv
   .venv\Scripts\activate
   pip install -r requirements.txt
   ```

## Run (single notebook)

Open and run:

- `notebooks/mrnet_training.ipynb`

Run cells top-to-bottom:

1. Configuration (`DATA_ROOT`, `TASK`, hyperparameters)
2. Imports
3. Data loading + dataset
4. Model definition
5. Train/validate loop for one task
6. Optional cell to train all three tasks and report average AUC

Best checkpoint per task is saved to:

- `checkpoints/mrnet_{task}_best.pt`

Metric: validation AUC per task; the competition metric is the average of the three task AUCs.

## Project Layout

- `notebooks/mrnet_training.ipynb` - complete end-to-end pipeline
- `requirements.txt` - Python dependencies
- `README.md` - setup and usage

## Citation

When using this dataset, cite:  
**MRNet: Knee MRI's**, Stanford AIMI, DOI: [10.71718/rcbp-8c35](https://doi.org/10.71718/rcbp-8c35).
