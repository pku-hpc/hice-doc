# Transpose

## Matrix（Only support CPU）

Definition：$$B_{n,m} ={A_{m,n}}^T \cdot{A_{m,n}}$$ is a matrix with $$m$$ rows and $$n$$ columns, $$B_{n,m}$$ is the result with $$n$$ rows and $$m$$ columns。

```cpp
// take double for an example
// Transpose should only be applied to matrix.(tensor<2>)

// create matrix with size = 8 X 8
Tensor<double, 2> matrix(8, 8);

// init matrix
...

Tensor<double, 2> result_2d(8, 8);
result_2d = transpose(matrix);
```

