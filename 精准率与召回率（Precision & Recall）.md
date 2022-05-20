### 精准率与召回率（Precision & Recall）

Precision 和 Recall最早是信息检索中的概念，用来评价一个信息检索系统的优劣。Precision 就是检索出来的条目中（比如：文档、网页等）有多大比例是我们需要的，Recall就是所有我们需要的网页的条目有多大比例被检索出来了。用到目标检测领域，假设我们有一组图片，里面有若干待检测的目标，Precision就代表我们模型检测出来的目标有多打比例是真正的目标物体，Recall就代表所有真实的目标有多大比例被我们的模型检测出来了。

![image-20220520150115585](C:\Users\Ricar\AppData\Roaming\Typora\typora-user-images\image-20220520150115585.png)

![image-20220520150132289](C:\Users\Ricar\AppData\Roaming\Typora\typora-user-images\image-20220520150132289.png)

![[公式]](https://www.zhihu.com/equation?tex=Precision%3D%5Cfrac%7BTP%7D%7BTP%2BFP+%7D)

![[公式]](https://www.zhihu.com/equation?tex=Recall%3D%5Cfrac%7BTP%7D%7BTP%2BFN%7D)



### PR曲线

我们当然希望检测的结果P越高越好，R也越高越好，但事实上这两者在**某些情况下是矛盾的**。比如极端情况下，我们只检测出了一个结果，且是准确的，那么Precision就是100%，但是Recall就很低；而如果我们把所有结果都返回，那么必然Recall必然很大，但是Precision很低。

因此在不同的场合中需要自己判断希望P比较高还是R比较高。如果是做实验研究，可以绘制Precision-Recall曲线来帮助分析。

这里我们举一个简单的例子，假设我们的数据集中共有五个待检测的物体，我们的模型给出了10个候选框，我们按照模型给出的置信度由高到低对候选框进行排序。

![preview](https://pic3.zhimg.com/v2-866d3e50348f6f882a9f4a81d9f641e2_r.jpg)

表格第二列表示该候选框是否预测正确（即是否存在某个待检测的物体与该候选框的iou值大于0.5）第三列和第四列表示以该行所在候选框置信度为阈值时，Precision和Recall的值。我们以表格的第三行为例进行计算：

![[公式]](https://www.zhihu.com/equation?tex=TP%3D2+) ![[公式]](https://www.zhihu.com/equation?tex=FP%3D1+) FN = 3

![[公式]](https://www.zhihu.com/equation?tex=Precision%3D%5Cfrac%7B2%7D%7B2%2B1%7D%3D0.67)

![[公式]](https://www.zhihu.com/equation?tex=Recall%3D%5Cfrac%7B2%7D%7B2%2B3%7D%3D0.4+)

由上表以Recall值为横轴，Precision值为纵轴，我们就可以得到PR曲线。我们会发现，Precision与Recall的值呈现负相关，在局部区域会上下波动。

![preview](https://pic1.zhimg.com/v2-8e5dea717aa368da9e66d91f4fbe053c_r.jpg)

### AP(Average Precision)

顾名思义AP就是平均精准度，简单来说就是对PR曲线上的Precision值求均值。对于pr曲线来说，我们使用积分来进行计算。

![[公式]](https://www.zhihu.com/equation?tex=AP%3D%5Cint_%7B0%7D%5E%7B1%7Dp%28r%29dr)

### AUC(Area under curve)

绘制出平滑后的PR曲线后，用积分的方式计算平滑曲线下方的面积作为最终的AP值。

![[公式]](https://www.zhihu.com/equation?tex=AP%3D%5Cint_%7B0%7D%5E%7B1%7Dp_%7Bsmooth%7D%28r%29dr)

[目标检测中的AP，mAP - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/88896868)