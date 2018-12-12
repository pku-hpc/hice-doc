# 测试自定义的operation

在`test/`目录下新增测试代码，测试代码引入`#include "hice.h"`后编写测试用例，并在同目录下的`CMakeLists.txt`中增加对该测试文件的编译，示例如下：

```
# dot_cpu_test为生成的测试可执行程序
# dot_cpu_test.cpp为测试源代码
add_executable(dot_cpu_test dot_cpu_test.cpp)
target_link_libraries(dot_cpu_test hice)
add_test(
  NAME dot_cpu_test
  COMMAND $<TARGET_FILE:dot_cpu_test>
)
```

完成以上操作，在`build/`目录下重新`cmake && make`即可。