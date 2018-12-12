# 增加自定义的operation

有关张量基础操作，如`dot`，`transpose`等在`la`目录下开发。有关机器学习算法，如`knn`，`svm`等在`ml`目录下开发。有关卷积操作算法，在`nn`目录下开发。

代码过程主要遵循以下五步：

- 在`engine`的`namespace`中定义该操作的具体实现kernel，若操作要支持`cuda`，则需分别定义，并使用`enable_if`自动选择合适算法做计算。
- 在`op`的`namespace`中新增自定义`operation`的结构体，该结构体中需定义一个`apply`函数用于选择调用`engine namespace`中定义的合适的`kernel`，定义方法参考[这里](../concept/STINAE.md)。
- 定义新增自定义`operation`的模板表达式，主要应用了`Expression Template`技术。
- 定义新增自定义`operation`对应的`Traits`结构体，定义方法参考[这里](../concept/Traits.md)。
- 针对操作的模板表达式定义对应的`evalutor`。

新增头文件和对应operation的名字保持一致，放在指定目录下，定义完成后在`src/hice.h`中`#include`对应操作头文件即可。