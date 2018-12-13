# K-Nearest-Neighbor

## 算法描述

给定训练数据集的多维特征向量`ref`，和其对应的类别信息`label`，根据用户自定义的常数`k`寻找未打标签的测试集`query`附近最邻近的k个实例，如果这k个实例的多数属于某个类，就把该测试数据分到这个类中。

## 语法说明

```cpp
// 默认CPU执行KNN
result = knn(ref, label, query, k);
// 用CUDA加速执行KNN
result = knn(ref, label, query, k).to(CUDA);
```

### 参数

* `ref`：训练数据特征，`(ref_num, dim)`的张量。
* `label`：训练数据类别标签，`(ref_num, 1)`的张量。
* `query`：测试数据集特征，`(query_num, dim)`的张量。
* `k`：选取最邻近的`k`个点。

### 返回值

* `result`：测试数据类别标签，`(query_num, 1)`的张量

## 性能测试

* 各部分运行时间

  ![图1 实验数据](../images/knn/knn-time.png)