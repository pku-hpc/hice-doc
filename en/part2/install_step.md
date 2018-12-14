# Download and Install

## Build from source

### Download the HICE source code

```shell
git clone https://github.com/pku-hpc/hice.git
```

### Compile

* New a directory named `build` in hice.

  ```shell
  cd hice
  mkdir build
  ```

* Compile in `build`

  ```shell
  cd build
  cmake ..
  make
  make install
  ```

## Test

* Turn on the test option in  `CMakeList.txt`.

  ```
  option(ENABLE_TESTING "ENABLE tests" ON)
  ```

* Recompile the program, and the execution test program is under `build`.

  ```shell
  ./dot_cpu_test
  ```

###Optional: GPU Support

* Inorder to use GPU in HICE, CUDA should be preinstalled. Turn on the cuda option in  `CMakeList.txt`.

  ```
  option(USE_CUDA "Use CUDA" ON)
  ```

* It's important to set the compile parameter in `CMakeList.txt`, which should be consistent with your GPU.

  ```
  set(CMAKE_CUDA_FLAGS "--generate-code arch=compute_60,code=sm_60 -Xcompiler=-Wall")
  ```