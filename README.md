# FastSpeech-FloWaveNet
This repository is adapted from [FastSpeech-Pytorch](https://github.com/xcmyz/FastSpeech) from `xcmyz` and [FloWaveNet](https://github.com/ksw0306/FloWaveNet) from `kws0306`. Instead of using WaveGlow, FastSpeech from this repository use FloWaveNet as the vocoder. Many thanks to the original authors. Please check their repositories for more detailed description.

## Prepare FloWaveNet Model
1. Download pretrained model from [here](https://drive.google.com/drive/folders/1OtacR02ecsFhyqXMwHJdDTKKQ-lWx390?usp=sharing), and put it under `pretrained_model`.
2. Download pretrained model from [here](https://drive.google.com/file/d/1vMrKtbjPj9u_o3Y-8prE6hHCc6Yj4Nqk/view?usp=sharing), and put it under `new_model`.

## Setup Environment
Please check the [Pytorch](https://pytorch.org) website if CUDA version needs to be downloaded.
```
conda create -n fastspeech python=3.8.0
conda activate fastspeech
conda install --file requirements.txt -c pytorch -c defaults -c anaconda -c conda-forge
```
Or consider using [colab](https://colab.research.google.com/drive/19Jhnk5BkNa6R97tgJn97QOV8fyogpeHm?usp=sharing)

## Synthesize
The result will be written into `results/${step}_${flowavenets_step}`. Please change `flowavenet_step` according to the file downloaded from [Prepare FloWaveNet Model](#prepare-flowavenet-model) to synthesize audio in different quality.
```
python synthesize.py --file generate.txt --step 135000 --flowavenet_step 126764
```