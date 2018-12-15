# Expression

## Lazy Evaluation (feature)

```cpp
// eg.2-1：will not be evaluated
tensor_a + tensor_b;

// eg.2-2：evaluation touched off by '='(assignment)
result = tensor_a + tensor_b;
```

For every expression, a grammer tree will be constructed and the process of evaluation will be touched off by '='. In eg.2-1, a grammer tree is created, but not evaluated. In eg.2-2, a grammer tree is created as well as evaluated, and the result  is stored into 'result'.

PS: You should read the introduction carefully before using any operator.



## Compound expression

```cpp
// eg.1-1：simple expression
temp = tensor_b / tensor_c;
result = tensor_a + temp;

// eg.1-2：compound expression
result = tensor_a + tensor_b / tensor_c;

// eg.1-3：compound expression
(result = tensor_d) = tensor_a; // wrong, not work
```

The results of eg.1-1 and eg.1-2 are equivalent. In compound expression, the basic operators precedence of tensor is same with that of real number.

At the left side of the '='(assignment), it cannot be another expression.(as it shown in eg.1-3)



## Evaluating Environment

The expression can be evaluated on CPU or GPU. Two enumeration values, 'CPU' and 'CUDA', are pre-defined in Hice to help you can specify the evaluating environment explicitly, as shown in eg.3-1 and eg.3-2. 

It is necessary to mention that, when you specify the evaluating environment explicitly, all device info of tensors in the right side of '=' will be changed .

```cpp
// eg.3-1
result = (tensor_a + tensor_b).to(CPU);	// the device info of tensor_a and tensor_b is set to 'CPU', and then evaluated on CPU.

// eg.3-2
result = (tensor_a + tensor_b).to(CUDA);// the device info of tensor_a and tensor_b is set to 'CUDA', and then evaluated on GPU.
```

If the evaluating environment is not specify explicitly, the evaluation will be processed on CPU by default. But sometimes it not works, so it is always a good habit to specify the evaluating environment explicitly.