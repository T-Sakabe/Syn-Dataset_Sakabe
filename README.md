# Syn-Datasets (Syn-MNIST, Syn-Fashion-MNIST, Syn-FER-2013)

## Overview
**Syn-Datasets** are synthetic image datasets automatically generated using a framework proposed in *“Dataset Construction Using Item Response Theory for Educational Machine Learning Competitions.”* This framework integrates **Item Response Theory (IRT)** and a **Conditional Variational Autoencoder (CVAE)** to create datasets that can more accurately evaluate the performance differences among machine learning (ML) models.

Each Syn-Dataset is an enhanced version of an existing benchmark dataset, designed to maintain the original structure:

- **Syn-MNIST**: based on [MNIST](http://yann.lecun.com/exdb/mnist/) (70,000 samples, 28×28 grayscale)  
- **Syn-Fashion-MNIST**: based on [Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist) (70,000 samples, 28×28 grayscale)  
- **Syn-FER-2013**: based on [FER-2013](https://www.kaggle.com/datasets/msambare/fer2013) (35,882 samples, 48×48 grayscale)


---

## Why we created Syn-Datasets
Common benchmark datasets such as MNIST, Fashion-MNIST, and FER-2013 are widely used in educational ML competitions. However, these datasets **do not consider participants’ ability distributions or task difficulty**, making it difficult to accurately distinguish performance differences among models.

For example, many standard ML models achieve over 90% accuracy on MNIST with default settings, which limits their effectiveness in assessing participants’ skills or model improvements.

To address this issue, we propose a **dataset generation framework** that combines IRT and CVAE, as illustrated below.

<p align="center">
  <img src="framework_overview.png" alt="Overview of the proposed IRT+CVAE framework" width="600"><br>
  <em>Figure 1. Overview of the proposed dataset generation framework (IRT + CVAE)</em>
</p>

Through this framework, datasets with controllable **item difficulty** and **discrimination** can be generated automatically, enabling more effective and fair performance evaluation.

Below is an example of generated Syn-MNIST images with specified difficulty and discrimination parameters.

<p align="center">
  <img src="syn_mnist_examples.png" alt="Examples of Syn-MNIST generated images by difficulty and discrimination" width="600"><br>
  <em>Figure 2. Examples of generated Syn-MNIST images (controlled by difficulty and discrimination)</em>
</p>

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
