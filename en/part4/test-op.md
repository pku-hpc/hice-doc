# Test operations

Add new test code under `test/`, the test code should include `hice.h`. After that the compile command for the test file should be added in `CMakeLists.txt` under the same directory. For example:

```
# dot_cpu_test is a execuation program
# dot_cpu_test.cpp is the source code
add_executable(dot_cpu_test dot_cpu_test.cpp)
target_link_libraries(dot_cpu_test hice)
add_test(
  NAME dot_cpu_test
  COMMAND $<TARGET_FILE:dot_cpu_test>
)
```

Finally rebuild the whole program.