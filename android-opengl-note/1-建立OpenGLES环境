# 建立OpenGLES环境

为了使用OpenGL ES在android应用中绘制图像, 你必须创建一个视图容器. 比较直接的方式是实现`GLSurfaceView`和`GLSurfaceView.Renderer`. `GLSurfaceView`是一个用于使用OpenGL来绘制图像的视图容器, `GLSurfaceView.Renderer`在该视图容器中绘制什么内容. 更多信息可参见[OpenGL ES](https://developer.android.com/guide/topics/graphics/opengl.html)

`GLSurfaceView`只是使用OpenGL ES的一种方式. 对于全屏或接近全屏的图像视图, 这种方式比较合理. 如果开发者只是在一小部分视图中使用OpenGL ES, 那么可以考虑`TextureView`. 对于一些喜欢DIY的开发者, 使用`SurfaceView`也是可以的, 但这需要编写更多的代码.

本章解释了如何使用`GLSurfaceView`和`GLSurfaceView.Renderer`实现一个简单的应用


## 在Manifest中声明使用OpenGL

为了使用OpenGL ES 2.0, 必须在manifest中声明一下内容:

```xml
<uses-feature android:glEsVersion="0x00020000" android:required="true" />
```

如果你的应用使用纹理压缩, 你必须同时声明应用支持的压缩格式:

```xml
<supports-gl-texture android:name="GL_OES_compressed_ETC1_RGB8_texture" />
<supports-gl-texture android:name="GL_OES_compressed_paletted_texture" />
```


## 为OpenGL图像创建一个Activity

使用OpenGL的activity同普通应用一样. 主要的区别在于activity中的布局. 在OpenGL的不居中, 一般会使用`GLSurfaceView`.

以下代码演示了activity中使用`GLSurfaceView`的最小实现:

```java
public class OpenGLES20Activity extends Activity {

    private GLSurfaceView mGLView;

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // Create a GLSurfaceView instance and set it
        // as the ContentView for this Activity.
        mGLView = new MyGLSurfaceView(this);
        setContentView(mGLView);
    }
}
```


## 创建一个GLSurfaceView对象

`GLSurfaceView`是专用于绘制OpenGL图像的特殊视图. 它自身并没有做太多事. 对象实际的绘制时在`GLSurfaceView.Renderer`来控制的. 该对象的代码很少, 你可能希望直接创建一个`GLSurfaceView`实例而不希望继承它, 但请不要这样做. 你需要继承该类, 来捕获触摸事件.

`GLSurfaceView`的必要代码时很少的, 为了快速实现, 通常可以在activity中创建一个内部类:

```java
class MyGLSurfaceView extends GLSurfaceView {

    private final MyGLRenderer mRenderer;

    public MyGLSurfaceView(Context context){
        super(context);

        // Create an OpenGL ES 2.0 context
        setEGLContextClientVersion(2);

        mRenderer = new MyGLRenderer();

        // Set the Renderer for drawing on the GLSurfaceView
        setRenderer(mRenderer);
    }
}
```

另一个额外选项是使用`GLSurfaceView.RENDERMODE_WHRN_DIRTY`设置将渲染模式设置为仅当有变化时绘制视图:

```java
// Render the view only when there is a change in the drawing data
setRenderMode(GLSurfaceView.RENDERMODE_WHEN_DIRTY);
```

该设置会阻止`GLSurfaceView`框架重绘, 直到你调用`requestRender()`, 这对于本例来说更有效率


## 创建一个渲染器类

`GLSurfaceView.Renderer`来的实现类, 或渲染器是比较有意思的地方. 该类控制`GLSurfaceView`中要绘制的内容. 渲染器有3个方法会被系统调用, 用来确定绘制内容和绘制方式:

* `onSurfaceCreated()` - 当OpenGL环境创建时调用一次
* `onDrawFrame()` - 每次重绘时调用
* `onSurfaceChanged()` - 当视图几何改变时调用, 例如屏幕方向改变

以下是OpenGL渲染器的基本实现, 只在`GLSurfaceView`中绘制了一个黑色背景:

```java
public class MyGLRenderer implements GLSurfaceView.Renderer {

    public void onSurfaceCreated(GL10 unused, EGLConfig config) {
        // Set the background frame color
        GLES20.glClearColor(0.0f, 0.0f, 0.0f, 1.0f);
    }

    public void onDrawFrame(GL10 unused) {
        // Redraw background color
        GLES20.glClear(GLES20.GL_COLOR_BUFFER_BIT);
    }

    public void onSurfaceChanged(GL10 unused, int width, int height) {
        GLES20.glViewport(0, 0, width, height);
    }
}
```

这就是全部. 以上代码创建了一个简单的显示黑色屏幕的OpenGL应用. 

> 注意: 你可能想知道为什么在使用OpenGL ES 2.0的API时, 这些方法的参数是`GL10`. 实际上这些方法只是简单的进行了复用, 从而作为2.0的API, 以此来简化代码.

