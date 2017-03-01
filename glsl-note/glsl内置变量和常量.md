# glsl内置变量和常量

## Vertex shader的特殊输出变量

### Vertex position

* vertex shader使用内置变量`gl_Position`将转换后的vertex position传递给OpenGL ES 2.0管道. 该变量已经在vertex shader中按照以下方式被定义过, 无需再次声明
* 位置向量的值在clip坐标空间中解释. vertex shader负责执行所有的vertex操作, 例如, 从object坐标到clip坐标的转换
* 对于vertex shader来说该变量的赋值是强制的

```c
highp vec4 gl_Position;
```

### Point size

* vertex shader使用内置变量`gl_PointSize`将vertex的point size传递给OpenGL ES 2.0管道. 该变量已经在vertex shader中按照以下方式被定义过, 无需再次声明
* point size的值会被解释为point sprite的像素半径. 实际绘制的几何图形是一个从点衍生出的弧线(rectangular primitive)和point sprite的半径.
* 注意: 如果渲染的primitive是点时, 仅通过OpenGL ES 2.0管道为该变量赋值时有效

```c
mediump float gl_PointSize;
```


## Fragment shader特有的input变量

### Fragment coordinates

* OpenGL ES 2.0管道内置变量`gl_FragCoord`用于将fragment坐标传递给fragment shader. 变量是只读的, 值被OpenGL ES 2.0管道赋值
* fragment坐标向量的值由窗口坐标系提供

```c
mediump vec4 gl_FragCoord;
```

### Fragment orientation

* OpenGL ES 2.0管道内置变量`gl_fontFacing`用于当fragment时某个front-facing primitive(三角)时将信息传递给fragment shader. 该变量是只读的, 值被OpenGL ES 2.0管道赋值
* front-facing变量有一个布尔值

```c
bool gl_FrontFacing;
```

### Point coordinates

* OpenGL ES 2.0管道内置变量`gl_PointCoord`用于将point sprite的坐标传递给fragment shader. 该变量是只读的, 其值根据位置和point sprite半径由OpenGL ES 2.0管道计算并赋值
* 只有当渲染的primitive是点时, OpenGL ES 2.0才会为该变量提供值

```c
mediump int gl_PointCoord;
```


## Fragment shader特有的output变量

### Fragment color

* fragment shader使用OpenGL ES 2.0管道内置变量`gl_FragColor`来将fragment的颜色传递给OpenGL ES 2.0管道. 该变量已经按以下方式提前定义, 无需声明便可在fragment shader中使用
* 颜色向量的值会在RGBA颜色空间解释
* 该变量的赋值在fagment shader中是强制的

```c
mediump vec4 gl_FragColor;
```


## 内置常量(vertex shader)

以下常量可以在vertex shader中读取, 可用于在运行时确定OpenGL ES 2.0环境的限制

### vertex属性数量

* 内置常量`gl_MaxVertexAttribs`提供了vertex shader可以使用的属性的最大数量. 该变量的值取决于OpenGL ES 2.0的实现, 但不会少于8

```c
const mediump int gl_MaxVertexAttribs >= 8
```

### vertex uniform向量数量

* 内置常量`gl_MaxVertexUniformVectors`提供了vertex shader可以使用的uniform向量的最大数量. 该变量的值取决于OpenGL ES 2.0的实现, 但不会少于128

```c
const mediump int gl_MaxVertexUniformVectors >= 128
```

### varing向量数量

* 内置常量`gl_MaxVaryingVectors`提供了可用于从vertex shader将数据传递到fragment shader的varying向量的最大数量. 该变量的值取决于OpenGL ES 2.0实现, 但不会少于8

```c
const mediump int gl_MaxVaryingVectors >= 8
```

### texture unit数量

* 内置常量`gl_MaxVertexTextureImageUnits`提供了vertex shader可以使用的texture unit的最大数量. 该变量的值取决于OpenGL ES 2.0的实现, 但不会少于0
* 在所有的iOS设备上该值为0. 这也是无法在vertex shader中访问texture数据的原因

```c
const mediump int gl_MaxVertexTextureImageUnits >= 0
```

### combined texture unit数量

* 内置常量`gl_MaxCombinedTextureImageUnits`提供了vertex shader或fragemnt shader可用的texture unit数量. 该变量的值取决于OpenGL ES 2.0的实现, 但不会少于8

```c
const mediump int gl_MaxCombinedTextureImageUnits >= 8
```


## 内置常量(fragment shader)

以下常量可以在fragment shader中读取, 可用于在运行时确定OpenGL ES 2.0环境的限制

### texture unit数量

* 内置常量`gl_MaxTextureImageUnits`提供了fragment shader可以使用的texture unit的最大数量. 该变量的值取决于OpenGL ES 2.0的实现, 但不会少于8

```c
const mediump int gl_MaxTextureImageUnits >= 8
```

### fragment uniform向量数量

* 内置常量`gl_MaxFragmentUniformVectors`提供了fragment shader可以使用的uniform向量的最大数量. 该变量的值取决于OpenGL ES 2.0的实现, 但不会少于16

```c
const mediump int gl_MaxFragmentUniformVectors >= 16
```

### draw buffer数量

* 内置常量`gl_MaxDrawBuffers`提供了可用的draw buffer的最大数量. 该变量的值在所有OpenGL ES 2.0中都是1. 可能会在未来的版本中改变
