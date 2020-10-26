---
title: 深度学习划水基础
date: 2020-10-24 23:05:19
tags: deeplearn 
categories: learn
---
**摘要**：神经网络的核心组件，即层、网络、目标函数和优化器；  

**基本步骤：**
 1. 加载数据
 2. 构建网络：
 3. 编译
 4. 训练

# 潜水要点即技巧：
## 1、小批量梯度下降![在这里插入图片描述](https://img-blog.csdnimg.cn/20200613111457627.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JlaW5kZWVyMTEwMQ==,size_16,color_FFFFFF,t_70)
## 1、网络最后一层激活函数及损失函数：
**MSE**![在这里插入图片描述](https://img-blog.csdnimg.cn/20200613104308525.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JlaW5kZWVyMTEwMQ==,size_16,color_FFFFFF,t_70)
**softmax**：[分类问题用交叉熵做损失函数而不用MSE均方误差](https://blog.csdn.net/weixin_37567451/article/details/80895309?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.nonecase)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200611204824564.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JlaW5kZWVyMTEwMQ==,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20200611204804864.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JlaW5kZWVyMTEwMQ==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200613112516530.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JlaW5kZWVyMTEwMQ==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200525173907609.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JlaW5kZWVyMTEwMQ==,size_16,color_FFFFFF,t_70)  
sigmoid: y = 1/(1 + e-x)   范围(0~1)

tanh: y = (ex - e-x)/(ex + e-x)   范围（-1~1)

relu: y = max(0, x)范围（0~5）  

深层网络在训练时，tanh和sigmoid会在端值趋于饱和，造成训练速度减慢，故**深层网络的激活函数默认大多采用relu函数**，浅层网络可以采用sigmoid和tanh函数。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200525175017721.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JlaW5kZWVyMTEwMQ==,size_16,color_FFFFFF,t_70)
## 2、优化器
带动量的SGD、Adagrad、RMSProp 等变体
动量解决了SGD 的两个问题：收敛速度和局部极小点
## 3、拟合问题
泛化（模型可以准确预测）、过拟合和欠拟合![在这里插入图片描述](https://img-blog.csdnimg.cn/20200527235317120.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JlaW5kZWVyMTEwMQ==,size_16,color_FFFFFF,t_70)


## 4、CNN基础
### 1、卷积神经网络层有：
卷积层(convolution,conv)
池化层(pooling,pool)
全连接层(Fully connected,FC)
### 2、填充padding
通过一个3x3的过滤器来对6x6的图像进行卷积，得到了一幅4x4的图像，假设输出图像大小为nxn与过滤器大小为fxf，输出图像大小则为(n−f+1)∗(n−f+1)(n−f+1)∗(n−f+1)。容易失去边缘信息，**故引入padding进行边缘填充**，即在图像卷积操作之前，沿着图像边缘用0进行图像填充。
**padding的两种模式**：
Valid：无填充，输入图像nxn,过滤器fxf,输出图像大小为：(n−f+1)∗(n−f+1)
Same：有填充，则输出图像和输入图像一样大。

### 3、卷积步长stride
加入stride后卷积图像大小的通用计算公式为：输入图像：nxn，过滤器：fxf步长：s，padding：p，则输出图像为::⌊((n+2p−f)/s+1))⌋∗⌊((n+2p−f)/s+1)⌋，⌊⌋⌊⌋表示向下取整. 
例：输入图像7x7，过滤器3x3，步长为2，padding模式为valid为例输出图像大小为:⌊((7+2∗0−3)2+1)⌋∗⌊(7+2∗0−3)2+1)⌋=3∗3
### 4、池化pooling
**最大池化（Max pooling）**
最大池化计算的是最大值。例如：把4*4的图像分割成4个不同的区域，然后输出每个区域的最大值即可。其实这里我们选择了2x2的过滤器，步长为2。在一幅真图像中提取最大值可能意味着提取了某些特定特征，比如垂直边缘、一只眼、嘴巴等等。![在这里插入图片描述](https://img-blog.csdnimg.cn/2020052800150777.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3JlaW5kZWVyMTEwMQ==,size_16,color_FFFFFF,t_70)
**平均池化**
它计算的是区域内的平均值，在日常应用使用最多的还是最大池化。
池化的超参数：步长、过滤器大小、池化类型最大池化or平均池化




### 5、参数个数
每个过滤器都有333+1=28个参数，333为过滤器大小，1是偏差系数，10个过滤器参数个数就是28*10=280个。不论输入图像大小参数个数是不会发生改变的。

### 6、采样
1、缩小图像（或称为下采样（subsampled）或降采样（downsampled））的主要目的有两个：

 1. 使得图像符合显示区域的大小；
 2. 生成对应图像的缩略图。
 
**下采样原理**：对于一幅图像I尺寸为M*N，对其进行s倍下采样，即得到(M/s)*(N/s)尺寸的得分辨率图像，当然s应该是M和N的公约数才行，如果考虑的是矩阵形式的图像，就是把原始图像s*s窗口内的图像变成一个像素，这个像素点的值就是窗口内所有像素的均值：

2、放大图像（或称为上采样（upsampling）或图像插值（interpolating））的主要目的是：

 1. 放大原图像,从而可以显示在更高分辨率的显示设备上，图像的质量受到影响。不过，有一些缩放方法能增加图像的信息，使得缩放后的图像质量超过原图质量的。
 
**上采样原理**：图像放大几乎都是采用内插值方法，即在原有图像像素的基础上在像素点之间采用合适的插值算法插入新的元素。  


# 练习实例
## 识别手写数字

## 电影评论划二分类问题


## 新闻主题多分类问题   

## 预测房价（回归问题）

# 鸢尾花数据集分类问题
基于skearn的LogisticRegression
[Python实现鸢尾花数据集分类问题——基于skearn的LogisticRegression](https://blog.csdn.net/weixin_30788239/article/details/96095098)
