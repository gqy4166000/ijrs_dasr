
# Dual-Det : A Fast Detector for Oriented Object Detection in Aerial Images

The code is useful for DOTA, HRSC2016 and UCAS-AOD

## How to get dataset?
- **Dota**: Dota is a large-scale dataset for object detection in aerial images. 
    It can be used to develop and evaluate object detectors in aerial images. 
    You can get the dataset via their [home page](https://captain-whu.github.io/DOTA/dataset.html).
- **[HRSC2016](https://www.kaggle.com/guofeng/hrsc2016)**
- **[UCAS-AOD](https://www.ucassdl.cn/resource.asp)**



### Installation
0. Create a new conda environment and install pytorch v1.0+ and torchvision
1. Clone code 
```
    git clone https://github.com/gqy4166000/DASR.git
```
2. Install the requirements
```
    pip install -r requirements.txt
```
3. Compile polyiou
```
    cd src
    sudo apt-get install swig
    swig -c++ -python polyiou.i
    python setup.py build_ext --inplace
    cd ..
```
4. Compile deformable convolutional
```
    cd src/lib/models/networks/DCNv2
    ./make.sh
```

### Usage

Download the dataset and copy the partitioned data to the **\data** folder in the following format. For DOTA, images and labels need to be splited for use(by **ImgSplit.py** or **ImgSplit_multi_process.py**).
```
.
├── src
└── data
    ├── Dota1.0*
        ├── train_sp*
            ├──images
            └──labelTxt
        └── val_sp*
            ├──images
            └──labelTxt
```
*mean that you can change the folder name and the path name in the **DOTA** file must also be changed. 

- Train

```
    python main.py --dataset dota --exp_id dota_train --gpus 0,1 --batch_size 32
```
- Val
```
    python main.py --dataset dota --exp_id dota_val --gpus 0 --test
```
You can adjust learning parameters in **opt.py**, and select single Angle, double Angle, and other branches in **cfg.py**.




