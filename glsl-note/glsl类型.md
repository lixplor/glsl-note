# OpenGL ES 着色器语言类型

[reference](http://www.shaderific.com/glsl-types)

## 纯量类型

### 空类型

* `void`数据类型用于无参数函数或没有返回值的函数

```c
void main(void);
int aFunction(void);
void bFunction(float);
```

### 布尔类型

* `bool`数据类型用于布尔值
* 不支持隐式类型转换, 可使用第二, 三示例显式转换

```c
bool aBool = true;
bool bBool = bool(aInt);
bool cBool = bool(aFloat);
```

### 整型

* `int`数据类型用于整数值
* 不支持隐式类型转换, 可使用第二, 三示例显式转换

```c
int aInt = 42;
int bInt = int(aBool);
int cInt = int(aFloat);
```

### 浮点类型

* `float`数据类型用于浮点数值
* 不支持隐式类型转换, 可使用第二, 三示例显式转换

```c
float aFloat = 1.0;
float bFloat = float(aBool);
float cFloat = float(aInt);
```


## 向量类型

### 二分量布尔向量

* `bvec2`数据类型用于二分量布尔向量
* 多种初始化方法:
    - 为每个分量分别指定一个纯量值
    - 为每个分量指定同一个纯量值
    - 为每个分量指定更高维度的矢量, 对应的值用于分量初始化
* 向量构造器可以转换不同的矢量类型, 其内部会自动为每个分量进行类型转换

```c
bvec2 aBvec2 = bvec2(true, true);
bvec2 bBvec2 = bvec2(true);

bvec2 vBvec2 = bvec2(aBvec3);
bvec2 dBvec2 = bvec2(aBvec3.x, aBvec3.y);
```

### 三分量布尔向量

* `bvec3`数据类型用于三分量布尔向量
* 多种初始化方法:
    - 为每个分量分别指定一个纯量值
    - 为每个分量指定同一个纯量值
    - 为每个分量指定更高维度的矢量, 对应的值用于分量初始化
    - 为每个分量指定向量和纯量的组合, 对应的值用于分量初始化
* 向量构造器可以转换不同的矢量类型, 其内部会自动为每个分量进行类型转换

```c
vec3 aBvec3 = bvec3(true, true, true);
vec3 bBvec3 = bvec3(true);

vec3 cBvec3 = bvec3(aBvec4);
vec3 dBvec3 = bvec3(aBvec4.x, aBvec4.y, aBvec4.z);

vec3 eBvec3 = bvec3(aBvec2, aBool);
vec3 fBvec3 = bvec3(aBvec2.x, aBvec2.y, aBool);
```

### 四分量布尔向量

* `bvec4`数据类型用于四分量布尔向量
* 多种初始化方法:
    - 为每个分量分别指定一个纯量值
    - 为每个分量指定同一个纯量值
    - 为每个分量指定向量和纯量的组合, 对应的值用于分量初始化, 参数分量数不能少于构造类型的分量数
* 向量构造器可以转换不同的矢量类型, 其内部会自动为每个分量进行类型转换

```c
vec4 aBvec4 = bvec4(true, true, true, true);
vec4 bBvec4 = bvec4(true);

vec4 cBvec4 = bvec4(aBvec2, aBool, aBvec3);
vec4 dBvec4 = bvec4(aBvec2.x, aBvec2.y, aBool, aBvec3.x);
```

### 二分量整型向量

* `ivec2`用于二分量整型向量
* 多种初始化方法:
    - 为每个分量分别指定一个纯量值
    - 为每个分量指定同一个纯量值
    - 为每个分量指定更高维度的矢量, 对应的值用于分量初始化
* 向量构造器可以转换不同的矢量类型, 其内部会自动为每个分量进行类型转换

```c
ivec2 aIvec2 = ivec2(1, 1);
ivec2 bIvec2 = ivec2(1);

ivec2 cIvec2 = ivec2(aIvec3);
ivec2 dIvec2 = ivec2(aIvec3.x, aIvec3.y);
```

### 三分量整型向量

* `ivec3`用于二分量整型向量
* 多种初始化方法:
    - 为每个分量分别指定一个纯量值
    - 为每个分量指定同一个纯量值
    - 为每个分量指定更高维度的矢量, 对应的值用于分量初始化
    - 为每个分量指定向量和纯量的组合, 对应的值用于分量初始化
* 向量构造器可以转换不同的矢量类型, 其内部会自动为每个分量进行类型转换

```c
ivec3 aIvec3 = ivec3(1, 1, 1);
ivec3 bIvec3 = ivec3(1);

ivec3 cIvec3 = ivec3(aIvec4);
ivec3 dIvec3 = ivec3(aIvec4.x, aIvec4.y, aIvec4.z);

ivec3 eIvec3 = ivec3(aIvec2, aInt);
ivec3 fIvec3 = ivec3(aIvec2.x, aIvec2.y, aInt);
```

### 四分量整型向量

* `ivec4`数据类型用于四分量布尔向量
* 多种初始化方法:
    - 为每个分量分别指定一个纯量值
    - 为每个分量指定同一个纯量值
    - 为每个分量指定向量和纯量的组合, 对应的值用于分量初始化, 参数分量数不能少于构造类型的分量数
* 向量构造器可以转换不同的矢量类型, 其内部会自动为每个分量进行类型转换

```c
ivec4 aIvec4 = ivec4(1, 1, 1, 1);
ivec4 bIvec4 = ivec4(1);

ivec4 cIvec4 = ivec4(aIvec2, aInteger, aIvec3);
ivec4 dIvec4 = ivec4(aIvec2.x, aIvec2.y, aInt, aIvec3.x);
```

### 二分量浮点向量

* `vec2`用于二分量整型向量
* 多种初始化方法:
    - 为每个分量分别指定一个纯量值
    - 为每个分量指定同一个纯量值
    - 为每个分量指定更高维度的矢量, 对应的值用于分量初始化
* 向量构造器可以转换不同的矢量类型, 其内部会自动为每个分量进行类型转换

```c
vec2 aVec2 = vec2(1.0, 1.0);
vec2 bVec2 = vec2(1.0);

vec2 cVec2 = vec2(aVec3);
vec2 dVec2 = vec2(aVec3.x, aVec3.y);
```

### 三分量浮点向量

* `vec3`用于二分量整型向量
* 多种初始化方法:
    - 为每个分量分别指定一个纯量值
    - 为每个分量指定同一个纯量值
    - 为每个分量指定更高维度的矢量, 对应的值用于分量初始化
    - 为每个分量指定向量和纯量的组合, 对应的值用于分量初始化
* 向量构造器可以转换不同的矢量类型, 其内部会自动为每个分量进行类型转换

```c
vec3 aVec3 = vec3(1.0, 1.0, 1.0);
vec3 bVec3 = vec3(1.0);

vec3 cVec3 = vec3(aVec4);
vec3 dVec3 = vec3(aVec4.x, aVec4.y, aVec4.z);

vec3 eVec3 = vec3(aVec2, aFloat);
vec3 fVec3 = vec3(aVec2.x, aVec2.y, aFloat);
```

### 四分量浮点向量

* `vec4`数据类型用于四分量布尔向量
* 多种初始化方法:
    - 为每个分量分别指定一个纯量值
    - 为每个分量指定同一个纯量值
    - 为每个分量指定向量和纯量的组合, 对应的值用于分量初始化, 参数分量数不能少于构造类型的分量数
* 向量构造器可以转换不同的矢量类型, 其内部会自动为每个分量进行类型转换

```c
vec4 aVec4 = vec4(1.0, 1.0, 1.0, 1.0);
vec4 bVec4 = vec4(1.0);

vec4 cVec4 = vec4(aVec2, aFloat, aVec3);
vec4 dVec4 = vec4(aVec2.x, aVec2.y, aFloat, aVec3.x);
```


## 矩阵类型

### 2x2浮点矩阵

* `mat2`数据类型用于二阶二分量列序浮点矩阵
* 多种初始化方法:
    - 为每个分量分别指定一个纯量值. 矩阵按列填充
    - 为每个分量指定同一个纯量值, 该值用于分量的主对角线
    - 为每个分量指定向量和纯量的组合, 对应的值按列应用于分量初始化, 参数分量数不能少于构造类型的分量数
* 矩阵的值可以按分量方向或按列获取

```c
mat2 aMat2 = mat2(1.0, 0.0,  // 1. column
                  0.0, 1.0); // 2. column
mat2 bMat2 = mat2(1.0);

mat2 cMat2 = mat2(aVec2, bVec2);
mat2 dMat2 = mat2(aVec3, aFloat);

// 设置获取矩阵的值
mat2 aMat2;
aMat2[1][1] = 1.0;           // 为右下角设置值
float aFloat = aMat2[1][1];  // 获取右下角的值

aMat2[0] = vec2(1.0);        // 设置矩阵第一列向量为一个向量
vec2 aVec2 = aMat2[0];       // 获取矩阵第一列向量
```

### 3x3浮点矩阵

* `mat3`数据类型用于三阶三分量列序浮点矩阵
* 多种初始化方法:
    - 为每个分量分别指定一个纯量值. 矩阵按列填充
    - 为每个分量指定同一个纯量值, 该值用于分量的主对角线
    - 为每个分量指定向量和纯量的组合, 对应的值按列应用于分量初始化, 参数分量数不能少于构造类型的分量数
* 矩阵的值可以按分量方向或按列获取

```c
mat3 aMat3 = mat3(1.0, 0.0, 0.0,  // 1. column
                  0.0, 1.0, 0.0,  // 2. column
                  0.0, 0.0, 1.0); // 3. column
mat3 bMat3 = mat3(1.0);

mat3 cMat3 = mat3(aVec3, bVec3, cVec3);
mat3 dMat3 = mat3(aVec4, aVec3, bVec4, aFloat);

// 设置获取矩阵的值
mat3 aMat3;
aMat3[2][2] = 1.0;                // 为矩阵右下角设置值
float aFloat = aMat3[2][2];       // 获取矩阵右下角的值

aMat3[0] = vec3(1.0);             // 设置矩阵第一列向量为一个向量
vec3 aVec3 = aMat3[0];            // 获取矩阵第一列向量
```

### 4x4浮点矩阵

* `mat4`数据类型用于四阶四分量列序浮点矩阵
* 多种初始化方法:
    - 为每个分量分别指定一个纯量值. 矩阵按列填充
    - 为每个分量指定同一个纯量值, 该值用于分量的主对角线
    - 为每个分量指定向量和纯量的组合, 对应的值按列应用于分量初始化, 参数分量数不能少于构造类型的分量数
* 矩阵的值可以按分量方向或按列获取

```c
mat4 aMat4 = mat4(1.0, 0.0, 0.0, 0.0,  // 1. column
                  0.0, 1.0, 0.0, 0.0,  // 2. column
                  0.0, 0.0, 1.0, 0.0,  // 3. column
                  0.0, 0.0, 0.0, 1.0); // 4. column
mat4 bMat4 = mat4(1.0);

mat4 cMat4 = mat4(aVec4, bVec4, cVec4, dVec4);
mat4 dMat4 = mat4(aVec4, aVec3, bVec4, cVec4, aFloat);

// 设置获取矩阵的值
aMat4[3][3] = 1.0;
float aFloat = aMat4[3][3];

aMat4[0] = vec4(1.0);
vec4 aVec4 = aMat4[0];
```

## 纹理类型

### 2D纹理

* `sampler2D`数据类型用于访问2D纹理. 它必须被声明为`uniform`变量, 这是因为它被作为一个数据引用加载到一个数据单元中
* 在iOS设备上, 该类型只能用于fragment shader, 这是因为iOS设备没有纹理图片单元可供vertex shader访问

```c
uniform sampler2D texture;
```

### 立方体纹理

* `samplerCube`数据类型用于访问立方体纹理. 它必须被声明为`uniform`变量, 这是因为它被作为一个数据引用加载到一个数据单元中
* 在iOS设备上, 该类型只能用于fragment shader, 这是因为iOS设备没有纹理图片单元可供vertex shader访问

```c
uniform samplerCube texture;
```

## 结构体和数组

### 结构体

* `struct`用于声明基于基本类型的自定义数据结构体. 一个同名的构造器会被自动创建. 变量名声明是可选的
* 结构体的成员和构造器的参数必须一致
* 结构体的成员可以使用`.`点操作符访问

```c
struct matStruct {
    vec4 ambientColor;
    vec4 diffuseColor;
    vec4 specularColor;
    float specularExponent;
} newMaterial;

newMaterial = matStruct(vec4(0.1, 0.1, 0.1, 1.0),
                        vec4(1.0, 0.0, 0.0, 1.0),
                        vec4(0.7, 0.7, 0.7, 1.0),
                        50.0);

vec4 ambientColor = newMaterial.ambientColor;
vec4 diffuseColor = newMaterial.diffuseColor;
vec4 specularColor = newMaterial.specularColor;
float specularExponent = newMaterial.specularExponent;
```

### 数组

* `array`数据类型用于声明基于基本类型的自定义数组.
* 有以下规则:
    - 数组可以包含所有基本类型, 也可以包含结构体
    - 数组不能在声明时初始化
    - 数组元素必须依次初始化
* 数组的元素使用对应元素的索引进行初始化和访问
* iOS设备上不可以使用变量索引访问数组元素, 索引值必须在编译时期是一个常量

```c
int newIntArray[9];
vec3 newVec3Array[3];

newIntArray[0] = 5;
newVec3Array[1] = vec3(1.0, 1.0, 1.0);

int newInt = newIntArray[0];
vec3 newVec3 = newVec3Array[1];
```
