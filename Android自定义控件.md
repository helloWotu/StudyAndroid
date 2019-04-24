# Android自定义控件

### 为什么要自定义控件
+ 提升用户交互体验；
+ 搭配App的整体风格；
+ 优化布局；
+ ......

### 自定义控件分为两种：
1. 继承自View；
2. 继承自TextView、ImageView等现成的控件；

第一种需要我们从无到有来实现我们想要的控件，第二种只需要在原有的控件功能的基础上来拓展一些功能；

##自定义控件流程
自定义控价的基本流程：
1. 自定义属性的声明（类似于xml中的android:width）
    1. 在res/values/attrs.xml定义声明
    2. 在xml文件中使用或者在view构造函数中获取
2. 实现onMeasure()，控件的测量
    1. MeasureSpec.getMode(xxx)和MeasureSpec.getSize(xxx)，获取用户从xml中设置的控件的大小；（Mode的三种模式，EXACTLY, AT_MOST, UNSPECIFIED）
    2. setMeasuredDimension
    3. requestLayout()
3. 实现onLayout()，控件的布局的位置（只在ViewGroup中使用）
    1. 布局子View的位置
4. 实现onDraw()方法，控件的绘制
    1. 绘制内容
    2. 使用Canvas api中的一些方法
    3. 当发生改变时，重新绘制invalidate() postInvalidate()
5. onTachEvent()/onInterceptTouchEvent(ViewGroup)
    1. 用户交互实现
    2. 触摸事件、点击事件、多指触控等
    3. viewGroup中拦截子View事件拦截

