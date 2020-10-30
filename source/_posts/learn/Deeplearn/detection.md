---
title: 目标检测
date: 2020-10-24 23:05:19
tags: deeplearn
    - yolo
    - RCNN 
categories: 玲酱の学习笔记
---

# 目标检测
**记得看一下吴恩达明天**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200610163813143.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JlaW5kZWVyMTEwMQ==,size_16,color_FFFFFF,t_70)
## yolo目标检测
[https://blog.csdn.net/guleileo/article/details/80581858](https://blog.csdn.net/guleileo/article/details/80581858)

 
## **FASTER -RCNN:**
(1)输入测试图像；  
(2)将整张图片输入CNN，进行特征提取；  
(3)用RPN先生成一堆Anchor box，对其进行裁剪过滤后通过softmax判断anchors属于前景(foreground)或者后景(background)，即是物体or不是物体，所以这是一个二分类；同时，另一分支bounding box regression修正anchor box，形成较精确的proposal（注：这里的较精确是相对于后面全连接层的再一次box regression而言）  
(4)把建议窗口映射到CNN的最后一层卷积feature map上；  
(5)通过RoI pooling层使每个RoI生成固定尺寸的feature map；  
(6)利用Softmax Loss(探测分类概率) 和Smooth L1 Loss(探测边框回归)对分类概率和边框回归(Bounding box regression)联合训练.

相比FASTER-RCNN，主要两处不同:  
(1)使用RPN(Region Proposal Network)代替原来的Selective Search方法产生建议窗口；  
(2)产生建议窗口的CNN和目标检测的CNN共享

改进:  
(1) 如何高效快速产生建议框？  
FASTER-RCNN创造性地采用卷积网络自行产生建议框，并且和目标检测网络共享卷积网络，使得建议框数目从原有的约2000个减少为300个，且建议框的质量也有本质的提高.

**Faster R CNN结构详解**
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200610224244954.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JlaW5kZWVyMTEwMQ==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200610224249176.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JlaW5kZWVyMTEwMQ==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200610224249833.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JlaW5kZWVyMTEwMQ==,size_16,color_FFFFFF,t_70)
从上面的三张图可以看出，Faster R CNN由下面几部分组成：  
1.数据集，image input  
2.卷积层CNN等基础网络，提取特征得到feature map  
3-1.RPN层，再在经过卷积层提取到的feature map上用一个3x3的slide window，去遍历整个feature map,在遍历过程中每个window中心按rate，scale（1:2,1:1,2:1）生成9个anchors，然后再利用全连接对每个anchors做二分类（是前景还是背景）和初步bbox regression，最后输出比较精确的300个ROIs。  
3-2.把经过卷积层feature map用ROI pooling固定全连接层的输入维度。  
4.然后把经过RPN输出的rois映射到ROIpooling的feature map上进行bbox回归和分类。



**进一步了解目标检测**
1、[https://blog.csdn.net/qq_35451572/article/details/80249259](https://blog.csdn.net/qq_35451572/article/details/80249259)

2、[https://blog.csdn.net/qq_35451572/article/details/80249259?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase](https://blog.csdn.net/qq_35451572/article/details/80249259?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase)

3、[https://blog.csdn.net/qq_32241189/article/details/80573087](https://blog.csdn.net/qq_32241189/article/details/80573087)