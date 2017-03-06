# OpenGLES

* `OpenGL ES`: OpenGl for Embedded Systems, 专门适用于嵌入式设备的OpenGL

## OpenGLES版本在安卓上的支持

* `1.0`, `1.1`: android 1.0(0)及以上支持
* `2.0`: android 2.2(8)及以上支持
* `3.0`: android 4.3(18)及以上支持
* `3.1`: android 5.0(21)及以上支持

> OpenGLES 3.0要求设备支持图像管道, android 4.3及以上的设备有可能不支持此特性

## 基本概念

android通过框架API和NDK支持OpenGL, 本文专注于框架接口.

OpenGL ES创建和操作图形主要有两个基本类: `GLSurfaceView`和`GLSurfaceView.Renderer`. 在应用中使用OpenGL首先需要了解如何在activity中实现这两个类

* `GlSurfaceView`   
是一个View子类, 可以使用OpenGL api来绘制和操作对象, 同SurfaceView类似. 通过创建`GLSurfaceView`实例并添加`Renderer`来使用该类. 如果需要捕获触屏事件, 需要继承`GLSurfaceView`类, 并实现触摸监听器
* `GLSurfaceView.Renderer`
该接口定义了`GLSurfaceView`绘制图像所需的方法. 必须实现该接口, 并使用`GLSurfaceView.setRenderer()`来将你的`GLSurfaceView`实例设置进去. `GLSurfaceView.Render`接口需要实现以下方法:
    - `onSurfaceCreated()`: 当创建`GLSurfaceView`时系统会调用本方法一次. 可以使用本方法来调用只需要执行一次的方法, 例如设置OpenGL环境参数, 初始化OpenGL图像对象
    - `onDrawFrame()`: 当`GLSurfaceView`每次重绘时调用. 本方法用于绘制或重绘图像对象时的主要操作
    - `onSurfaceChanged()`: 当`GLSurfaceView`发生几何改变时调用, 包括`GLSurfaceView`的尺寸或设备屏幕方向的变化. 可以使用本方法处理`GLSurfaceView`的变化


## OpenGLES包

当使用`GLSurfaceView`和`GLSurfaceView.Render`创建了容器之后, 便可以调用OpenGL的api:
* 1.0/1.1:
    - `android/opengl`: 该包提供静态接口
        - `GLES10`
        - `GLES10Ext`
        - `GLES11`
        - `GLES11Ext`
    - `javax.microedition.khronos.opengles`: 该包提供OpenGL ES 1.0/1.1的标准实现
        - `GL10`
        - `GL10Ext`
        - `GL11`
        - `GL11Ext`
        - `GL11ExtensionPack`
* 2.0:
    - `android.opengl.gles20`: 该包提供android 2.2及以上对OpenGLES 2.0的接口
* 3.0/3.1:
    - `android.opengl`: 该包提供OpenGLES3.0/3.1的接口. 3.0适用于4.3及以上, 3.1适用于5.0及以上
        - `GLES30`
        - `GLES31`
        - `GLES31Ext`(android扩展包)

## 声明OpenGL要求

需要在`AndroidManifest.xml`中声明OpenGL的版本要求:

```xml
// OPENGLES 2.0
<!-- Tell the system this app requires OpenGL ES 2.0. -->
<uses-feature android:glEsVersion="0x00020000" android:required="true" />

// OPENGLES 3.0
<!-- Tell the system this app requires OpenGL ES 3.0. -->
<uses-feature android:glEsVersion="0x00030000" android:required="true" />

// OPENGLES 3.1
<!-- Tell the system this app requires OpenGL ES 3.1. -->
<uses-feature android:glEsVersion="0x00030001" android:required="true" />
```


## 坐标系

OpenGL假设使用正方形, 统一的坐标系来进行绘制, 该正方形在非正方形屏幕上会被拉伸

![坐标轴拉伸](https://developer.android.com/images/opengl/coordinates.png)



## OpenGLES 1.0中的projection和camera view

OpenGLES 1.0 中, 通过为projection和camera view创建各自的matrix并添加到OpenGL环境中实现

1. Projection matrix: 使用设备屏幕的几何参数来创建projection matrix以便重新计算相关属性.
2. Camera transformation matrix: 使用projection matrix调整了坐标系后, 必须设置camera view.

```java
// projection matrix
public void onSurfaceChanged(GL10 gl, int width, int height) {
    gl.glViewport(0, 0, width, height);

    // make adjustments for screen ratio
    float ratio = (float) width / height;
    gl.glMatrixMode(GL10.GL_PROJECTION);        // set matrix to projection mode
    gl.glLoadIdentity();                        // reset the matrix to its default state
    gl.glFrustumf(-ratio, ratio, -1, 1, 3, 7);  // apply the projection matrix
}

// camera view
public void onDrawFrame(GL10 gl) {
    ...
    // Set GL_MODELVIEW transformation mode
    gl.glMatrixMode(GL10.GL_MODELVIEW);
    gl.glLoadIdentity();                      // reset the matrix to its default state

    // When using GL_MODELVIEW, you must set the camera view
    GLU.gluLookAt(gl, 0, 0, -5, 0f, 0f, 0f, 0f, 1.0f, 0.0f);
    ...
}
```


## OpenGLES 2.0及更高版本中的projection和camera view

在ES 2.0和3.0中, 必须首先添加一个matrix member到图像对象的vertex shader来设置projection和camera view. 添加该meatrix member后, 便可以生成并设置projection和camera view矩阵到对象中

1. 添加matrix到vertex shader: 创建一个变量, 将其作为shader位置的乘数.
2. 访问shader matrix: 在vertex shader创建钩子来设置projection和camera view后, 便可通过刚才的变量来设置projection和camera view矩阵
3. 创建projection和camera view矩阵
4. 设置projection和camera view矩阵

```java
// 创建变量
private final String vertexShaderCode =

    // This matrix member variable provides a hook to manipulate
    // the coordinates of objects that use this vertex shader.
    "uniform mat4 uMVPMatrix;   \n" +

    "attribute vec4 vPosition;  \n" +
    "void main(){               \n" +
    // The matrix must be included as part of gl_Position
    // Note that the uMVPMatrix factor *must be first* in order
    // for the matrix multiplication product to be correct.
    " gl_Position = uMVPMatrix * vPosition; \n" +

    "}  \n";

// 设置shader matrix
public void onSurfaceCreated(GL10 unused, EGLConfig config) {
    ...
    muMVPMatrixHandle = GLES20.glGetUniformLocation(mProgram, "uMVPMatrix");
    ...
}

// 创建projection和camera view矩阵
public void onSurfaceCreated(GL10 unused, EGLConfig config) {
    ...
    // Create a camera view matrix
    Matrix.setLookAtM(mVMatrix, 0, 0, 0, -3, 0f, 0f, 0f, 0f, 1.0f, 0.0f);
}

public void onSurfaceChanged(GL10 unused, int width, int height) {
    GLES20.glViewport(0, 0, width, height);

    float ratio = (float) width / height;

    // create a projection matrix from device screen geometry
    Matrix.frustumM(mProjMatrix, 0, -ratio, ratio, -1, 1, 3, 7);
}

// 设置projection和camera view矩阵
public void onDrawFrame(GL10 unused) {
    ...
    // Combine the projection and camera view matrices
    Matrix.multiplyMM(mMVPMatrix, 0, mProjMatrix, 0, mVMatrix, 0);

    // Apply the combined projection and camera view transformations
    GLES20.glUniformMatrix4fv(muMVPMatrixHandle, 1, false, mMVPMatrix, 0);

    // Draw objects
    ...
}
```

## 图形的face和winding

* face: 3个或以上个点组成的三维空间的平面, face方向由winding或点的方向确定
    - front face: 逆时针绘制点
    - back face: 顺时针绘制点
* winding: 点的绘制方向
* face culling: back face不会进行计算和绘制, 以节省时间和内存

> 建议使用顺时针定义front face的点

## 纹理压缩支持

* `text compression`: 纹理压缩, 可以通过减少内存消耗, 提高内存带宽使用效率来显著提高应用的性能
* android提供`ETC1`(ETC1Util)压缩格式, 并提供了etc1tool(<sdk>/tools/)
* 并不是所有android设备都支持纹理压缩, 使用前需要进行判断:`ETC1Util.isETC1Supported()`
* ETC1纹理压缩不支持透明通道
* OpenES 3.0提供ETC2.0/EAC纹理压缩格式, 提供更优秀的压缩比, 支持透明通道
* 其他纹理压缩格式
    - `ATITC(ATC)`
    - `PVRTC`
    - `S3TC(DXTn/DXTC)`
    - `3DC`

```java
// 检查设备支持何种纹理压缩
String extensions = javax.microedition.khronos.opengles.GL10.glGetString(
        GL10.GL_EXTENSIONS);
```

## 使用OpenGL扩展

* 使用`Android Extension Pack`必须在`AndroidManifest.xml`中声明

```xml
<uses feature android:name="android.hardware.opengles.aep"
              android:required="true" />
```

* 检查是否支持aep

```java
boolean deviceSupportsAEP = getPackageManager().hasSystemFeature
     (PackageManager.FEATURE_OPENGLES_EXTENSION_PACK);
```


## 检查设备支持的OpenGLES版本

2种方式:
1. 尝试从高版本创建, 并检查创建结果, 失败则尝试低版本
2. 查看最低支持版本并创建

```java
// 方式1: 检查是否支持ES 3.0, 不支持则尝试2.0
private static double glVersion = 3.0;

private static class ContextFactory implements GLSurfaceView.EGLContextFactory {

  private static int EGL_CONTEXT_CLIENT_VERSION = 0x3098;

  public EGLContext createContext(
          EGL10 egl, EGLDisplay display, EGLConfig eglConfig) {

      Log.w(TAG, "creating OpenGL ES " + glVersion + " context");
      int[] attrib_list = {EGL_CONTEXT_CLIENT_VERSION, (int) glVersion,
              EGL10.EGL_NONE };
      // attempt to create a OpenGL ES 3.0 context
      EGLContext context = egl.eglCreateContext(
              display, eglConfig, EGL10.EGL_NO_CONTEXT, attrib_list);
      return context; // returns null if 3.0 is not supported;
  }
}


// 方式2: 直接查看当前最低支持版本
// Create a minimum supported OpenGL ES context, then check:
String version = javax.microedition.khronos.opengles.GL10.glGetString(
        GL10.GL_VERSION);
Log.w(TAG, "Version: " + version );
// The version format is displayed as: "OpenGL ES <major>.<minor>"
// followed by optional content provided by the implementation.
```

## 选择合适的OpenGL版本

考虑以下几点:
1. 性能: 2.0/3.0提供更快的图像性能
2. 设备兼容性: 设备是否兼容
3. 编码便利性: 1.0/1.1提供固定的函数管道和便捷的函数api, 更易于编码
4. 图像控制: 2.0/3.0通过shader提供更高等级的控制
5. 纹理支持: 3.0支持ETC2压缩格式和透明通道; 1.x/2.0使用ETC1, 不支持透明通道






## 参考

文章:
* [子龙山人](https://zilongshanren.com/categories/Cocos2d-x/OpenGL-ES/)
* [Android OpenGL 基础入门](http://www.cnblogs.com/zhuyp1015/p/4472599.html)
* [Android OpenGL 编写简单滤镜](http://www.cnblogs.com/zhuyp1015/p/4513355.html)
* [GLSL实现图像处理](http://blog.csdn.net/zhouxuguang236/article/details/45540801)
* [GPU处理图像Shader的入门](http://www.jianshu.com/p/8687a040eb48)
* [OpenGLES着色器(Shader)介绍](http://imgtec.eetrend.com/blog/1948)
* [OpenGL超级宝典笔记](https://my.oschina.net/sweetdark/blog/208024)

Shader资源:
* [Shadertoy](https://www.shadertoy.com/)
