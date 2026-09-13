# DermaMNIST Image Classification

Comparison of a multilayer perceptron (MLP) and a convolutional neural network
(CNN) for multiclass classification of dermatoscopic images from DermaMNIST.

This repository is a sanitized portfolio edition of an academic team project
developed for the Advanced Machine Learning course at the University of
Coimbra. The dataset, trained weights, personal contact information, and the
original report are not distributed here.

## Project overview

DermaMNIST contains small RGB images of skin lesions divided into seven
diagnostic categories. The main technical challenge is the strong class
imbalance: the most common class contains substantially more samples than the
minority classes.

The project compares two approaches:

- A configurable MLP trained on flattened image pixels.
- A CNN with convolutional blocks, batch normalization, max pooling, dropout,
  and adaptive average pooling.

Both notebooks include weighted sampling, normalization, training utilities,
confusion matrices, and class-level evaluation metrics.

## Reported academic results

The original academic report recorded the following aggregate results:

| Model | Accuracy | Weighted F1 | Macro F1 |
| --- | ---: | ---: | ---: |
| Best reported MLP | 50.87% | 0.5593 | Not reported |
| Reported CNN | 78.00% | Approximately 0.76 | Approximately 0.57 |

These values are historical results from the original project report. They
have not been regenerated from this sanitized repository and should not be
treated as a new benchmark run.

## Methodology correction in this edition

The original notebooks used the test split during training and configuration
selection. That can produce optimistic estimates of generalization.

The portfolio copies have been corrected to:

1. Train models on the official DermaMNIST training split.
2. Use the official validation split for early stopping and model selection.
3. Reserve the test split for final evaluation only.

Stored notebook outputs and execution counters were removed. This keeps the
repository small, avoids redistributing dataset-derived images, and makes it
clear which results still need to be reproduced.

## Repository structure

```text
.
|-- notebooks/
|   |-- cnn_dermamnist.ipynb
|   `-- mlp_dermamnist.ipynb
|-- .gitignore
|-- NOTICE.md
|-- README.md
`-- requirements.txt
```

## Setup

Create an isolated Python environment and install the dependencies:

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
jupyter lab
```

Open either notebook and run its cells in order. The `medmnist` package can
download DermaMNIST when the data-loading cell runs. Training the CNN is much
faster with a CUDA-capable GPU, but the notebook selects CPU automatically when
CUDA is unavailable.

## Evaluation

The notebooks report:

- Accuracy.
- Weighted F1 score.
- Precision and recall by class.
- Confusion matrix.
- Training and validation curves.

The CNN experiment compares Adam, RMSprop, SGD, and AdamW with multiple loss
functions. Configuration selection is based on validation F1, followed by one
evaluation on the held-out test split.

## Limitations

- DermaMNIST is strongly imbalanced, particularly for minority lesion classes.
- The original results show a generalization gap between training and test
  performance.
- The MLP does not preserve spatial relationships between pixels.
- Results depend on random initialization, hardware, package versions, and
  training duration.
- This is an educational classification experiment, not a clinical diagnostic
  system.

## Data and privacy

No dataset files, patient information, credentials, local paths, trained
weights, or personal email addresses are included. Users are responsible for
reviewing the DermaMNIST and MedMNIST terms before downloading or using the
dataset.

## Team and attribution

Academic team project by Gabriel Pinto and Joao Antunes.

The public repository is presented for educational and portfolio purposes. It
does not claim that every component was produced individually by the repository
owner. See [NOTICE.md](NOTICE.md) for the publication and licensing status.

