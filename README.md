## 安装

```
git clone https://github.com/graphdeco-inria/gaussian-splatting --recursive

conda create -n gaussian_splatting python=3.8 # 创建名为3dgs的python环境，建议3.8，
conda activate gaussian_splatting # 激活名为3dgs的python环境
cd gaussian-splatting
conda config --add channels pytorch
conda config --add channels conda-forge
nvcc --version #查看cuda的版本
conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia # 安装pytorch环境，cudatoolkit版本需要与安装的CUDA版本一致，均为12.1
conda install cudatoolkit=11.8 #找不到12.1 所以我安装了11.8
conda install plyfile    
conda install tqdm
pip install ./submodules/diff-gaussian-rasterization
pip install ./submodules/simple-knn
pip install ./submodules/fused-ssim
pip install opencv-python
pip install joblib
```

## 数据准备
```
data/
├── input/
│   ├── img0000.png
│   ├── ...
```

## 生成相机位姿
```
python convert.py -s data
```

## 训练
```
python train.py -s data -m output
```

## 渲染
```
python render.py  -m output
```

## 评估
```
python metrics.py  -m output
```
