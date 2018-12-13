# Traits

> Traits gives us additional information other than just the type.

We use `Traits` to match the correct parameters type of `Expr` in HICE. Use the unary operation for example:  

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

The unary expression will auto match the first struct and invoke the second struct to get the type of operand for further usage.

## Reference

https://www.cnblogs.com/mangoyuan/p/6446046.html

