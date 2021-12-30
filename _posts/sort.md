```
layout: post
title:  "About sort"
date:   2021-12-27 20:20:20
categories: viva
```

# About SORT

### 	**Yolo + kalman + Hungarian**

#### 		Yolo				-> 检测框

#### 		kalman		  -> 预测

#### 		Hungarian	-> 数据关联

###### 		☆ **关于深度学习**

```
	深度学习因其强大的特征提取能力在动物形体关键部位识别方面应用广泛。目前，深度学习目标检测
算法主要分为两类：
	一类是以基于区域的卷积神经网络（Region-based Convolution Neural Networks，R-CNN）
系列为代表的候选区域检测算法；
	另一类是以单次多框检测器（Single Shot MultiBox Detector，SSD）和单次检测器（You Only Look Once，YOLO）系列为代表的回归分析检测算法。
```

##### 								{ 马氏距离

##### Hungarian     ->   { IOU 面积重合度

##### 													{ 欧式距离

```
基于重叠度（IoU）的 Hungarian 算法多目标跟踪中需将检测框与预测框进行匹配，使在连续两帧之间保持关联。考虑到 Hungarian 算法时间复杂度低，故用该算法对预测框和检测框进行匹配。以检测框和预测框的重叠度作为匹配依据，重叠度越大表示检测框与预测框关联性越高。IoU 的计算如式（6）所示：
```

![](C:\Users\shxi_\AppData\Roaming\Typora\typora-user-images\image-20211227141648693.png)

```
式中 Sd 为检测框面积（单位为像素），Sp 为预测框面积（单位为像素）。
	Hungarian 算法以重叠度为关联依据建立检测框和预测框之间的匹配关系，寻求 IoU 最大的一组最优匹配，如式（7）所示：
```





[![image-20211227141628019](C:\Users\shxi_\AppData\Roaming\Typora\typora-user-images\image-20211227141628019.png)]

```
式中M为检测框个数，i 为上颚检测框与预测框匹配对数，Di、Ti分别为第i对匹配中的上颚检测框和预测框。
```



