# Transpose（转置）

## 矩阵（仅支持CPU）

定义： $$B_{n,m} ={A_{m,n}}^T$$ . 其中$$A_{m,n}$$为$$m \times n$$ 的二维矩阵，$$B_{n,m}$$为转置结果，尺寸为$$n \times m$$。

```cpp
// 以double类型为例
// 仅支持对二维矩阵进行转置操作

// 创建尺寸为8 X 8的矩阵
Tensor<double, 2> matrix(8, 8);

// 初始化matrix
...

Tensor<double, 2> result_2d(8, 8);
result_2d = transpose(matrix);
```

