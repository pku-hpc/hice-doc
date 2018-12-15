# Bisic-Operators

## Unary Operators ( Support CPU and GPU )

- Absolute value：element-wise 

  ```cpp
  // shape of 'result' should be same with 'tensor'
  result = tensor.abs();
  ```


- Negative：element-wise 

  ```cpp
  // shape of 'result' should be same with 'tensor'
  result = -tensor;
  ```

## Binary Operators ( Support CPU and GPU )

- Add：element-wise 

  ```cpp
  // between tensor and tensor
  // shape of 'result', 'tensor_a' and 'tensor_b' should be same.
  result = tensor_a + tensor_b;
  
  // between tensor<dim=n> and tensor<dim=0> is ok, tensor<dim=0> will be broadcasted.
  result = tensor_nd + tensor_0d;	
  
  // between tensor<dim=0> and tensor<dim=n> is ok, tensor<dim=0> will be broadcasted.
  result = tensor_0d + tensor_nd;	
  
  // between tensor and scalar
  // type of 'scalar' should be same with the datatype of 'tensor_a'.
  double/int/float scalar = ...;
  result = tensor_a + scalar;
  
  // !!! operator between scalar and tensor is not support.
  // !!! compile error if you put the following code into compiler.
  double/int/float scalar = ...;
  result = scalar + tensor_a; 
  ```


- Subtraction：element-wise, same usage with 'Add'.

  ```cpp
  result = tensor_a - tensor_b;
  ```

- Multiplication：element-wise, same usage with 'Add'.

  ```cpp
  result = tensor_a * tensor_b;
  ```


- Division：element-wise, same usage with 'Add'.

  ```cpp
  result = tensor_a / tensor_b;
  ```


- Residual：not supported for now.



## Reduce Operators ( Only support CPU)

- Maximum：return the maximum element of a tensor.

  ```cpp
  // 'result_0d' should be a zero-dim-tensor.
  // the datatype of 'result_0d'' should be same with 'tensor''.
  Tensor<double, 0> result_0d;
  result_0d = tensor.maximum();
  ```


- Minimum：return the minimum element of a tensor.

  ```cpp
  // 'result_0d' should be a zero-dim-tensor.
  // the datatype of 'result_0d'' should be same with 'tensor''.
  Tensor<double, 0> result_0d;
  result_0d = tensor.minimum();
  ```


- Mean：return the average value of a tensor.

  ```cpp
  // 'result_0d' should be a zero-dim-tensor.
  // the datatype of 'result_0d'' should be same with 'tensor''.
  Tensor<double, 0> result_0d;
  result_0d = tensor.mean();
  ```


- Sum：return the sum of all element in a tensor.

  ```cpp
  // 'result_0d' should be a zero-dim-tensor.
  // the datatype of 'result_0d'' should be same with 'tensor''.
  Tensor<double, 0> result_0d;
  result_0d = tensor.sum();
  ```


- Norm1：consider the tensor as a vector, and return its norm1.

  ```cpp
  // 'result_0d' should be a zero-dim-tensor.
  // the datatype of 'result_0d'' should be same with 'tensor''.
  Tensor<double, 0> result_0d;
  result_0d = tensor.norm1();
  ```


- Norm2：consider the tensor as a vector, and return its norm2.

  ```cpp
  // 'result_0d' should be a zero-dim-tensor.
  // the datatype of 'result_0d'' should be same with 'tensor''.
  Tensor<double, 0> result_0d;
  result_0d = tensor.norm2();
  ```







