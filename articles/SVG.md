#学习前请点击下面链接
[为何Google的新Logo只有305个字节？](http://www.tuicool.com/articles/rUNBjq#0-qzone-1-26437-d020d2d2a4e8d1a374a433f596ad1440)
#什么是矢量图?
    矢量图使用直线和曲线来描述图形，这些图形的元素是一些点、线、矩形、多边形、圆和弧线等等，它们都是通过数学公式计算获得的。
#什么是SVG?
    SVG(可放缩的矢量图形)是W3C在2000年8月制定的一种新的二维矢量图形格式。

# 使用 SVG 的优势
1. SVG 可被非常多的工具读取和修改（比如记事本）,由于使用xml格式定义，所以可以直接被当作文本文件打开，看里面的数据；
2. SVG 与 JPEG 和 GIF 图像比起来，尺寸更小，且可压缩性更强，SVG图就相当于保存了关键的数据点，比如要显示一个圆，需要知道圆心和半径，那么SVG 就只保存圆心坐标和半径数据，而平常我们用的位图都是以像素点的形式根据图片大小保存对应个数的像素点，因而SVG尺寸更小；
3. 是可伸缩的，平常使用的位图拉伸会发虚，压缩会变形，而SVG格式图片保存数据进行运算展示，不管拉大多少，可以不失真显示；
4. 图像可在任何的分辨率下被高质量地打印;
5. 可在图像质量不下降的情况下被放大;
6. 图像中的文本是可选的，同时也是可搜索的（很适合制作地图）;
7. 可以与 Java 技术一起运行;
8. 是开放的标准;
9. 文件是纯粹的 XML;

#SVG图片样例
![图片](/image/heart.svg)

##图片代码

    <?xml version="1.0" ?>
    <!DOCTYPE svg  PUBLIC '-//W3C//DTD SVG 1.1//EN'  'http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd'>
    <svg enable-background="new 0 0 64 64" id="Layer_1" version="1.1" viewBox="0 0 64 64" xml:space="preserve"
    xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
      <g>
        <path d="M58.3,10.6C51.4,3.6,40,3.7,32,10.5c-1.3-1.1-2.6-2-4.1-2.8l-5.5-3.8c-0.3-0.2-0.6-0.2-1-0.1
        c-0.3,0.1-0.5,0.4-0.6,0.8l-0.2,1C15,4.9,9.6,6.7,5.7,10.6C-1.8,18.1-2,30,5.4,37.8L31.3,64c0.2,0.2,0.4,0.3,0.7,0.3
        s0.5-0.1,0.7-0.3l25.9-26.2C65.9,30.2,65.7,18,58.3,10.6z M14.3,20.7l1.6,1.9L5.3,26.4l-0.9-9.1L14.3,20.7z M19.5,18.3l1.5,3.8    l-2,1.2l-2.6-3.1L19.5,18.3z M17.2,24.3C17.3,24.3,17.3,24.3,17.2,24.3l0.4,0.5L14,34c0,0,0,0,0,0l0,0c-0.1,0.3-0.3,0.5-0.5,0.6
        c-0.3,0.1-0.6,0.1-0.8,0l-6.8-3.1l7.6-5.9L17.2,24.3z M19.6,25.2l0.2-0.1l4.1,17.9l-7.2-1.1L16,34.4L19.6,25.2z
        M22.4,23.5    l9.6,1.2l6.2,4.3l-2.5,6.8L22.2,23.7L22.4,23.5z     M33.8,21.9c0,0.3-0.2,0.6-0.4,0.7c-0.2,0.2-0.5,0.2-0.9,0.2l-9.6-1.2l-0.3-0.7    l3.3-2.8l8.4-3.6L33.8,21.9z
        M30.4,11.9l-8.4,7L21,16.5c0,0,0-0.1-0.1-0.1l1.9-9.5c0,0,0.2,0,0.2,0s0,0,0,0l-0.2-0.4L30.4,11.9z
        M7.1,12c3.5-3.5,8.2-5.1,13.3-4.5l-1.5,8.8l-4.1,2.4L4.5,15.3C5.3,14.1,6.1,13,7.1,12z M2.6,19.6l0.8,8.3c0,0.3,0.2,0.6,0.5,0.7
        c0.2,0.1,0.3,0.2,0.5,0.2c0.1,0,0.2,0,0.3-0.1l2.7-1L3.3,31c0,0,0,0,0,0C1.8,27.4,1.6,23.3,2.6,19.6z M57.2,36.4L32,61.8L6.8,36.4
        c-1-1-1.8-2.1-2.5-3.3l7.5,3.4c0.4,0.2,0.8,0.3,1.2,0.3c0.4,0,0.8-0.1,1.1-0.2l0.7,6.4c0,0.5,0.4,0.8,0.8,0.9l9.4,1.4
        c0,0,0.1,0,0.1,0c0.3,0,0.5-0.1,0.7-0.3c0.2-0.2,0.3-0.6,0.2-0.9l-4-17.6l13.3,11.9c0.2,0.2,0.4,0.3,0.7,0.3c0.1,0,0.2,0,0.2,0
        c0.3-0.1,0.6-0.3,0.7-0.6l3.2-8.9c0.2-0.4,0-0.9-0.4-1.2l-5.3-3.6c0.6-0.5,1.1-1.3,1.1-2.1l0.7-9.1c0-0.3-0.1-0.7-0.4-0.9
        c-0.3-0.2-0.7-0.2-1-0.1l-3.6,1.5l1.1-0.9c0,0,0,0,0,0c0,0,0,0,0,0c7.2-6.7,17.8-7,24.2-0.6C63.5,18.6,63.7,29.6,57.2,36.4z"
        fill="#4D4D4D"/>
      </g>
    </svg>

##path标签指令

    M = moveto   相当于 android Path 里的moveTo(),用于移动起始点  
    L = lineto   相当于 android Path 里的lineTo()，用于画线  
    H = horizontal lineto     用于画水平线  
    V = vertical lineto       用于画竖直线  
    C = curveto               相当于cubicTo(),三次贝塞尔曲线  
    S = smooth curveto        同样三次贝塞尔曲线，更平滑  
    Q = quadratic Belzier curve             quadTo()，二次贝塞尔曲线  
    T = smooth quadratic Belzier curveto    同样二次贝塞尔曲线，更平滑  
    A = elliptical Arc   相当于arcTo()，用于画弧  
    Z = closepath     相当于closeTo(),关闭path

#SVG图片与android关系
    一个类:AnimatedVectorDrawable
    两个标签:animated-vector,vector
##animated-vector,vector简介

***Android L提供了新的API VectorDrawable 可以使用SVG类型的资源，也就是矢量图。在xml文件中的标签是<vector>***

***path代表一个元素，绘制的内容是pathData下的一长串字符，里面是SVG绘制的一系列命令***
    
        <?xml version="1.0" encoding="utf-8"?>
        <vector xmlns:android="http://schemas.android.com/apk/res/android"
            android:width="256dp"
            android:height="256dp"
            android:viewportHeight="100"
            android:viewportWidth="100">
            <path
                android:name="heart1"
                android:strokeColor="#E91E63"
                android:strokeWidth="1"
                android:pathData="
        M58.3,10.6C51.4,3.6,40,3.7,32,10.5c-1.3-1.1-2.6-2-4.1-2.8l-5.5-3.8c-0.3-0.2-0.6-0.2-1-0.1c-0.3,0.1-0.5,0.4-0.6,0.8l-0.2,1C15,4.9,9.6,6.7,5.7,10.6C-1.8,18.1-2,30,5.4,37.8L31.3,64c0.2,0.2,0.4,0.3,0.7,0.3s0.5-0.1,0.7-0.3l25.9-26.2C65.9,30.2,65.7,18,58.3,10.6z"
                 />
            <path
                android:name="heart2"
                android:strokeColor="#00BCD4"
                android:strokeWidth="1"
                android:pathData="
        M57.2,36.4L32,61.8L6.8,36.4c-1-1-1.8-2.1-2.5-3.3l7.5,3.4c0.4,0.2,0.8,0.3,1.2,0.3c0.4,0,0.8-0.1,1.1-0.2l0.7,6.4c0,0.5,0.4,0.8,0.8,0.9l9.4,1.4c0,0,0.1,0,0.1,0c0.3,0,0.5-0.1,0.7-0.3c0.2-0.2,0.3-0.6,0.2-0.9l-4-17.6l13.3,11.9c0.2,0.2,0.4,0.3,0.7,0.3c0.1,0,0.2,0,0.2,0c0.3-0.1,0.6-0.3,0.7-0.6l3.2-8.9c0.2-0.4,0-0.9-0.4-1.2l-5.3-3.6c0.6-0.5,1.1-1.3,1.1-2.1l0.7-9.1c0-0.3-0.1-0.7-0.4-0.9c-0.3-0.2-0.7-0.2-1-0.1l-3.6,1.5l1.1-0.9c0,0,0,0,0,0c0,0,0,0,0,0c7.2-6.7,17.8-7,24.2-0.6C63.5,18.6,63.7,29.6,57.2,36.4z"
                 />
        
            <path
                android:name="heart3"
                android:strokeColor="#CDDC39"
                android:strokeWidth="1"
                android:pathData="
        M14.3,20.7l1.6,1.9L5.3,26.4l-0.9-9.1L14.3,20.7z"
                 />
            <path
                android:name="heart4"
                android:strokeColor="#795548"
                android:strokeWidth="1"
                android:pathData="
        M19.5,18.3l1.5,3.8    l-2,1.2l-2.6-3.1L19.5,18.3z"
                 />
            <path
                android:name="heart5"
                android:strokeColor="#E91E63"
                android:strokeWidth="1"
                android:pathData="
        M17.2,24.3C17.3,24.3,17.3,24.3,17.2,24.3l0.4,0.5L14,34c0,0,0,0,0,0l0,0c-0.1,0.3-0.3,0.5-0.5,0.6c-0.3,0.1-0.6,0.1-0.8,0l-6.8-3.1l7.6-5.9L17.2,24.3z"
                />
            <path
                android:name="heart6"
                android:strokeColor="#FF5722"
                android:strokeWidth="1"
                android:pathData="
        M22.4,23.5    l9.6,1.2l6.2,4.3l-2.5,6.8L22.2,23.7L22.4,23.5z"
                />
            <path
                android:name="heart7"
                android:strokeColor="#8BC34A"
                android:strokeWidth="1"
                android:pathData="
        M33.8,21.9c0,0.3-0.2,0.6-0.4,0.7c-0.2,0.2-0.5,0.2-0.9,0.2l-9.6-1.2l-0.3-0.7    l3.3-2.8l8.4-3.6L33.8,21.9z"
                 />
            <path
                android:name="heart8"
                android:strokeColor="#4CAF50"
                android:strokeWidth="1"
                android:pathData="
        M30.4,11.9l-8.4,7L21,16.5c0,0,0-0.1-0.1-0.1l1.9-9.5c0,0,0.2,0,0.2,0s0,0,0,0l-0.2-0.4L30.4,11.9z"
                />
            <path
                android:name="heart9"
                android:strokeColor="#3F51B5"
                android:strokeWidth="1"
                android:pathData="
        M7.1,12c3.5-3.5,8.2-5.1,13.3-4.5l-1.5,8.8l-4.1,2.4L4.5,15.3C5.3,14.1,6.1,13,7.1,12z"
                 />
            <path
                android:name="heart10"
                android:strokeColor="#9C27B0"
                android:strokeWidth="1"
                android:pathData="
        M2.6,19.6l0.8,8.3c0,0.3,0.2,0.6,0.5,0.7c0.2,0.1,0.3,0.2,0.5,0.2c0.1,0,0.2,0,0.3-0.1l2.7-1L3.3,31c0,0,0,0,0,0C1.8,27.4,1.6,23.3,2.6,19.6z"
                 />
        </vector>
  
***animated-vector引入的SVG是与vector相对应的,只是在其绘制时加载了动画***

    <animated-vector xmlns:android="http://schemas.android.com/apk/res/android"
    android:drawable="@drawable/heart">
    <target
        android:name="heart1"
        android:animation="@animator/heart_animator" />
    <target
        android:name="heart2"
        android:animation="@animator/heart_animator" />
    <target
        android:name="heart3"
        android:animation="@animator/heart_animator" />
    <target
        android:name="heart4"
        android:animation="@animator/heart_animator" />
    <target
        android:name="heart5"
        android:animation="@animator/heart_animator" />
    <target
        android:name="heart6"
        android:animation="@animator/heart_animator" />
    <target
        android:name="heart7"
        android:animation="@animator/heart_animator" />
    <target
        android:name="heart8"
        android:animation="@animator/heart_animator" />
    <target
        android:name="heart9"
        android:animation="@animator/heart_animator" />
    <target
        android:name="heart10"
        android:animation="@animator/heart_animator" />
</animated-vector>

***动画代码***

        <objectAnimator xmlns:android="http://schemas.android.com/apk/res/android"
        android:duration="6000"
        android:propertyName="trimPathEnd"
        android:valueFrom="0"
        android:valueTo="1"
        android:valueType="floatType" />

##AnimatedVectorDrawable简介
负责VectorDrawable矢量图形的动画的，不过我们不能像属性动画那样去通过代码进行设置动画，而是需要通过animated-vector标签在xml文件中创建一个AnimatedVectorDrawable

    ImageView mImageView = (ImageView) findViewById(R.id.imageView);
    AnimatedVectorDrawable mAnimatedVectorDrawable =  (AnimatedVectorDrawable) getResources().getDrawable(R.drawable.heart_vector_animator);
    mImageView.setImageDrawable(mAnimatedVectorDrawable);
    mAnimatedVectorDrawable.start();

#友情链接
[将SVG转成Android VectorDrawable XML资源文件](https://github.com/inloop/svg2android)

[SVG元素和代码解释](http://wenku.baidu.com/link?url=uH5IhUr3HO4oOgYc9_tDMRMFoCdduT2EB_MCzToXXXdnFaOoXLbMZwlPmcqE223YfIyebnE5ghnZcwM334w0l6eDETGIWsYu_N7eHmTdzg3)

[参考博客](http://blog.csdn.net/u010687392/article/details/48176727)
