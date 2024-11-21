# RbG_framework

## 1. Description

- Templates from https://github.com/ashleve/lightning-hydra-template was used.

- `Pytorch-lighting` + `Hydra` + `Tensorboard` was used for experiment-tracking


## 2. Installation

```bash
conda env create -f environment.yml
```

If you encounter an error while setting up the environment using the environment.yaml file, please install the libraries in the following order:
```bash
conda create --name RbG_framework python=3.9.16
conda activate RbG_framework
pip install hydra-core
python -m pip install lightning
pip install pyrootutils
pip install rich
pip install hydra-colorlog
pip install h5py
pip install monai-weekly
pip install torchvision
pip install torchio
pip install lpips
pip install opencv-python
pip install torch-fidelity
pip install gdown
pip install tensorboardX
```

## 3. Dataset
#### Dataset 
Grand challenge ['SynthRAD 2023'](https://synthrad2023.grand-challenge.org/) Pelvis MR, CT
Demo data will be provided.

#### File Format: 
h5

#### Pretrained model
Pretrained data will be provided.

## 4. How to run (Stage 1 will be updated soon.)

```bash
#### Stage 1 (test)
python src/train.py model='munit.yaml' tags='MUNIT_Test' trainer.devices=[0] train=False ckpt_path='<YOUR_PROJECT_PATH>/pretrained/synthesis/munit_synthesis_epoch98.ckpt'
# <YOUR_PROJECT_ROOT>: Put your project path (e.g., /SSD_8TB/RbG_framework)
```

```bash
#### Stage 2 (test)
python src/train.py model='RbG.yaml' trainer.devices=[0] tags='RbG_MrCtPelvis_MUNIT_Test' data.use_split_inference=true train=False ckpt_path='<YOUR_PROJECT_ROOT>/pretrained/proposed/proposed_weight.ckpt'
# <YOUR_PROJECT_ROOT>: Put your project path (e.g., /SSD_8TB/RbG_framework)
# data.use_split_inference: Whether to split the image into two parts for inference. Set to False if memory is sufficient.
```