# MLEP
Official github repository for the article [MLEP: Multi-granularity Local Entropy Patterns for Generalized Al-generated lmage Detection](https://arxiv.org/abs/2504.13726).

<img src="./MLEP.png" width="100%" alt="overall pipeline">

## Environment Setup
```sh
conda env create -f environment.yaml
```
Due to the large number of environment packages, the "solving environment" step of creating environment may be time-consuming.

## Getting the  Datasets
Test Datasets:
|                       |                Url                |
|:---------------------:|:---------------------------------:|
|     GAN Dataset1      |     [xxxdrive](url here)          | 
|     GAN Dataset2      |     [xxxdrive](url here)          | 
|   Diffusion Dataset   |     [xxxdrive](url here)          | 

You can also create a dataset with few images to test, just follow a similar folder structure below, and modify the dataroot in 'test.py'.

Train Datasets:
We use the same training dataset as NPR, which can be obtained at [NPR 2024 CVPR](https://github.com/chuangchuangtan/NPR-DeepfakeDetection).

## Directory structure
<details>
<summary> Click to expand the folder tree structure. </summary>

```
datasets
|-- TrainDatasets
|   |-- train
|   |-- val
|   `-- test
`-- TestDatasets
    |-- GAN-set-1        # Table1
    |   |-- biggan
    |   |-- cyclegan
    |   |-- gaugan
    |   |-- progan
    |   |-- stargan
    |   |-- stylegan
    |   `-- stylegan2
    |-- GAN-set-2        # Table2
    |   |-- AttGAN
    |   |-- BEGAN
    |   |-- CramerGAN
    |   |-- InfoMaxGAN
    |   |-- MMDGAN
    |   |-- RelGAN
    |   |-- S3GAN
    |   |-- SNGAN
    |   `-- STGAN
    `-- Diffusion-set    # Table3
        |-- adm
        |-- DALLE
        |-- dalle_mini
        |-- ddpm
        |-- glide_100_10
        |-- glide_100_27
        |-- glide_50_27
        |-- iddpm
        |-- ldm
        |-- ldm_200
        |-- ldm_200_cfg
        |-- midjourney
        |-- pndm
        |-- sdv1_new
        |-- sdv2
        `-- vqdiffusion

```
</details>

Further down are the '0_real' and '1_fake' folders.

## Training
Download the training datasets and modify the dataroot:
```sh
python train.py --name 4class-resnet50 --dataroot /Data/MLEP/datasets/TrainDatasets --classes car,cat,chair,horse --batch_size 32 --delr_freq 10 --lr 0.0002 --niter 100
```
## Testing

Download the testing datasets and modify the dataroot in 'test.py', and then run:
```sh
python test.py --model_path ./pretrained/model_epoch_best.pth --batch_size 64
```
## To Do
1. 环境文件'environment.yaml'为成功运行测试用到的环境，训练用到的其他包待添加
2. 测试集链接，待给出
3. 训练集来源和目录结构，待整理
