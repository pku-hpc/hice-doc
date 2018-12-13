# Tensor

## Create Tensor

Now the tensors created are all dense.

```cpp
// Create a Tensor shape as 8*8

// Use many parameters
Tensor<double, 2> mat1(8, 8);

// Or use an array to organized the parameters
Tensor<double, 2> mat2({8,8});
```

## Initial Tensor

* Duplicate

  ```cpp
  // Suppose mat1 is existed.
  Tensor<double, 2> mat2(8,8);
  mat2 = mat1;
  ```

* Assignment

  ```cpp
  for (int row = 0; row < 8; ++row)
      for (int col = 0; col < 8; ++col)
        mat(row, col) = value;
  ```


## Access elements in Tensor

```cpp
// Similar as array
Tensor<double,2> mat(8,8);
cout<<mat(3,4)<<endl;
```

## Information of Tensor

The basic information of Tensor include `number of dims`, `number of elements in each dim`:

* Directly get the information

  ```cpp
  Tensor<double, 2> mat(8, 8);
  
  // Return the number of dims
  cout<<mat.rank()<<endl; // 2
  
  // Return the number of elements in dim i
  cout<<mat.dim(i)<<endl; 
  ```

* Use TensorShape

  ```cpp
  Tensor<double, 2> mat(8, 8);
  TensorShape<int, 2> shape = mat.shape();
  
  // Return the number of dims
  cout<<shape.rank()<<endl; // 2
  
  // Return the number of elements in dim i
  cout<<shape.dim(i)<<endl; 
  ```

## Resize

```cpp
// Suppose mat is a Tensor shape as 8*8
Tensor<double,2> mat(8,8);
// Now change the shape of mat to be 16*16
TensorShape<int,2> shape = {16,16};
mat.resize(shape);
```

## Return the data of Tensor

```cpp
Tensor<double,2> mat(8,8);
// Initial
....
// Return data
double* data = mat.data();
```

## Transfer

```cpp
Tensor<double,2> mat(8,8);
// Transfer the tensor to device
mat.to_device(CUDA);
// Get the data on device
double *d_mat = mat.device_data();
// Transfer the tensor to host
mat.to_host();
```

