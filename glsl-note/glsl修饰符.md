# glsl修饰符

## 存储修饰符

### Const

* `const`用于修饰编译时常量, 或只读函数参数

```c
const
```

### Attribute

* `attribute`用于声明共享于vertex shader和OpenGL ES环境的变量
* 由于vertex shader对于每个用于指定vertex数据的vertex属性来说只执行一次, 这些属性通常用于提供对象空间位置的数据, 方向, 以及vertex的纹理坐标. 属性都是只读变量, 它的值不能在vertex shader中改变
* 由于属性不能在shader中初始化, 所以必须在应用执行shader时加载数据

```c
attribute
```

### Uniform

* `uniform`用于声明共享于shader和OpenGL ES环境的变量
* uniform类型可用于vertex shader和fragment shader, 但必须是全局变量. 相同的uniform变量可以同时用于vertex shader和fragment shader, 但由于两种shader共享相同的命名空间, 所以变量名必须唯一. uniform类型用于指定被渲染对象的属性. 例如对象投影矩阵, 光照点, 或材质颜色. uniform变量都是只读变量, 它的值不能在shader中改变
* 由于uniform不能在shader中初始化, 所以必须在应用执行shader时加载数据

```c
uniform
```

### Varying

* `varying`用于声明共享于vertex shader和fragment shader的变量
* varying类型用于vertex shader计算后, 应该传递给fragment shader的信息. 两种shader都需要声明varying类型, 并且变量名必须唯一. vertex shader为每个vertex初始化varying. 然后varying的每个vertex数据会在点阵化过程中, 传递给fragment shader之前被插入.
* varying修饰符仅适用于浮点纯量, 浮点向量, (浮点)矩阵, 以及包含这三种类型的数组


## 精度修饰符

### High precision

* `highp`用于为变量指定最高可用精度. 变量必须为整型, 或浮点型纯量或向量, 或基于这些类型的矩阵. 精度修饰符要在变量类型之前声明.
* 在vertex shader中, 精度修饰符是可选的. 如果没有指定修饰符, 所有变量默认都是最高精度. 在fragment shader中, 当声明变量时必须使用精度修饰符, 除非该类型默认定义了精度
* 精度修饰符的实际范围依赖于OpenGL ES的实现标准. 使用更低的精度可能对性能(帧率)和节能有帮助, 但也可能导致渲染质量的降低. 只能通过测试不同精度配置来达到平衡的目的.

```c
uniform highp vec3 lightDirection;
```

### Medium precision

* `mediump`修饰符用于为变量指定介于最高和最低的可用精度. 变量必须为整型, 或浮点型纯量或向量, 或基于这些类型的矩阵. 精度修饰符要在变量类型之前声明.
* 在vertex shader中, 精度修饰符是可选的. 如果没有指定修饰符, 所有变量默认都是最高精度. 在fragment shader中, 当声明变量时必须使用精度修饰符, 除非该类型默认定义了精度
* 精度修饰符的实际范围依赖于OpenGL ES的实现标准. 使用更低的精度可能对性能(帧率)和节能有帮助, 但也可能导致渲染质量的降低. 只能通过测试不同精度配置来达到平衡的目的.

```c
varying mediump vec2 textureCoordinate;
```

### Low precision

* `lowp`修饰符用于为变量指定最低可用精度. 变量必须为整型, 或浮点型纯量或向量, 或基于这些类型的矩阵. 精度修饰符要在变量类型之前声明.
* 在vertex shader中, 精度修饰符是可选的. 如果没有指定修饰符, 所有变量默认都是最高精度. 在fragment shader中, 当声明变量时必须使用精度修饰符, 除非该类型默认定义了精度
* 精度修饰符的实际范围依赖于OpenGL ES的实现标准. 使用更低的精度可能对性能(帧率)和节能有帮助, 但也可能导致渲染质量的降低. 只能通过测试不同精度配置来达到平衡的目的.

```c
varying lowp vec4 colorVarying;
```

### Default precision

* `precision`关键字用于将精度修饰符和数据类型结合, 来为该默认数据类型指定默认的精度. 类型必须为整型, 或浮点型纯量或向量, 或基于这些类型的矩阵.
* 在vertex shader中, 精度修饰符是可选的. 如果没有指定修饰符, 所有变量默认都是最高精度. 在fragment shader中, 当声明变量时必须使用精度修饰符, 除非该类型默认定义了精度
* 精度修饰符的实际范围依赖于OpenGL ES的实现标准. 使用更低的精度可能对性能(帧率)和节能有帮助, 但也可能导致渲染质量的降低. 只能通过测试不同精度配置来达到平衡的目的.

```c
precision highp float;
```


## 参数修饰符

### Input修饰符

* `in`修饰符用于在声明函数时将参数标记为只读. 参数会通过值传递给函数, 值不允许被函数修改

```c
int newFunction(in bvec4 aBvec4,   // read-only
                out vec3 aVec3,    // write-only
                inout int aInt);   // read-write
```

### Output修饰符

* `out`修饰符用于在声明函数时将参数标记为只读. 参数会通过引用传递给函数, 但其并没有被初始化, 例如, 值无法读取. 值可以被函数修改, 且在函数执行完毕后修改依然有效

```c
int newFunction(in bvec4 aBvec4,   // read-only
                out vec3 aVec3,    // write-only
                inout int aInt);   // read-write
```

### Input-output修饰符

* `inout`修饰符用于在声明函数时将参数标记为只读. 参数会通过引用传递给函数, 但其并没有被初始化, 例如, 值无法读取. 值可以被函数修改, 且在函数执行完毕后修改依然有效

```c
int newFunction(in bvec4 aBvec4,   // read-only
                out vec3 aVec3,    // write-only
                inout int aInt);   // read-write
```
