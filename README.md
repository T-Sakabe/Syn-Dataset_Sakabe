# Syn-Datasets (Syn-MNIST, Syn-Fashion-MNIST, Syn-FER-2013)

## Overview
“Syn-Datasets” provide synthetic image-classification datasets generated via Item Response Theory (IRT).  
They are designed as drop-in replacements/enhancements for the original datasets:
- **Syn-MNIST**: based on [MNIST](http://yann.lecun.com/exdb/mnist/) (images shape: 70000×784, labels: 70000×1)  
- **Syn-Fashion-MNIST**: based on [Fashion-MNIST] (images shape: 70000×784, labels: 70000×1)  
- **Syn-FER-2013**: based on [FER-2013] (images shape: 35882×2304, labels: 35882×1)  

All classes follow the original dataset’s class assignments.

## Why we created these datasets
- Original datasets (MNIST, Fashion-MNIST, FER-2013) are widely used benchmarks—but have limitations when evaluating model difficulty, robustness, or comparative algorithm performance under controlled difficulty settings.  
- By leveraging IRT, each image (item) is associated with difficulty/discrimination parameters, and each synthetic “learner” (model) ability parameter θ is simulated, enabling more nuanced performance analyses.  
- These Syn-Datasets enable researchers and educators to:  
  * explore model performance across item-difficulty spectra  
  * study algorithm robustness with controlled item parameters  
  * use for competitions/education where item-response modelling is relevant.

## Get the Data
Each dataset is available as CSV files:
| Dataset            | Images file                        | Labels file                        |
|--------------------|-----------------------------------|------------------------------------|
| Syn-MNIST          | `Syn-MNIST_imgs.csv`              | `Syn-MNIST_labels.csv`             |
| Syn-Fashion-MNIST  | `Syn-Fashion-MNIST_imgs.csv`      | `Syn-Fashion-MNIST_labels.csv`     |
| Syn-FER-2013       | `Syn-FER-2013_imgs.csv`           | `Syn-FER-2013_labels.csv`          |

Example download using GitHub repository or direct link (if provided).  
MD5 checksums and detailed links may be given here when available.

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
imgs = pd.read_csv("Syn-MNIST_imgs.csv", header=None).values
labels = pd.read_csv("Syn-MNIST_labels.csv", header=None).values

# Display a sample image
index = 0
image = imgs[index].reshape(28, 28)
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



# 🧠 Syn-Datasets (Syn-MNIST, Syn-Fashion-MNIST, Syn-FER-2013)

## Overview
**Syn-Datasets** provide *synthetic image-classification datasets* generated using **Item Response Theory (IRT)**.  
They are designed as drop-in replacements or enhancements for the original benchmark datasets:

| Dataset | Original Source | Image Shape | Samples |
|----------|------------------|--------------|-----------|
| **Syn-MNIST** | [MNIST](http://yann.lecun.com/exdb/mnist/) | 28×28 (flattened to 784) | 70,000 |
| **Syn-Fashion-MNIST** | [Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist) | 28×28 (flattened to 784) | 70,000 |
| **Syn-FER-2013** | [FER-2013](https://www.kaggle.com/datasets/deadskull7/fer2013) | 48×48 (flattened to 2304) | 35,882 |

Each dataset consists of two CSV files:
- `*_imgs.csv` — pixel intensity values (0–255)
- `*_labels.csv` — corresponding class labels (integers)

All classes follow the same mappings as the original datasets.

---

## Why we created these datasets
The original benchmark datasets are widely used for model evaluation, but they do not capture differences in *item difficulty* or *model ability*.  
Using **IRT (Item Response Theory)**, we associate each synthetic item (image) with difficulty and discrimination parameters, and simulate “learner” (model) ability parameters (θ).

These datasets enable researchers and educators to:

- Analyze model performance across varying item difficulties  
- Evaluate robustness under controlled item-response settings  
- Use in competitions or educational experiments involving IRT

---

## 📦 Get the Data

Each dataset is provided as a ZIP archive containing two CSV files.

| Dataset | Download | Contents |
|----------|-----------|-----------|
| **Syn-MNIST** | [data/Syn-MNIST.zip](./data/Syn-MNIST.zip) | `Syn-MNIST_imgs.csv`, `Syn-MNIST_labels.csv` |
| **Syn-Fashion-MNIST** | [data/Syn-Fashion-MNIST.zip](./data/Syn-Fashion-MNIST.zip) | `Syn-Fashion-MNIST_imgs.csv`, `Syn-Fashion-MNIST_labels.csv` |
| **Syn-FER-2013** | [data/Syn-FER-2013.zip](./data/Syn-FER-2013.zip) | `Syn-FER-2013_imgs.csv`, `Syn-FER-2013_labels.csv` |

*(You can right-click the links above → “Save link as…” to download)*

---

## 🧩 Usage Example (Python)

```python
import pandas as pd
import matplotlib.pyplot as plt
import zipfile

# Load Syn-MNIST directly from the ZIP archive
with zipfile.ZipFile("data/Syn-MNIST.zip") as z:
    with z.open("Syn-MNIST_imgs.csv") as f1, z.open("Syn-MNIST_labels.csv") as f2:
        imgs = pd.read_csv(f1, header=None).values
        labels = pd.read_csv(f2, header=None).values

# Display a sample image
index = 0
image = imgs[index].reshape(28, 28)
label = labels[index, 0]

plt.imshow(image, cmap="gray", vmin=0, vmax=255)
plt.title(f"Label: {label}")
plt.show()
