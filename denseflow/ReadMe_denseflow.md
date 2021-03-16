# Denseflow installation in Docker

#### Requirements
- CUDA (driver version > 400)

#### Installation
1. Add these commands in  <kbd>~/.bashrc</kbd>
```
export ZZROOT=$HOME/app
export PATH=$ZZROOT/bin:$PATH
export LD_LIBRARY_PATH=$ZZROOT/lib:$ZZROOT/lib64:$LD_LIBRARY_PATH
```
 Preserve the current shell (Run it everytime after add new contents)
```
source ~/.bashrc
```

2. Fetch scripts for installation
```
git clone https://github.com/innerlee/setup.git
cd setup
```

3. Install
- Install __nasm__, __yasm__, __libx264__, __openssl__
```
apt-get install dh-autoreconf (Optional)
./zznasm.sh
./zzyasm.sh
./zzlibx264.sh
./zzopenssl.sh
```
Add this command in <kbd>~/.bashrc</kbd>:
```
export OPENSSL_ROOT_DIR=$ZZROOT/ssl
```
- Install __cmake__, __libx265__, __libvpx__, __ffmmpeg__, __opencv__
```
./zzcmake.sh
./zzlibx265.sh
./zzlibvpx.sh
apt-get install pkg-config (Optional)
./zzffmpeg.sh
./zzopencv.sh
```
Add this command in <kbd>~/.bashrc</kbd>:
```
export OpenCV_DIR=$ZZROOT
```
- Install __boost__
```
./zzboost.sh
```
Add this command in <kbd>~/.bashrc</kbd>:
```
export BOOST_ROOT=$ZZROOT
```
- Install __hdf5__, __denseflow__
```
./zzhdf5.sh
./zzdenseflow.sh
```
#### Verification
```
denseflow ./demo/demo.mp4 -b=20 -a=tvl1 -s=1 -v
```
The results should look like this
```
"./demo/demo.mp4", frames ≈ 280
push frames gray, video_flow_idx 0, batch_size 280
loaded video "./demo/demo.mp4", 280 frames
load frames exit.
1 videos (280 frames, 279 tvl1 flows) processed, using 4.925s, decoding speed 56.8528fps, flow speed 56.6497fps
```

#### Reference
 For more information of installation, please check this website: [Denseflow installation](https://github.com/open-mmlab/denseflow/blob/master/INSTALL.md)
