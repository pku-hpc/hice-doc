# K-Nearest-Neighbor

## Algorithm description

The training examples are vectors in a multidimensional feature space named `ref`, each with a class label named `label`. The training phase of the algorithm consists only of storing the feature vectorsand class labels of the training samples.In the classification phase, `k` is a user-defined constant, and unlabeled vectors `query` is classified by assigning the label which is most frequent among the `k` training samples nearest to that query point.

## Usage

```cpp
// default run on CPU
result = knn(ref, label, query, k);
// Use GPU speed up
result = knn(ref, label, query, k).to(CUDA);
```

### Parameter

* `ref`：Features for training dataset，a tensor shape as `(ref_num, dim)`.
* `label`：Labels for training dataset，a tensor shape as `(ref_num, 1)`.
* `query`：Features for test dataset，a tensor shape as `(query_num, dim)`.
* `k`：Select the nearest `k` points.

### Return

* `result`：Labels for test dataset，a tensor shape as `(query_num, 1)`.

## Performance

* Running time of each parts

  ![图1 实验数据](../images/knn/knn-time.png)