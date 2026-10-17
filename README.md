# Maize Leaf Disease Classification with a Custom Vision Transformer

This repository contains the Jupyter/Google Colab notebooks used to train and
evaluate a custom Vision Transformer (ViT) for maize leaf disease
classification across maize image datasets from Tanzania, Uganda, and
Namibia.

The notebooks include:

- image discovery and class-folder validation;
- deterministic train/validation/test splitting;
- image preprocessing and augmentation;
- class-weighted Custom ViT training;
- accuracy, precision, recall, F1-score, classification reports, and confusion
  matrices; and
- qualitative predictions with attention-map or Grad-CAM visualizations.

## Repository structure

```text
.
├── notebooks/
│   ├── custom_vit_makerere.ipynb
│   ├── custom_vit_nm_aist.ipynb
│   └── custom_vit_nust.ipynb
├── .gitignore
├── README.md
└── requirements.txt
```

Datasets, trained models, plots, and other generated artifacts are intentionally
not included in this repository.

## Dataset sources

Download the datasets from their original repositories. Please review and
follow each dataset's terms of use and citation requirements.

| Notebook | Dataset | Source |
| --- | --- | --- |
| `custom_vit_makerere.ipynb` | Makerere University Maize Image Dataset (Uganda) | [Harvard Dataverse, DOI 10.7910/DVN/LPGHKK](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/LPGHKK) |
| `custom_vit_nm_aist.ipynb` | Nelson Mandela African Institution of Science and Technology Maize Dataset (Tanzania) | [Harvard Dataverse, DOI 10.7910/DVN/GDON8Q](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/GDON8Q) |
| `custom_vit_nust.ipynb` | Namibia University of Science and Technology Maize Dataset (Namibia) | [Harvard Dataverse, DOI 10.7910/DVN/6R78HR](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/6R78HR) |

Do not commit downloaded image archives or extracted datasets. The source
datasets remain the property of their respective providers.

## Quick start with Google Colab

1. Open the relevant notebook from `notebooks/` in Google Colab.
2. Download the corresponding dataset archive from the source listed above.
3. Upload the archive to the root of your Google Drive (`My Drive`).
4. Use the archive name expected by the notebook:

   | Notebook | Archive expected in Google Drive |
   | --- | --- |
   | Makerere | `Dataset2.zip` |
   | NM-AIST | `Dataset3.zip` |
   | NUST | `Dataset.zip` |

5. Run the notebook from top to bottom. The first cells mount Google Drive,
   install/import dependencies, extract the archive, and locate the dataset
   directory.

The expected class folders are documented in the first markdown cell of each
notebook. The NUST notebook expects five classes; the Makerere and NM-AIST
notebooks expect three classes each.

## Run locally

Create a virtual environment, install the dependencies, and launch Jupyter:

```bash
python -m venv .venv

# macOS/Linux
source .venv/bin/activate

# Windows PowerShell
.venv\Scripts\Activate.ps1

python -m pip install --upgrade pip
python -m pip install -r requirements.txt
jupyter lab
```

The notebooks currently use Google Colab paths and Google Drive mounting.
For local execution, replace the Drive mount and archive paths in the
data-loading cells with paths to your local dataset files.

## Reproducibility notes

- Image size: `224 × 224`
- Batch size: `32`
- Random seed: `42`
- Training epochs: `70`
- The exact class names and folder conventions are dataset-specific and are
  defined in each notebook.
- Training requires substantial memory and is best run with a GPU.

Each notebook saves a Keras model in its working directory when training
finishes. These model files are ignored by Git; copy them to a separate
artifact store if they need to be preserved.

## Citation

If you use this code or the associated experiments, cite the manuscript
associated with this repository and cite the original dataset records listed
above.
