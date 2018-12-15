# Dot Product（点积）

## 向量与向量（支持CPU和GPU）

定义： $$\alpha = x^Ty$$ . 其中 $$x, y$$ 是两个长度相同向量，$$\alpha$$ 为点积结果。

```cpp
// 以double类型为例
// 注：在Hice中，向量与向量的乘积结果是零维张量，而不是标量

// 创建长度为8的两个向量
Tensor<double, 1> vector1(8);
Tensor<double, 1> vector2(8);

// 初始化vector1和vector2
...

// 创建零维张量
Tensor<double, 0> result_0d;
result_0d = dot(vector1, vector2);
```



## 矩阵与向量（支持CPU和GPU）

定义： $$ y_{m} = A_{m,n}\cdot v_{n}$$. 其中$$A_{m,n}$$为$$m \times n$$的二维矩阵，$$v_n$$为长度为$$n$$的向量，$$y_m$$为点积结果向量，长度等于$$m$$。

```cpp

// 创建长度为8的向量，以及8 X 8的两个矩阵
Tensor<double, 2> matrix(8, 8);
Tensor<double, 1> vector(8);

// 初始化matrix和vector
...

Tensor<double, 1> result_1d(8);
result_1d = dot(matrix, vector);
```



## 矩阵与矩阵（支持CPU和GPU）

定义： $$ C_{m,k} = A_{m,n}\cdot B_{n,k}$$. 其中$$A_{m,n}$$为$$m \times n$$的二维矩阵，$$B_{n,k}$$为$$n \times k$$的二维矩阵，$$ C_{m,k} $$为点积结果矩阵。

```cpp

// 创建长度为8 X 8的两个矩阵
Tensor<double, 2> matrix1(8, 8);
Tensor<double, 2> matrix2(8, 8);

// 初始化matrix1和matrix2
...

Tensor<double, 2> result_2d(8, 8);
result_2d = dot(matrix1, matrix2);
```
