## Installation


### Requirements:
- PyTorch >= 1.6 (Mine 1.7.1 (CUDA 11.0))
- torchvision >= 0.4 (Mine 0.8.2 (CUDA 11.0))
- cocoapi
- yacs
- matplotlib
- GCC >= 4.9
- OpenCV
- python (Mine 3.8.18)


### Step-by-step installation

```bash

conda create --name BAL_RS_SGG 
conda activate BAL_RS_SGG


conda install ipython
conda install scipy
conda install h5py

# scene_graph_benchmark and coco api dependencies
pip install ninja yacs cython matplotlib tqdm opencv-python overrides


pip install torch==1.7.1+cu110 torchvision==0.8.2+cu110 torchaudio==0.7.2 -f https://download.pytorch.org/whl/torch_stable.html

export INSTALL_DIR=$PWD
# install pycocotools
cd $INSTALL_DIR
git clone https://github.com/cocodataset/cocoapi.git
cd cocoapi/PythonAPI
python setup.py build_ext install

# install apex
cd $INSTALL_DIR
git clone https://github.com/NVIDIA/apex.git
cd apex
python setup.py install --cuda_ext --cpp_ext

cd $INSTALL_DIR
git clone https://github.com/Zhuzi24/BAL.git
cd BAL

python setup.py build develop
unset INSTALL_DIR

# need to install mmrotate and mmdetection for STAR dataset

pip install openmim
mim install mmcv-full # Mine 1.7.1   
mim install mmdet # Mine 2.26.0 
git clone https://github.com/open-mmlab/mmrotate.git
cd mmrotate
pip install -r requirements/build.txt
pip install -v -e .

