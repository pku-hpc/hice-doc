# SFINAE

SFINAE英文直译过来“匹配失败也不算错误”，有了前面Traits的概念就会知道，调用模板函数时编译器会根据传入参数推导最合适的模板函数，选择最合适的那一个意味其他模板匹配失败，但该匹配失败不会造成任何编译错误。

SFINAE应用最为广泛的场景是C++中的 std::enable_if。

## std::enable_if

> 定义在头文件<type_traits>中。

```c++
// 若B为true，则std::enable_if的typedef type为T
// 若B为false，则std::enable_if的typedef type为void
template< bool B, class T = void >
struct enable_if;
```

在`HICE`库中，使用`std::enable_if`主要是为了完成：

* 针对不同的device，能在不报错的情况下匹配对应的处理函数，避免出现重载二义性问题。

，举个例子：

```c++
// CPU
template< DeviceType Td, typename TScalarType,  typename TVec, typename TZeroDimTensor>
typename std::enable_if<is_same_device<Td, DeviceType::kCPU>::value, void>::type
dotvv(......){
    //......
}

// GPU kernels
template< DeviceType Td, typename TScalarType,  typename TVec, typename TZeroDimTensor>
typename std::enable_if<is_same_device<Td, DeviceType::kCUDA>::value, void>::type
dotvv(.......){
	//.......
}
```

当传入函数的`DeviceType`是`KCUDA`时，第一个函数调用`is_same_device<Td, DeviceType::kCPU>::value`返回`false`，使得`std::enable_if`没有`type`这个属性，导致匹配失败，这样使得这两个同名函数的返回值在同一个函数调用的推导过程中只有一个合法，遵循SFINAE原则，可以顺利通过编译。通过这种方式使代码看起来更统一。

这样在`apply`函数中，可以直接使用

```c++
if (lhs.device().is_cpu()) {
        engine::dotvv<DeviceType::kCPU, TScalarType3>(lhs, rhs, result);
} 
else if (lhs.device().is_cuda()) {
    engine::dotvv<DeviceType::kCUDA, TScalarType3>(lhs, rhs, result);
}
```

来调用对应的kernel。

## 参考链接

* https://zh.cppreference.com/w/cpp/language/sfinae
* https://zh.cppreference.com/w/cpp/types/enable_if

