# 下载与安装

> 按理说这里应该包括mac, linux, windows三种操作平台的安装方式。

## 从源码安装

### 克隆HICE仓库

```shell
git clone https://github.com/pku-hpc/hice.git
```

### 编译

* 进入程序目录并新建`build`文件夹

  ```shell
  cd hice
  mkdir build
  ```

* 进入`build`文件夹并编译

  ```shell
  cd build
  cmake ..
  make
  ```

## 测试

* 将根目录下的`CMakeList.txt`中的测试选项设置为`ON`。

  ```
  option(ENABLE_TESTING "ENABLE tests" ON)
  ```

* 按以上步骤编译后，执行`build`目录下生成可执行的测试程序。

  ```shell
  ./dot_cpu_test
  ```

###可选: 支持GPU

* 为了编译并运行能够使用 GPU 的HICE，需要先安装 NVIDIA 提供的 Cuda。并将根目录下的`CMakeList.txt`中的`CUDA`选项设置为`ON`。

  ```
  option(USE_CUDA "Use CUDA" ON)
  ```

* 较为重要的是，不同GPU计算能力不同，需根据硬件设置根目录下`CMakeList.txt`中的编译参数：

  ```
  set(CMAKE_CUDA_FLAGS "--generate-code arch=compute_60,code=sm_60 -Xcompiler=-Wall")
  ```