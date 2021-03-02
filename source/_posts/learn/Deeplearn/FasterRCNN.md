---
title: Faster R-CNN
date: 2020-11-24 10:45:19
tags: R-CNN
    - Fast R-CNN
    - RPN
    - Anchors

categories: learn
---
# 1、R-CNN
>1.输入测试图像；  
>2.利用selective search 算法在图像中从上到下提取2000个左右的Region Proposal；  
>3.将每个Region Proposal缩放(warp)成227*227的大小并输入到CNN，将CNN的fc7层的输出作为特征；  
>4.将每个Region Proposal提取的CNN特征输入到SVM进行分类；  
>5.对于SVM分好类的Region Proposal做边框回归，用Bounding box回归值校正原来的建议窗口，生成预测窗口坐标.








