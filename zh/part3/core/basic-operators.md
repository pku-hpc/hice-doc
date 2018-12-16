# Basic-Operators (基础操作)

## 一元运算（支持CPU和GPU）

- 取绝对值：返回一个新的张量，其中每一个元素等于原张量相应元素的绝对值。

  ```cpp
  // 'result' 和 'tensor'的维度信息必须一致
  result = tensor.abs();
  ```


- 取相反值：返回一个新的张量，其中每一个元素等于原张量相应元素的相反数。

  ```cpp
  // 'result' 和 'tensor'的维度信息必须一致
  result = -tensor;
  ```

## 二元运算（支持CPU和GPU）

- 加法：元素级别加法

  ```cpp
  // 张量之间的加法
  // 'result' 和 'tensor_a' 以及 'tensor_b' 的维度信息必须一致
  result = tensor_a + tensor_b;
  
  // 若其中存在零维张量，则自动广播
  result = tensor_nd + tensor_0d;	
  result = tensor_0d + tensor_nd;	
  
  // 张量+标量
  // 'scalar'的数据类型必须和'tensor_a'保持一致
  double/int/float scalar = ...;
  result = tensor_a + scalar;
  
  // !!! 不支持‘标量+张量’操作
  // !!! 下面代码会编译错误
  double/int/float scalar = ...;
  result = scalar + tensor_a; 
  ```


- 减法：元素级别减法，运算符为'-'，用法同加法。


- 乘法：元素级别乘法，运算符为'*'，用法同加法。


- 除法：元素级别除法，运算符为'/'，用法同加法。


- 取余：暂不支持



## 归约运算（仅支持CPU）

- 最大值：返回张量所有元素的最大值。

  ```cpp
  // 'result_0d' 必须是一个零维张量
  // 'result_0d'的数据类型必须和'tensor'保持一致
  Tensor<double, 0> result_0d;
  result_0d = tensor.maximum();
  ```


- 最小值：返回张量所有元素的最小值。

  ```cpp
  // 'result_0d' 必须是一个零维张量
  // 'result_0d'的数据类型必须和'tensor'保持一致
  Tensor<double, 0> result_0d;
  result_0d = tensor.minimum();
  ```


- 平均值：返回张量所有元素的平均值。

  ```cpp
  // 'result_0d' 必须是一个零维张量
  // 'result_0d'的数据类型必须和'tensor'保持一致
  Tensor<double, 0> result_0d;
  result_0d = tensor.mean();
  ```


- 和：返回张量所有元素的和。

  ```cpp
  // 'result_0d' 必须是一个零维张量
  // 'result_0d'的数据类型必须和'tensor'保持一致
  Tensor<double, 0> result_0d;
  result_0d = tensor.sum();
  ```


- 一模：将张量视为一维向量，返回向量的一模。

  ```cpp
  // 'result_0d' 必须是一个零维张量
  // 'result_0d'的数据类型必须和'tensor'保持一致
  Tensor<double, 0> result_0d;
  result_0d = tensor.norm1();
  ```


- 二模：将张量视为一维向量，返回向量的二模。'

  ```cpp
  // 'result_0d' 必须是一个零维张量
  // 'result_0d'的数据类型必须和'tensor'保持一致
  Tensor<double, 0> result_0d;
  result_0d = tensor.norm2();
  ```
