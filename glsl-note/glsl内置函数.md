# 内置函数

## 角和三角函数

### radians

```c
float radians(float degrees);
vec2 radians(vec2 degrees);
vec3 radians(vec3 degrees);
vec4 radians(vec4 degrees);
```

* `radians`函数用于将角度转为弧度. 输入的参数可以是浮点纯量或浮点向量. 如果是浮点向量的话, 所有component都会单独从角度转换为弧度

### degrees

```c
float degrees(float radians);
vec2 degrees(vec2 radians);
vec3 degrees(vec3 radians);  
vec4 degrees(vec4 radians);
```

* `degrees`函数用于将弧度转为角度. 输入的参数可以是浮点纯量或浮点向量. 如果是浮点向量的话, 所有component都会单独从弧度转换为角度

### sine

```c
float sin(float angle);
vec2 sin(vec2 angle);
vec3 sin(vec3 angle);
vec4 sin(vec4 angle);
```

* `sin`函数返回一个角的弧度的正弦值. 输入的参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则每个component都会单独计算正弦值

### cosine

```c
float cos(float angle);
vec2 cos(vec2 angle);
vec3 cos(vec3 angle);
vec4 cos(vec4 angle);
```

* `cos`函数返回一个角的弧度的余弦值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则每个component都会单独计算余弦值

### tangent

```c
float tan(float angle)  
vec2 tan(vec2 angle)  
vec3 tan(vec3 angle)  
vec4 tan(vec4 angle)
```

* `tan`函数返回一个角的弧度的正切值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则每个component都会单独计算正切值

### arcsine

```c
float asin(float x);
vec2 asin(vec2 x);
vec3 asin(vec3 x);
vec4 asin(vec4 x);
```

* `asin`函数返回一个角的弧度的反正弦值. 是正切函数的相反. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则每个component会单独计算反正弦值

### arccosine

```c
float acos(float x)  
vec2 acos(vec2 x)  
vec3 acos(vec3 x)  
vec4 acos(vec4 x)
```

* `acos`函数返回一个角的弧度的反余弦值. 是余弦函数的反函数. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则每个component会单独计算反余弦值

### arctangent

```c
float atan(float y_over_x)  
vec2 atan(vec2 y_over_x)  
vec3 atan(vec3 y_over_x)  
vec4 atan(vec4 y_over_x)

float atan(float y, float x)  
vec2 atan(vec2 y, vec2 x)  
vec3 atan(vec3 y, vec3 x)  
vec4 atan(vec4 y, vec4 x)
```

* `atan`函数返回一个角的弧度的反正切值. 是正切函数的反函数. 输入参数可以是浮点纯 量或浮点向量. 如果是浮点向量, 则每个component会单独计算反正切值
* `atan`函数还有两个参数的函数. 在笛卡尔坐标系(x, y)中该函数返回与极坐标(r, θ)相同的点角θ


## 指数函数

### 指数函数

```c
float pow(float x, float y)  
vec2 pow(vec2 x, vec2 y)  
vec3 pow(vec3 x, vec3 y)  
vec4 pow(vec4 x, vec4 y)
```

* `power`函数返回x的y次幂的值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照分量方向进行运算

## 自然指数函数

```c
float exp(float x)  
vec2 exp(vec2 x)  
vec3 exp(vec3 x)  
vec4 exp(vec4 x)
```

* `exp`函数返回常量e的x次幂的值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照分量方向进行运算 

### 对数

```c
float log(float x)  
vec2 log(vec2 x)  
vec3 log(vec3 x)  
vec4 log(vec4 x)
```

* `log`函数返回以e为底x的对数. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照分量方向进行运算

### 自然指数函数2

```c
float exp2(float x)  
vec2 exp2(vec2 x)  
vec3 exp2(vec3 x)  
vec4 exp2(vec4 x)
```

* `exp2`函数返回2的x次幂的值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照分量方向进行运算

### 对数函数2

```c
float log2(float x)  
vec2 log2(vec2 x)  
vec3 log2(vec3 x)  
vec4 log2(vec4 x)
```

* `log2`函数返回以2为底x的对数. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照分量方向进行运算

### 平方根

```cpp
float sqrt(float x)  
vec2 sqrt(vec2 x)  
vec3 sqrt(vec3 x)  
vec4 sqrt(vec4 x)
```

* `sqrt`函数返回x的平方根. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照分量方向进行运算

### 平方根倒数

```cpp
float inversesqrt(float x)  
vec2 inversesqrt(vec2 x)  
vec3 inversesqrt(vec3 x)  
vec4 inversesqrt(vec4 x)
```

* `inversesqrt`函数返回x的平方根倒数. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照分量方向进行运算


## 通用函数

### 绝对值

```cpp
float abs(float x)  
vec2 abs(vec2 x)  
vec3 abs(vec3 x)  
vec4 abs(vec4 x)
```

* `abs`函数返回x的绝对值. 输入参数可以是浮点纯量或浮点向量. 如果是浮>点向量, 则按照分量方向进行运算

### sign

```cpp
float sign(float x)  
vec2 sign(vec2 x)  
vec3 sign(vec3 x)  
vec4 sign(vec4 x)
```

* `sign`函数在当x为正数时返回1.0, 当x是0时返回0.0, 当x为负数时返回-1.0. 输入参数可以是浮点纯量或浮点向量. 如果是浮>点向量, 则按照分量方向进行运算

### 向下取整

```cpp
float floor(float x)  
vec2 floor(vec2 x)  
vec3 floor(vec3 x)  
vec4 floor(vec4 x)
```

* `floor`函数进行向下取整并返回该整数. 输入参数可以是浮点纯量或浮点向量. 如果是浮>点向量, 则按照分量方向进行运算
* 注意: 即使运算的是整数, 返回值也会是浮点纯量或浮点向量

### 向上取整

```cpp
float ceil(float x)  
vec2 ceil(vec2 x)  
vec3 ceil(vec3 x)  
vec4 ceil(vec4 x)
```

* `ceiling`函数进行向上取整并返回该整数. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照分量方向进行运算
* 注意: 即使运算的是整数, 返回值也会是浮点纯量或浮点向量

### 取余

```cpp
float fract(float x)  
vec2 fract(vec2 x)  
vec3 fract(vec3 x)  
vec4 fract(vec4 x)
```

* `fract`函数返回x的小数部分. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按分量方向进行运算

### 取模

```cpp
float mod(float x, float y)  
vec2 mod(vec2 x, vec2 y)  
vec3 mod(vec3 x, vec3 y)  
vec4 mod(vec4 x, vec4 y)

float mod(float x, float y)  
vec2 mod(vec2 x, float y)  
vec3 mod(vec3 x, float y)  
vec4 mod(vec4 x, float y)
```

* `mod`函数返回x模于y的值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照分量方向进行运算
* 此外`mod`还有带有2个参数的函数, 第二个参数是浮点纯量

### 最小值

```cpp
float min(float x, float y)  
vec2 min(vec2 x, vec2 y)  
vec3 min(vec3 x, vec3 y)  
vec4 min(vec4 x, vec4 y)

float min(float x, float y)  
vec2 min(vec2 x, float y)  
vec3 min(vec3 x, float y)  
vec4 min(vec4 x, float y)
```

* `min`函数返回两个参数的最小值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照分量方向进行运算
* 此外`min`函数还有第二个参数是浮点纯量的函数

### 最大值

```cpp
float max(float x, float y)  
vec2 max(vec2 x, vec2 y)  
vec3 max(vec3 x, vec3 y)  
vec4 max(vec4 x, vec4 y)

float max(float x, float y)  
vec2 max(vec2 x, float y)  
vec3 max(vec3 x, float y)  
vec4 max(vec4 x, float y)
```

* `max`函数返回两个参数的最大值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量
, 则按照分量方向进行运算
* 此外`max`函数还有第二个参数是浮点纯量的函数

### clamp

```cpp
float clamp(float x, float minVal, float maxVal)  
vec2 clamp(vec2 x, vec2 minVal, vec2 maxVal)  
vec3 clamp(vec3 x, vec3 minVal, vec3 maxVal)  
vec4 clamp(vec4 x, vec4 minVal, vec4 maxVal)

float clamp(float x, float minVal, float maxVal)  
vec2 clamp(vec2 x, float minVal, float maxVal)  
vec3 clamp(vec3 x, float minVal, float maxVal)  
vec4 clamp(vec4 x, flfloat minVal, float maxVal)
```

* `clamp`函数在当x大于minVal并且小于maxVal时返回x, 当x小于minVal时返回minVal, 当x大于maxVal时返回maxVal. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照分量方向进行运算
* 此外`clamp`函数还有第二个和第三个参数是浮点纯量的函数

### mix

```cpp
float mix(float x, float y, float a)  
vec2 mix(vec2 x, vec2 y, vec2 a)  
vec3 mix(vec3 x, vec3 y, vec3 a)  
vec4 mix(vec4 x, vec4 y, vec4 a)

float mix(float x, float y, float a)  
vec2 mix(vec2 x, vec2 y, float a)  
vec3 mix(vec3 x, vec3 y, float a)  
vec4 mix(vec4 x, vec4 y, float a)
```

* `mix`函数返回x和y的线性混合, 例如x * ((1-a) + (y * a)). 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照分量方向进行运算
* 此外`mix`函数还有第三个参数是浮点纯量的函数

## step

```cpp
float step(float edge, float x)  
vec2 step(vec2 edge, vec2 x)  
vec3 step(vec3 edge, vec3 x)  
vec4 step(vec4 edge, vec4 x)

float step(float edge, float x)  
vec2 step(float edge, vec2 x)  
vec3 step(float edge, vec3 x)  
vec4 step(float edge, vec4 x)
```

* `step`函数在当x小于edge时返回0.0, 否则返回1.0. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照分量方向进行运算
* 此外`step`函数还有edge参数是浮点纯量的函数

### smoothstep

```cpp
float smoothstep(float edge0, float edge1, float x)  
vec2 smoothstep(vec2 edge0, vec2 edge1, vec2 x)  
vec3 smoothstep(vec3 edge0, vec3 edge1, vec3 x)  
vec4 smoothstep(vec4 edge0, vec4 edge1, vec4 x)

float smoothstep(float edge0, float edge1, float x)  
vec2 smoothstep(float edge0, float edge1, vec2 x)  
vec3 smoothstep(float edge0, float edge1, vec3 x)  
vec4 smoothstep(float edge0, float edge1, vec4 x)
```

* `smoothstep`函数在当x小于edge0时返回0.0, 当x大于edge1时返回1.0, 否则返回使用厄尔米多项式(Hermite polynomials)插值的介于0.0到1.0之间的值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照分量方向进行运算
* 此外`smoothstep`函数还有edge0和edge1参数是浮点纯量的函数


## 几何函数

### 长度

```cpp
float length(float x)  
float length(vec2 x)  
float length(vec3 x)  
float length(vec4 x)
```

* `length`函数返回欧几里德范数(Euclidean norm)定义的向量长度, 即分量平方和的平方根(the square root of the sum of the squared components). 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则该函数是平凡的(trivial)并返回绝对值

### 距离

```cpp
float distance(float p0, float p1)  
float distance(vec2 p0, vec2 p1)  
float distance(vec3 p0, vec3 p1)  
float distance(vec4 p0, vec4 p1)
```

* `distance`函数返回两点之间的距离. 两点之间的距离就是向量的长度d = p0 - p1, 从p1开始, 指向p0. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则该函数是平凡的(trivial)并返回d的绝对值

### 点积

```cpp
float dot(float x, float y)  
float dot(vec2 x, vec2 y)  
float dot(vec3 x, vec3 y)  
float dot(vec4 x, vec4 y)
```

* `dot`函数返回两个输入参数的点积, 即分量乘积的和. 如果x和y相同, 那么点积的平方根等于向量的长度. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则该函数是平凡的, 并返回x和y的乘积

### 叉积

```cpp
vec3 cross(vec3 x, vec3 y)
```

* `cross`函数返回两个输入参数的叉积, 即两个叉乘向量共起点时, 所构成平行四边形的面积. 输入参数只能是3分量浮点向量. 叉积等于向量长度乘以x与y之间的弧(sinus)的积

### 归一化函数

```cpp
float normalize(float x)  
vec2 normalize(vec2 x)  
vec3 normalize(vec3 x)  
vec4 normalize(vec4 x)
```

* `normalize`函数返回一个平行于x的长度为1.0的向量, 即x除以它的长度. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 该函数是平凡的, 且返回1.0

### faceforward

```cpp
float faceforward(float N, float I, float Nref)  
vec2 faceforward(vec2 N, vec2 I, vec2 Nref)  
vec3 faceforward(vec3 N, vec3 I, vec3 Nref)  
vec4 faceforward(vec4 N, vec4 I, vec4 Nref)
```

* `faceforward`函数返回一个与参考向量指向相同的向量. 该函数有三个浮点纯量或浮点向量的输入参数: N, 即朝向的向量; I, 即关联向量; Nref, 即参考向量. 如果I和Nref的点积小于0, 则返回值是N, 否则返回-N

### 反射

```cpp
float reflect(float I, float N)  
vec2 reflect(vec2 I, vec2 N)  
vec3 reflect(vec3 I, vec3 N)  
vec4 reflect(vec4 I, vec4 N)
```

* `reflect`函数返回一个指向反射方向的向量. 该函数有两个浮点纯量或浮点向量类型的输入参数: I, 即关联向量; N, 即反射面的法向量(normal vector)
* 注意: 要获取期望的结果, 向量N必须归一化. 反射向量总是与关联向量拥有相同的长度. 由此得出若N和I都是归一化的, 则反射向量也是归一化的

### refract

```cpp
float refract(float I, float N, float eta)  
vec2 refract(vec2 I, vec2 N, float eta)  
vec3 refract(vec3 I, vec3 N, float eta)  
vec4 refract(vec4 I, vec4 N, float eta)
```

* `refract`函数返回一个指向refraction方向的向量. 该函数有两个浮点纯量或浮点向量类型的输入参数, 以及一个浮点纯量类型的输入参数: I, 即关联向量; N, 即refracting面的法向量; eta, 即ratio of indices of refraction.
* 注意: 要获取期望的结果, I向量和N向量必须归一化


## 矩阵函数

### 分量矩阵乘法

```cpp
mat2 matrixCompMult(mat2 x, mat2 y)  
mat3 matrixCompMult(mat3 x, mat3 y)  
mat4 matrixCompMult(mat4 x, mat4 y)
```

* `matrixCompMult`函数返回分量矩阵乘法的结果. 该函数有两个浮点矩阵类型的输入参数, 并返回该类型的矩阵. 返回向量的索引按照如下公式计算: z[i][j] = x[i][j] * y[i][j]
* 注意: 这不是线性代数中的矩阵乘法. 要获取平凡的矩阵乘法, 应该这样运算: z = x y


## 向量关系函数

### 小于

```cpp
bvec2 lessThan(vec2 x, vec2 y)  
bvec3 lessThan(vec3 x, vec3 y)    
bvec4 lessThan(vec4 x, vec4 y)  

bvec2 lessThan(ivec2 x, ivec2 y)  
bvec3 lessThan(ivec3 x, ivec3 y)  
bvec4 lessThan(ivec4 x, ivec4 y)
```

* `lessThan`函数返回x[i] < y[i]比较结果的布尔向量. 该函数有两个浮点向量或有符号整型向量类型的输入参数

### 小于等于

```cpp
bvec2 lessThanEqual(vec2 x, vec2 y)  
bvec3 lessThanEqual(vec3 x, vec3 y)  
bvec4 lessThanEqual(vec4 x, vec4 y)  

bvec2 lessThanEqual(ivec2 x, ivec2 y)  
bvec3 lessThanEqual(ivec3 x, ivec3 y)  
bvec4 lessThanEqual(ivec4 x, ivec4 y)
```

* `lessThanEqual`函数返回x[i] <= y[i]的比较结果的布尔向量. 该函数有两个浮点向量或有符号整型向量的输入参数

### 大于

```cpp
bvec2 greaterThan(vec2 x, vec2 y)  
bvec3 greaterThan(vec3 x, vec3 y)  
bvec4 greaterThan(vec4 x, vec4 y)  

bvec2 greaterThan(ivec2 x, ivec2 y)  
bvec3 greaterThan(ivec3 x, ivec3 y)  
bvec4 greaterThan(ivec4 x, ivec4 y)
```

* `greaterThan`函数返回x[i] > y[i]的比较结果的布尔向量. 该函数有两个浮点向量或有符号整型向量类型的输入参数

### 大于等于

```cpp
bvec2 greaterThanEqual(vec2 x, vec2 y)  
bvec3 greaterThanEqual(vec3 x, vec3 y)  
bvec4 greaterThanEqual(vec4 x, vec4 y)  

bvec2 greaterThanEqual(ivec2 x, ivec2 y)  
bvec3 greaterThanEqual(ivec3 x, ivec3 y)  
bvec4 greaterThanEqual(ivec4 x, ivec4 y)
```

* `greaterThanEqual`函数返回x[i] >= y[i]比较结果的布尔向量. 该函数有两个浮点向量或有符号整型向量的输入参数

### 等于

```cpp
bvec2 equal(vec2 x, vec2 y)  
bvec3 equal(vec3 x, vec3 y)  
bvec4 equal(vec4 x, vec4 y)  

bvec2 equal(ivec2 x, ivec2 y)  
bvec3 equal(ivec3 x, ivec3 y)  
bvec4 equal(ivec4 x, ivec4 y)
```

* `equal`函数返回x[i] = y[i]比较结果的布尔向量. 该函数有两个浮点向量或有符号整型向量的输入参数

### 不等

```cpp
bvec2 notEqual(vec2 x, vec2 y)  
bvec3 notEqual(vec3 x, vec3 y)  
bvec4 notEqual(vec4 x, vec4 y)  

bvec2 notEqual(ivec2 x, ivec2 y)  
bvec3 notEqual(ivec3 x, ivec3 y)  
bvec4 notEqual(ivec4 x, ivec4 y)
```

* `notEqual`函数返回x[i] != y[i]比较结果的布尔向量. 该函数有两个浮点向量或有符号整型向量的输入参数

### any估值

```cpp
bool any(bvec2 x)  
bool any(bvec3 x)  
bool any(bvec4 x)
```

* `any`函数返回是否任意的输入向量的分量都是TRUE的布尔值. 该函数有一个布尔向量类型的输入参数

### all估值

```cpp
bool all(bvec2 x)  
bool all(bvec3 x)  
bool all(bvec4 x)
```

* `all`函数返回是否全部的输入向量的分量都是TRUE的布尔值. 该函数有一个布尔向量类型的输入参数

### not估值

```cpp
bvec2 not(bvec2 x)  
bvec3 not(bvec3 x)  
bvec4 not(bvec4 x)
```

* `not`函数返回对向量x元素逐个进行逻辑补操作后结果的向量


## 纹理查询函数

### 2D纹理查询

```cpp
vec4 texture2D(sampler2D sampler, vec2 coord)  
vec4 texture2D(sampler2D sampler, vec2 coord, float bias)
```

* `texture2D`函数返回一个纹理元素(texel), 即纹理指定坐标的颜色值. 该函数有一个sampler2D类型的输入参数, 和一个vec2类型的输入参数: sampler, 纹理绑定的uniform; coord, 即纹理元素的二维坐标
* 有一个可选的第三个浮点类型的输入参数: bias. 在使用mipmap计算一个纹理的合理级别的细节后, bias会在实际纹理查询运算执行之前被加入
* 注意: 在iOS设备上纹理查询函数仅适用于fragment shader

## cubemap纹理查询

```cpp
vec4 textureCube(samplerCube sampler, vec3 coord)  
vec4 textureCube(samplerCube sampler, vec3 coord, float bias)
```

* `textureCube`函数返回一个纹理元素(texel), 即纹理指定坐标的颜色值. 该函数有一个samplerCube类型的输入参数, 和一个vec3类型的输入参数: sampler, 即纹理绑定的uniform; coord, 即纹理元素的三维坐标
* 有一个可选的第三个浮点类型的输入参数: bias. 在使用mipmap计算一个纹理的合理级别的细节后, bias会在实际纹理查询运算执行之前被加入
* 注意: 在iOS设备上纹理查询函数仅适用于fragment shader
