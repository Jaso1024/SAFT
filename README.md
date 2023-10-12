# SAFT
Implementation of Self-Attention Factor-Tuning, a technique for Parameter-Efficient Fine-Tuning 
[![PyPI version](https://badge.fury.io/py/saft.svg)](https://badge.fury.io/py/saft)

## Requirements
```
- Python == 3.8
- torch == 1.10.0
- torchvision == 0.11.1
- timm == 0.4.12
- avalanche-lib == 0.1.0
- tqdm == 4.66.1
```

## Data
To get started, head over to the SSF data preparation page and download the VTAB-1K dataset: [SSF Data Preparation](https://github.com/dongzelian/SSF#data-preparation). Once you've obtained the data, place the dataset folders into `<YOUR PATH>/SAFT/data/`.

## Pretrained Model
Download the [pretrained ViT-B/16](https://storage.googleapis.com/vit_models/imagenet21k/ViT-B_16.npz) to `<YOUR PATH>/SAFT/ViT-B_16.npz`


## Results (.055 Million Trainable Backbone Parameters) (ViT-B/16)
Coming soon...
```
Caltech101: 91.6%
Oxford Flowers: 99.2%
```

## Run
```sh
cd <YOUR PATH>/SAFT
python3 Test.py
```

## Modular Quick-Start
```python
from SAFT import SAFT
from Utils import *

if __name__ == "__main__":
    saft = SAFT(
        model='vit_base_patch16_224',
        num_classes=get_classes_num('oxford_flowers102'),
        validation_interval=1,
        rank=3,
        scale=10
    )
    train_dl, test_dl = get_data('oxford_flowers102')
    saft.upload_data(train_dl, test_dl)
    saft.train(10)
```

