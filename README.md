# LL4J

LL4J(Light Learning For Java)是一个深度学习的极小化Java实现。  
因为某项目改组而以MIT协议开源。

### 亮点速记

无任何第三方依赖。  
MinRT（非编译最小运行时）：仅有一个类，不到70行代码。  
测试代码能够在Fashion-MNIST（图像10分类问题）上达到82%的准确率。  
训练出的模型可以被编译成C代码，然后在只支持标准C的设备上运行。

### 验证上述指标

1，从[这里](https://www.kaggle.com/datasets/zalando-research/fashionmnist)获取Fashion-MNIST数据集（或者使用自带的）。  
2，只解压训练集，运行huzpsb.ll4j.samples.TestTrain  
3，将生成的test.model移动到源代码根目录；删除训练集，解压测试集。  
4，删除除了huzpsb.ll4j.samples.TestMinRt和huzpsb.ll4j.minrt.MinRt之外的所有文件。  
5，通过huzpsb.ll4j.minrt.Compiler将test.model编译成C代码。

### 推荐的用法

Minecraft插件：因为绝大多数情况下，MC中的分类问题不足10类，且复杂度比不上图像识别。  
树莓派或单片机：因为大多数情况下，哪怕资源充足Python+NumPy多多少少还是太奢侈了。  
此外，通过滚动窗口法，可以将运行时所需内存压缩到3KB（模型文件还是1MB+）。  
未附上代码，因为文件缓冲区是平台相关严重的资源消耗大头，简单思路是逐个计算下一层的量。

### 常见的坑

- ....is NaN! Plz reduce learning rate!
    - 学习率太大了。调小一点。
- Wrong input size for...!
    - 临近的两层大小必须匹配。
- C/RNN？GPU/SIMD？
    - 差不多得了。卷这个你干嘛不用DL4J和TensorFlow？
- 训练到最后准确率反而下降了？
    - 模型不是越大越好。把模型的层数减少，尺寸调低。

### 未来的计划

只提供对严重的bug的修复。

### 版权提示

你的程序应该以用户可见的方式指出自己使用了LL4J。  
除此之外没有更多要求。不必开源，可以商用。  

感谢zalando-research按MIT协议开源Fashion-MNIST数据集。  
