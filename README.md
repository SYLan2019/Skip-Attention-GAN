# Skip-Attention-GANomaly

This repository contains PyTorch implementation of the following paper: **SAGAN: SKIP-ATTENTION GAN FOR ANOMALY DETECTION**.

You can get the paper from [link](https://ieeexplore.ieee.org/document/9506332)

## 1. Installation

1. First clone the repository
   ```
   git clone https://github.com/samet-akcay/skip-ganomaly.git
   ```
2. Create the virtual environment via conda
    ```
    conda create -n sagan python=3.8
    ```
3. Activate the virtual environment.
    ```
    conda activate sagan
    ```
4. Install the dependencies.
   ```
   pip install --user --requirement requirements.txt
   ```

5. Install the SoftPool(you can see details in [github link](https://github.com/alexandrosstergiou/SoftPool))

   ```
   git clone https://github.com/alexandrosstergiou/SoftPool.git
   cd SoftPool-master/pytorch
   make install
   ```

   

## 3. Experiment

To replicate the results in the paper for CIFAR10  dataset, run the following commands:

``` shell
# CIFAR
sh experiments/run_cifar.sh
```

## 4. Training
To list the arguments, run the following command:
```
python train.py -h
```

### 4.1. Training on CIFAR10
To train the model on CIFAR10 dataset for a given anomaly class, run the following:

``` 
python train.py \
    --dataset cifar10                                                             \
    --niter <number-of-epochs>                                                    \
    --abnormal_class                                                              \
        <airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck>    \
    --display                                   # optional if you want to visualize        
```

### 4.2. Train on Custom Dataset
To train the model on a custom dataset, the dataset should be copied into `./data` directory, and should have the following directory & file structure:

```
Custom Dataset
├── test
│   ├── 0.normal
│   │   └── normal_tst_img_0.png
│   │   └── normal_tst_img_1.png
│   │   ...
│   │   └── normal_tst_img_n.png
│   ├── 1.abnormal
│   │   └── abnormal_tst_img_0.png
│   │   └── abnormal_tst_img_1.png
│   │   ...
│   │   └── abnormal_tst_img_m.png
├── train
│   ├── 0.normal
│   │   └── normal_tst_img_0.png
│   │   └── normal_tst_img_1.png
│   │   ...
│   │   └── normal_tst_img_t.png

```

Then model training is the same as the training explained above.

```
python train.py                     \
    --dataset <name-of-the-data>    \
    --isize <image-size>            \
    --niter <number-of-epochs>      \
    --display                       # optional if you want to visualize
```

For more training options, run `python train.py -h`.

## 5. Citing Skip-Attention-GANomaly

If you use this repository or would like to refer the paper, please use the following BibTeX entry
```
@INPROCEEDINGS{9506332,
  author={Liu, Guoliang and Lan, Shiyong and Zhang, Ting and Huang, Weikang and Wang, Wenwu},
  booktitle={2021 IEEE International Conference on Image Processing (ICIP)}, 
  title={SAGAN: Skip-Attention GAN For Anomaly Detection}, 
  year={2021},
  volume={},
  number={},
  pages={2468-2472},
  doi={10.1109/ICIP42928.2021.9506332}}
```

