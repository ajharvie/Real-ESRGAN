# Real-ESRGAN
PyTorch implementation of a Real-ESRGAN model trained on custom dataset. This model shows better results on faces compared to the original version. It is also easier to integrate this model into your projects.

> This is forked from the ai-forever implementation, which is in turn derived from the [original Real ESRGAN](https://github.com/xinntao/Real-ESRGAN). This version contains training weights and bug fixes for deployment on HPC.

Real-ESRGAN is an upgraded [ESRGAN](https://arxiv.org/abs/1809.00219) trained with pure synthetic data is capable of enhancing details while removing annoying artifacts for common real-world images. 

- [Paper (Real-ESRGAN: Training Real-World Blind Super-Resolution with Pure Synthetic Data)](https://arxiv.org/abs/2107.10833)
- [Original implementation](https://github.com/xinntao/Real-ESRGAN)

### Installation

```bash
pip install git+https://github.com/ajharvie/Real-ESRGAN.git
```

A conda environment set up for HPC use is provided. This can be set up with

```bash
conda env create -f environment.yml

conda activate Real-ESRGAN

```

### Usage

---

Basic usage:

```python
import torch
from PIL import Image
import numpy as np
from RealESRGAN import RealESRGAN

device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')

model = RealESRGAN(device, scale=4)
model.load_weights('weights/RealESRGAN_x4.pth', download=True)

path_to_image = 'inputs/lr_image.png'
image = Image.open(path_to_image).convert('RGB')

sr_image = model.predict(image)

sr_image.save('results/sr_image.png')
```

### Examples

---

Low quality image:

![](inputs/lr_image.png)

Real-ESRGAN result:

![](results/sr_image.png)

---

Low quality image:

![](inputs/lr_face.png)

Real-ESRGAN result:

![](results/sr_face.png)

---

Low quality image:

![](inputs/lr_lion.png)

Real-ESRGAN result:

![](results/sr_lion.png)
