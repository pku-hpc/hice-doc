# Traits

> Traits，可以解释为特征萃取技术，即提取被传入对象对应的返回类型。

在`HICE`库中，主要利用`Traits`正确匹配传入的`Expr`中各参数类型，用一元操作举个例子来说：

```c++
// UnaryExpr
template<typename TExpr, typename TUnaryOp>
struct Traits<UnaryExpr<TExpr, TUnaryOp>> {
  static const int kDim = Traits<TExpr>::kDim;
  static const StorageType kSType = Traits<TExpr>::kSType;
  typedef typename Traits<TExpr>::ScalarType ScalarType;
  typedef typename Traits<TExpr>::IndexType IndexType;
  typedef typename Traits<TExpr>::ShapeType ShapeType;
  typedef typename Traits<TExpr>::ResultType ResultType;
};

template<typename TScalarType, int ndim, typename TIndexType, 
         StorageType stype>
struct Traits<Tensor<TScalarType, ndim, TIndexType, stype>> {
  static const int kDim = ndim;
  static const StorageType kSType = stype;
  typedef TIndexType IndexType;
  typedef TScalarType ScalarType;
  typedef TensorShape<IndexType, kDim> ShapeType;
  typedef Tensor<ScalarType, kDim, IndexType, stype> ResultType;
};
```

一元操作只有一个操作数（程序中默认为Tensor），使用时只需要将一元操作的表达式传入`Traits`，程序会自动匹配调用第一个`struct`，并在第一个`struct`中递归匹配调用第二个`struct`，最终得到`Tensor`中存储元素的信息。

所以在自定义新增`operation`时，也需要有一个对应该`operation expression` 的`Traits`结构体，用于获取并返回该`operation`内`Tensor`操作数的各个参数类型，不过需要注意的是，像`Traits`匹配并获取某个`Tensor`内元素类型的操作在`src/core/expression_traits`中已定义，所以实际上是不需要重复定义的，也就省略了上边例子中第二个`struct Traits`的定义。

## 参考链接

https://www.cnblogs.com/mangoyuan/p/6446046.html

