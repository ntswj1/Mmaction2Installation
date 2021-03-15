# Mmaction2 installation with docker image

#### Requirements
- Docker
- CUDA 9.2+

#### Installation
1. Install NVIDIA container toolkit.
```
sudo apt-get install -y nvidia-container-toolkit
sudo apt-get install -y nvidia-docker2
reboot
```

2. Download the [Dockerfile](https://github.com/open-mmlab/mmaction2/blob/master/docker/Dockerfile), and build an image.
```
# build an image with PyTorch 1.6.0, CUDA 10.1, CUDNN 7.
docker build -f ./docker/Dockerfile --rm -t mmaction2 .
```

3. Create a new container.
```
docker run --name mmaction2WS --gpus all --shm-size=8g -it mmaction2
```

4. Download checkpoints and save them in the folder  __/mmaction2/checkpoints/__. Here we use one example [tsn_r50_1x1x3_100e_kinetics400_rgb_20200614-e508be42.pth](https://download.openmmlab.com/mmaction/recognition/tsn/tsn_r50_1x1x3_100e_kinetics400_rgb/tsn_r50_1x1x3_100e_kinetics400_rgb_20200614-e508be42.pth).

#### Verification
Download <kbd>testMmaction2.py</kbd> and save it in the folder __/mmaction2/__.
Run and check if Mmaction2 is installed correctly.
```
python testMmaction2.py
```
The results should look like this
```
Use load_from_local loader
The top-5 labels with corresponding scores are:
arm wrestling:  29.616438
rock scissors paper:  10.754841
shaking hands:  9.908401
clapping:  9.189913
massaging feet:  8.305307
```

#### Reference
 For more information of installation, please check this website: [Mmaction2 installation](https://github.com/open-mmlab/mmaction2/blob/master/docs/install.md)
