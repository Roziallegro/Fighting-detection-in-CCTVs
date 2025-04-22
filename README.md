# Detecting fights in CCTV footages

## About
Exploring the relevance of LSTM and CNNs for detecting fighting in CCTV footages.

*[show results here]*

Results:  
|      | Vanilla LSTM | Xception + LSTM | MobileNet | ResNet with yolov7 | ResNet without yolov7 |
|:---: | :----------: | :-------------: | :-------: | :----------------: | :-------------------: |
| Accuracy on unseen datasets (%) | 0.43 | (training is too large to continue) | 0.60 | - | - |
| F1 score | - | - | 0.69 | - | - |

*F1 score is normally used for imbalanced datasets, of which we ensured that our dataset is balanced between fighting and non-fighting

## Installation
### Download code
```shell
git clone https://github.com/Roziallegro/Fighting-detection-in-CCTVs.git

cd Fighting-detection-in-CCTVs
```

### Pre-requitites
- Git and Git LFS
- CUDA toolkit
- Python

## Python Environment Setup for Training
1. Install requriements.
```shell
    pip install -r "requirement.txt"
```
2. Proceed to `training_LSTM.ipynb` for the vanilla implementation of LSTM. Likewise, you can proceed to `training_Xception_LSTM.ipynb`, `training_mobilenet.ipynb`, `training_ResNet.ipynb` respectively for LSTM + Xception, MobileNet and ResNet implementations.

3. Download datasets from: 
- [Fight detection survey dataset](https://github.com/seymanurakti/fight-detection-surv-dataset)
- [Real life violence dataset](https://github.com/seymanurakti/fight-detection-surv-dataset)
- In which the `VideoDataset` loader function automatically creates labels based on naming convention.
- If custom dataset is used, you can name violent datasets as `V_xxx.mp4` or `fixxx.mp4`. Meanwhile, non-violent datasets are named as `NV_xxx.mp4` or `nofixxx.mp4`.
- Preferably, each video is within 2 seconds long for training.

5. Update `video_folder = "../fight-detection-4"` to the correct file directory.

6. Run the code cells sequentially and read through comments for further information.

7. Debug when needed 😉.

*Weights will be saved in the root directory upon training

## Python Environment Setup for Inferencing
> Preferably use the ResNet with yolov7 weights for plug-and-play/testing.

1. Install requriements.
```shell
    pip install -r "requirement.txt"
```

2. Download [weights](https://drive.google.com/drive/u/2/folders/1GgBhyYF5ldI3fSK_v2oy6DTS8LzZcGmd) of the corresponding models needed. Eg: Download resnet weights from `ResNet saved weights` folder if you wish to play with the resnet model.

3. Save it in the same directory as `gradio_app.py`.
```shell
Fighting-detection-in-CCTVs
├── yolov7
├── README.md
├── requirements.txt
├── gradio_app.py
├── resnet_weights.pth
├── resnet_weights_without_yolo.pth
├── lstm_weights_with_yolo.pth
└── mobilenet_weights_with_yolov7.pth
```

3. Set-up gradio for user interface.