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

* `power`函数返回x的y次幂的值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算

## 自然指数函数

```c
float exp(float x)  
vec2 exp(vec2 x)  
vec3 exp(vec3 x)  
vec4 exp(vec4 x)
```

* `exp`函数返回常量e的x次幂的值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算 

### 对数

```c
float log(float x)  
vec2 log(vec2 x)  
vec3 log(vec3 x)  
vec4 log(vec4 x)
```

* `log`函数返回以e为底x的对数. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算

### 自然指数函数2

```c
float exp2(float x)  
vec2 exp2(vec2 x)  
vec3 exp2(vec3 x)  
vec4 exp2(vec4 x)
```

* `exp2`函数返回2的x次幂的值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算

### 对数函数2

```c
float log2(float x)  
vec2 log2(vec2 x)  
vec3 log2(vec3 x)  
vec4 log2(vec4 x)
```

* `log2`函数返回以2为底x的对数. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算

### 平方根

```cpp
float sqrt(float x)  
vec2 sqrt(vec2 x)  
vec3 sqrt(vec3 x)  
vec4 sqrt(vec4 x)
```

* `sqrt`函数返回x的平方根. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算

### 平方根倒数

```cpp
float inversesqrt(float x)  
vec2 inversesqrt(vec2 x)  
vec3 inversesqrt(vec3 x)  
vec4 inversesqrt(vec4 x)
```

* `inversesqrt`函数返回x的平方根倒数. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算


## 通用函数

### 绝对值

```cpp
float abs(float x)  
vec2 abs(vec2 x)  
vec3 abs(vec3 x)  
vec4 abs(vec4 x)
```

* `abs`函数返回x的绝对值. 输入参数可以是浮点纯量或浮点向量. 如果是浮>点向量, 则按照元素方向进行运算

### sign

```cpp
float sign(float x)  
vec2 sign(vec2 x)  
vec3 sign(vec3 x)  
vec4 sign(vec4 x)
```

* `sign`函数在当x为正数时返回1.0, 当x是0时返回0.0, 当x为负数时返回-1.0. 输入参数可以是浮点纯量或浮点向量. 如果是浮>点向量, 则按照元素方向进行运算

### 向下取整

```cpp
float floor(float x)  
vec2 floor(vec2 x)  
vec3 floor(vec3 x)  
vec4 floor(vec4 x)
```

* `floor`函数进行向下取整并返回该整数. 输入参数可以是浮点纯量或浮点向量. 如果是浮>点向量, 则按照元素方向进行运算
* 注意: 即使运算的是整数, 返回值也会是浮点纯量或浮点向量

### 向上取整

```cpp
float ceil(float x)  
vec2 ceil(vec2 x)  
vec3 ceil(vec3 x)  
vec4 ceil(vec4 x)
```

* `ceiling`函数进行向上取整并返回该整数. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算
* 注意: 即使运算的是整数, 返回值也会是浮点纯量或浮点向量

### 取余

```cpp
float fract(float x)  
vec2 fract(vec2 x)  
vec3 fract(vec3 x)  
vec4 fract(vec4 x)
```

* `fract`函数返回x的小数部分. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算

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

* `mod`函数返回x模于y的值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算
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

* `min`函数返回两个参数的最小值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算
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
, 则按照元素方向进行运算
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

* `clamp`函数在当x大于minVal并且小于maxVal时返回x, 当x小于minVal时返回minVal, 当x大于maxVal时返回maxVal. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算
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

* `mix`函数返回x和y的线性混合, 例如x * ((1-a) + (y * a)). 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算
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

* `step`函数在当x小于edge时返回0.0, 否则返回1.0. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算
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

* `smoothstep`函数在当x小于edge0时返回0.0, 当x大于edge1时返回1.0, 否则返回使用厄尔米多项式(Hermite polynomials)插值的介于0.0到1.0之间的值. 输入参数可以是浮点纯量或浮点向量. 如果是浮点向量, 则按照元素方向进行运算
* 此外`smoothstep`函数还有edge0和edge1参数是浮点纯量的函数


## 几何函数

### 长度

```cpp
float length(float x)  
float length(vec2 x)  
float length(vec3 x)  
float length(vec4 x)
```
