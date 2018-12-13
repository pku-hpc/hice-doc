# Tensor

## 创建Tensor

目前默认创建的Tensor都是稠密类型的。

```cpp
// 创建一个二维的8*8的Tensor

// 方法一：参数代表每一维度Tensor中元素的个数
Tensor<double, 2> mat1(8, 8);

// 方法二：以array形式组织每一维度元素的个数
Tensor<double, 2> mat2({8,8});
```

## 初始化Tensor

* 拷贝函数

  ```cpp
  // 假设存在某一已初始化Tensor mat1
  Tensor<double, 2> mat2(8,8);
  // mat2中信息和mat1完全一致
  mat2 = mat1;
  ```

* 赋值

  也可循环访问Tensor中每一个元素，并对其赋值

  ```cpp
  for (int row = 0; row < 8; ++row)
      for (int col = 0; col < 8; ++col)
        mat(row, col) = value;
  ```

* 暂不支持直接将array类型转换为Tensor

## 访问Tensor

```cpp
// 和访问数组中元素类似，下标以元组形式组织，高维度在前，低维度在后
Tensor<double,2> mat(8,8);
cout<<mat(3,4)<<endl;
```

## Tensor的基本信息

Tenesor的基本信息包括Tensor的维度个数，每一维度元素的个数等，有两种访问方式：

* 直接从Tensor中获取

  ```cpp
  Tensor<double, 2> mat(8, 8);
  
  // 返回Tensor的维度
  cout<<mat.rank()<<endl; // 2
  
  // 返回Tensor第i维元素的个数
  cout<<mat.dim(i)<<endl; // 当i=0, 输出8
  ```

* Tensor的基本信息也可通过其Tensorshape得到

  ```cpp
  Tensor<double, 2> mat(8, 8);
  TensorShape<int, 2> shape = mat.shape();
  
  // 返回Tensor的维度
  cout<<shape.rank()<<endl; // 2
  
  // 返回Tensor第i维元素的个数
  cout<<shape.dim(i)<<endl; // 当i=0, 输出8
  ```

## 改变Tensor的维度

```cpp
// 设目前有一个8*8的二维Tensor
Tensor<double,2> mat(8,8);
// 现把该Tensor改为16*16
TensorShape<int,2> shape = {16,16};
mat.resize(shape);
```

## 以数组的形式返回Tensor数据

```cpp
// 假设存在某一已初始化Tensor mat
Tensor<double,2> mat(8,8);
// 初始化
....
// 返回其数值
double* data = mat.data();
```

## Tensor的传输

```cpp
Tensor<double,2> mat(8,8);
// 将张量mat传输到device上
mat.to_device(CUDA);
// 得到张量在device上的数据
double *d_mat = mat.device_data();
// 将张量mat传回到host
mat.to_host();
```

