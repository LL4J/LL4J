# LL4J

LL4J (Light Learning For Java) is a minimalistic Java implementation for deep learning.  
It was open-sourced under the MIT license due to a project reorganization.

### Highlights

No third-party dependencies.  
MinRT (Minimum Runtime): Only one class, less than 70 lines of code.  
The test code can achieve an accuracy of 82% on the Fashion-MNIST (image 10-class classification problem).  
The trained model can be compiled into C code and then run on devices that only support standard C.

### Verifying the above metrics

1. Obtain the Fashion-MNIST dataset from [here](https://www.kaggle.com/datasets/zalando-research/fashionmnist) (or use
   the shipped one).
2. Unzip only the training set, run huzpsb.ll4j.samples.TestTrain
3. Move the generated test.model to the source code root directory; delete the training set, unzip the test set.
4. Delete all files except huzpsb.ll4j.samples.TestMinRt and huzpsb.ll4j.minrt.MinRt.
5. Compile the test.model into C code through huzpsb.ll4j.minrt.Compiler.

### Recommended Usage

Minecraft plugins: Because in most cases, the classification problems in MC are less than 10 classes, and the complexity
is not as high as image recognition.
Raspberry Pi or microcontroller: Because in most cases, even if resources are sufficient, Python+NumPy is still too
extravagant.
In addition, through the rolling window method, the memory required at runtime can be compressed to 3KB (the model file
is still 1MB+).
The code is not attached because the file buffer is a platform-related major resource consumption, the simple idea is to
calculate the quantity of the next layer one by one.

### Common Pitfalls

- ....is NaN! Plz reduce learning rate!
    - The learning rate is too high. Reduce it a bit.
- Wrong input size for...!
    - The sizes of the two adjacent layers must match.
- C/RNN? GPU/SIMD?
    - Use DL4J and TensorFlow.
- The accuracy rate decreased at the end of the training?
    - The model is not the bigger the better. Reduce the number of layers of the model and lower the size.

### Future Plans

Only serious bug fixes will be provided.

### Copyright Notice

Your program should indicate in a user-visible way that it uses LL4J.
There are no more requirements beyond this. No need to open source, can be commercial.

Thanks to zalando-research for open-sourcing the Fashion-MNIST dataset under the MIT license.