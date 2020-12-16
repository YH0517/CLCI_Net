# CLCI-Net
[CLCI-Net: Cross-Level Fusion and Context Inference Networks for Lesion Segmentation of Chronic Stroke (MICCAI 2019)](https://link.springer.com/chapter/10.1007/978-3-030-32248-9_30)
# 作者
Hao Yang, Weijian Huang, Kehan Qi, Cheng Li, Xinfeng Liu, Meiyun Wang, Hairong Zheng, and Shanshan Wang
# 项目简介
## 1. 功能
采用CLCI-Net实现对ATLAS数据集的图像分割
## 2. 性能
|Dice |Precision|Recall|VOE|RVD|
|-----|-----|-----|-----|-----|
|0.581|0.649    |0.581 |54.6|25.4|
## 3. 使用数据集
数据集：ATLAS数据集[1]，包含229个case，划分了训练集、测试集和验证集。数据采用[这里](https://github.com/Andrewsher/ATLAS-dataset-generate-h5file)所示的方法，对训练集、测试集合验证集分别进行预处理，得到3个h5文件。

[1] Liew, Sook-Lei, et al. "A large, open source dataset of stroke anatomical brain images and manual lesion segmentations." Scientific data 5 (2018): 180011.

# 运行环境与依赖
|类别|名称|版本|
|-----|-----|-----|
|os|ubuntu|16.04|
|深度学习框架|Keras|2.2.0|
|深度学习框架|tensorflow|1.10.0|

# 输入与输出
|名称|说明|
|-----|-----|
|输入|单通道灰度图，值域为0-1，大小为224x176。|
|输出|标签。0表示背景，1表示病变|

# 运行方式
在.py文件中执行如下的操作以使用CLCI-Net模型：

``` python
from CLCI_Net import CLCI_Net, dice_coef, dice_foef_loss
model = CLCI_Net()
model.summary()
model.compile(optimizer=Adam(lr=1e-4), loss=dice_coef_loss, metrics=[dice_coef])
```

其余步骤与X-Net中main.py中的操作一致。