# SFINAE

When substituting the explicitly specified or deduced type for the template parameter fails, the specialization is discarded from the overload set instead of causing a compile error.

The most popular usage of SFINAE in C++ is std::enable_if

## std::enable_if

> Define in  `type_traits` 

```cpp
// If B is true，the typedef type of std::enable_if is T
// If B is false，the typedef type of std::enable_if is void
template< bool B, class T = void >
struct enable_if;
```

`std::endable_if` in HICE is mainly for:

* Invoke the right function for different devices.

Example：

```cpp
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

While the parameter `DeviceType` is `KCUDA`, the first function invoke `is_same_device<Td, DeviceType::kCPU>::value` and return `false`, so `std::enable_if` won't have `type` attribute. So there will be only one function legal, this will make the code may clear.

While in `apply`, We can directly use:

```c++
if (lhs.device().is_cpu()) {
        engine::dotvv<DeviceType::kCPU, TScalarType3>(lhs, rhs, result);
} 
else if (lhs.device().is_cuda()) {
    engine::dotvv<DeviceType::kCUDA, TScalarType3>(lhs, rhs, result);
}
```

to invoke kernel.

## Reference

* https://zh.cppreference.com/w/cpp/language/sfinae
* https://zh.cppreference.com/w/cpp/types/enable_if

