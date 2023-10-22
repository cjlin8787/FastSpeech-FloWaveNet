# FastSpeech-FloWaveNet
This repository is adapted from [FastSpeech-Pytorch](https://github.com/xcmyz/FastSpeech) from `xcmyz` and [FloWaveNet](https://github.com/ksw0306/FloWaveNet) from `kws0306`. Instead of using WaveGlow, FastSpeech from this repository use FloWaveNet as the vocoder. Many thanks to the original authors. Please check their repositories for more detailed description.

## Prepare Dataset
1. Download and extract [LJSpeech dataset](https://keithito.com/LJ-Speech-Dataset/).
2. Put LJSpeech dataset in `data`. 
3. Unzip `alignments.zip`. The directory should look like the following:
```
data
├── README
├── __pycache__
│   └── ljspeech.cpython-38.pyc
├── ljspeech.py
├── metadata.csv
├── train.txt
└── wavs
    ├── LJ001-0001.wav
    ├── LJ001-0002.wav
    ...
    └── LJ050-0278.wav
```
4. Run `python3 preprocess.py`.

## Prepare FloWaveNet Model
1. Make directory `pretrained_model` under `flowavenet`. For Linux, MacOS user: `mkdir flowavenet/pretrained_model`.
2. Download pretrained model from [here](https://drive.google.com/drive/folders/1OtacR02ecsFhyqXMwHJdDTKKQ-lWx390?usp=sharing).
3. Put it under `pretrained_model`.

## Setup Environment
Please check the [Pytorch]() website if CUDA version needs to be downloaded.
```
conda create -n fastspeech python=3.8.0
conda activate fastspeech
conda install --file requirements.txt -c pytorch -c defaults -c anaconda
```

## Synthesize
The result will be written into `results/${step}_${flowavenets_step}`. Please change `flowavenet_step` according to the file downloaded from [Prepare FloWaveNet Model](#prepare-flowavenet-model) to synthesize audio in different quality.
```
python synthesize.py --file text.txt --step 135000 --flowavenet_step 126764
```