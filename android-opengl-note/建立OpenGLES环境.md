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


