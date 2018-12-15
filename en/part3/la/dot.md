# Dot Product

## Vector-Vector  ( Support CPU and GPU )

Definition： $$\alpha = x^Ty$$ . 	 $$x$$ and $$y$$  are two vectors with size length, $$\alpha$$ is the result of dot product.

```cpp
// take double for an example
// PS： In Hice, the result of dot product between vector and vector is defined as a zero-dim tensor, but not a scalar.

// create two vectors with length=8
Tensor<double, 1> vector1(8);
Tensor<double, 1> vector2(8);

// init vector1 and vector2
...

// create a zero-dim tensor
Tensor<double, 0> result_0d;
result_0d = dot(vector1, vector2);
```



## Matrix-Vector  ( Support CPU and GPU ) 

Definition： $$ y_{m} = A_{m,n}\cdot v_{n}$$.   $$A_{m,n}$$ is a matrix with $$m$$ rows and $$n$$ columns, $$v_n$$ is a vector with $$n$$ elements, and $$y_m$$ is the result vector with $$m$$ elements.

```cpp

// create a vector with length=8, and a matrix with size = 8 X 8
Tensor<double, 2> matrix(8, 8);
Tensor<double, 1> vector(8);

// init matrix and vector
...

Tensor<double, 1> result_1d(8);
result_1d = dot(matrix, vector);
```



## Matrix-Matrix ( Support CPU and GPU )

Definition： $$ C_{m,k} = A_{m,n}\cdot B_{n,k}$$.     $$A_{m,n}$$ is a matrix with $$m$$ rows and $$n$$ columns, $$B_{n,k}$$ is a matrix with $$n$$ rows and $$k$$ columns, $$ C_{m,k} $$ is the result matrix with $$m$$ rows and $$k$$ columns.

```cpp

// create two matrics with size = 8 X 8
Tensor<double, 2> matrix1(8, 8);
Tensor<double, 2> matrix2(8, 8);

// init matrix1 and matrix2
...

Tensor<double, 2> result_2d(8, 8);
result_2d = dot(matrix1, matrix2);
```
