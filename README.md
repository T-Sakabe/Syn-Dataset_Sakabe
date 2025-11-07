# Syn-Datasets (Syn-MNIST, Syn-Fashion-MNIST, Syn-FER-2013)

## Overview
**Syn-Datasets** are image datasets automatically generated using a framework proposed in *“Dataset Construction Using Item Response Theory for Educational Machine Learning Competitions.”* This framework combines **Item Response Theory (IRT)** with a **Conditional Variational Autoencoder (CVAE)** to create datasets that can more accurately evaluate the performance differences among machine learning (ML) models.

<p align="center">
  <img src="framework_overview.png" alt="Overview of the proposed IRT+CVAE framework" width="600"><br>
  <em>Figure 1. Overview of the proposed dataset generation framework (IRT + CVAE)</em>
</p>

Each Syn-Dataset is an enhanced version of an existing benchmark dataset, designed to maintain the original structure:

- **Syn-MNIST**: based on [MNIST](http://yann.lecun.com/exdb/mnist/) (70,000 samples, 28×28 grayscale)  
- **Syn-Fashion-MNIST**: based on [Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist) (70,000 samples, 28×28 grayscale)  
- **Syn-FER-2013**: based on [FER-2013](https://www.kaggle.com/datasets/msambare/fer2013) (35,887 samples, 48×48 grayscale)


---

## Why we created Syn-Datasets
Common benchmark datasets such as MNIST, Fashion-MNIST, and FER-2013 are widely used in educational ML competitions. However, these datasets **do not consider participants’ ability distributions or task difficulty**, making it difficult to accurately distinguish performance differences among models.

For example, many standard ML models achieve over 90% accuracy on MNIST with default settings, which limits their effectiveness in assessing participants’ skills or model improvements.

To address this issue, our proposed framework automatically generates datasets with **specified item difficulty and discrimination**, allowing fairer and more effective evaluation of model performance.

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
