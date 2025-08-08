# MNIST Dataset

## Overview

This DeepTrackAI repository provides a ready-to-use copy of the **MNIST** dataset, a benchmark collection of handwritten digits originally created by Yann LeCun, Corinna Cortes, and Christopher J.C. Burges. MNIST is widely used for training and evaluating machine learning and deep learning models in computer vision.

The dataset contains grayscale images of digits (0–9) with associated labels. Each image is 28×28 pixels. The dataset is split into a training set of 60,000 images and a test set of 10,000 images.

* **Dataset Size**: 70,000 images (60,000 training + 10,000 test)
* **Image Size**: 28×28 pixels
* **Color**: Grayscale
* **Labels**: 10 classes (digits 0–9)

---

## Original Source

* **Title:** The MNIST Database of Handwritten Digits
* **Authors:** [Yann LeCun](http://yann.lecun.com/), [Corinna Cortes](https://cseweb.ucsd.edu/~cortes/), [Christopher J.C. Burges](https://www.microsoft.com/en-us/research/people/cburges/)
* **Source:** [Official MNIST Website](http://yann.lecun.com/exdb/mnist/)
* **License:** [Creative Commons Attribution-Share Alike 3.0](https://creativecommons.org/licenses/by-sa/3.0/)

If you use this dataset in your research, you must follow the licensing requirements and properly attribute the original authors.

---

## Dataset Structure

\`\`\`bash
/MNIST\_dataset
├── train/          # Training images by class
│   ├── 0/
│   ├── 1/
│   └── ...
└── test/           # Test images by class
├── 0/
├── 1/
└── ...
\`\`\`

Each subfolder contains PNG files corresponding to the digit class.
Optional CSV manifests may include file paths, labels, and split information.

---

## How to Access the Data

### Clone the Repository

\`\`\`bash
git clone -b mnist github.com/DeepTrackAI/MNIST\_dataset
cd MNIST\_dataset
\`\`\`

### Download Programmatically in Python

\`\`\`python
import requests
from io import BytesIO
from zipfile import ZipFile

DATASET\_URL = '[https://github.com/DeepTrackAI/MNIST\_dataset/raw/main/mnist.zip](https://github.com/DeepTrackAI/MNIST_dataset/raw/main/mnist.zip)'

response = requests.get(DATASET\_URL)
with ZipFile(BytesIO(response.content)) as z:
z.extractall()

# Now load with your preferred framework (PyTorch, TensorFlow, deeplay, etc.)

\`\`\`

---

## Usage Examples

### PyTorch

\`\`\`python
from torchvision import datasets, transforms
from torch.utils.data import DataLoader

transform = transforms.Compose(\[
transforms.ToTensor(),
transforms.Normalize((0.1307,), (0.3081,))
])

train\_set = datasets.ImageFolder("MNIST\_dataset/train", transform=transform)
train\_loader = DataLoader(train\_set, batch\_size=64, shuffle=True)
\`\`\`


---

## Attribution

When using this dataset, please cite the original MNIST dataset creators:

LeCun Y, Cortes C, Burges CJC. *The MNIST Database of Handwritten Digits.*
[http://yann.lecun.com/exdb/mnist/](http://yann.lecun.com/exdb/mnist/)

BibTeX:
\`\`\`bibtex
@article{lecun1998mnist,
title={The MNIST database of handwritten digits},
author={LeCun, Yann and Cortes, Corinna and Burges, Christopher JC},
journal={[http://yann.lecun.com/exdb/mnist/}](http://yann.lecun.com/exdb/mnist/}),
year={1998}
}
\`\`\`

---

## License

This replication dataset is shared under the **Creative Commons Attribution-Share Alike 3.0** License, following the original licensing terms.
