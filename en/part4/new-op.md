# Add operations

The basic operations of tensor，like `dot`，`transpose` are under `la`.Machine learning algorithms，like `knn`，`svm` are under `ml`. Convolution operations are under `nn`。

Five steps while coding：

- Add the kernel in the `namespace` of `engine`, if the operation need to support `cuda`, use `enable_if` to do auto selection.
- Add the struct of new operation in the `namespace` of `op`, there should have an `apply` function in struct to select proper `kernel`, see more [here](../part5/SFINAE.md).
- Add expression template for the new operation, see more [here](../part5/Traits.md).
- Add  `evaluator` for the new expression template.

Finally `include` the header of operation in `src/hice.h`.