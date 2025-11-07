# Syn-Datasets (Syn-MNIST, Syn-Fashion-MNIST, Syn-FER-2013)

## Overview
“Syn-Datasets” provide synthetic image-classification datasets generated via Item Response Theory (IRT).  
They are designed as drop-in replacements/enhancements for the original datasets:
- **Syn-MNIST**: based on [MNIST](http://yann.lecun.com/exdb/mnist/) (images shape: 70000×784, labels: 70000×1)  
- **Syn-Fashion-MNIST**: based on [Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist) (images shape: 70000×784, labels: 70000×1)  
- **Syn-FER-2013**: based on [FER-2013](https://www.kaggle.com/datasets/msambare/fer2013) (images shape: 35882×2304, labels: 35882×1)  

All classes follow the original dataset’s class assignments.

## Why we created these datasets
- Original datasets (MNIST, Fashion-MNIST, FER-2013) are widely used benchmarks—but have limitations when evaluating model difficulty, robustness, or comparative algorithm performance under controlled difficulty settings.  
- By leveraging IRT, each image (item) is associated with difficulty/discrimination parameters, and each synthetic “learner” (model) ability parameter θ is simulated, enabling more nuanced performance analyses.  
- These Syn-Datasets enable researchers and educators to:  
  * explore model performance across item-difficulty spectra  
  * study algorithm robustness with controlled item parameters  
  * use for competitions/education where item-response modelling is relevant.

## Get the Data
Each dataset is provided as a ZIP archive containing two CSV files.

| Dataset | Download | Contents |
|----------|-----------|-----------|
| **Syn-MNIST** | [data/Syn-MNIST.zip](./data/Syn-MNIST.zip) | `Syn-MNIST_images.csv`, `Syn-MNIST_labels.csv` |
| **Syn-Fashion-MNIST** | [data/Syn-Fashion-MNIST.zip](./data/Syn-Fashion-MNIST.zip) | `Syn-Fashion-MNIST_images.csv`, `Syn-Fashion-MNIST_labels.csv` |
| **Syn-FER-2013** | [data/Syn-FER-2013.zip](./data/Syn-FER-2013.zip) | `Syn-FER-2013_images.csv`, `Syn-FER-2013_labels.csv` |

## Labels
The class labels follow the original dataset mapping:

### Syn-MNIST / Syn-Fashion-MNIST (0-9):
(*Insert descriptive class names for Fashion-MNIST if desired.*)

### Syn-FER-2013:
(*Example mapping — adjust if your research uses a different mapping.*)

## Usage Example
Here is how to load and display images in Python:

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load dataset
images = pd.read_csv("Syn-MNIST_images.csv", header=None).values
labels = pd.read_csv("Syn-MNIST_labels.csv", header=None).values

# Display a sample image
index = 0
image = images[index].reshape(28, 28)
label = labels[index, 0]

plt.imshow(image, cmap="gray", vmin=0, vmax=255)
plt.title(f"Label: {label}")
plt.show()
```

## Citation
If you use these datasets in your publication, please cite:
```latex
@article{Sakabe:IEEE:2025,
  title     = {Dataset Construction Using Item Response Theory for Educational Machine Learning Competitions},
  author    = {Sakabe, Takeaki and Sakurai, Yuko and Tsutsumi, Emiko and Oyama, Satoshi},
  journal   = {IEEE Access},
  year      = {2025},
  publisher = {IEEE}
}
```
