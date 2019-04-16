# 参考
[官网](https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxss.html)


# 前言
**wxss**: 类似`css`，用来描述`wxml`组件的样式。`wxss`除了拥有`css`的大部分特性外，
它还对`css`的功能进行了两方面的拓展：
1. 新的尺寸`rpx`
2. 支持文件导入


# 响应式尺寸rpx
**rpx**: 默认所有的设备宽度为**750rpx**。
以iphone6为例，屏幕宽度为375px
```
375px = 750rpx
由此可以得到换算关系
1px  = 2rpx
1rpx = 0.5px
```

不同设备上的换算关系：
```
1px = 屏幕宽度/750 rpx
1rpx = 750/屏幕宽度 px
```

`rpx`的原理和普通的css尺寸单位`rem`原理类似，都是相对单位，不同的是：
> rpx是相对于整个设备宽度  
> rem是相对于根元素`html`的`fontsize`

# 文件导入
小程序支持导入外部的`css`文件，可作为共同样式的定义

例： 在某`wxss`文件中导入`test.wxss`文件
> 必须以`;`结束
```
使用
@import './test.wxss';
```

> 注意：css的解析顺序是从上到下的，后面的样式会覆盖前面。


# 支持的选择器
- id
- class
- element
- element, element
- ::before
- ::after

和`css`一样，注意权重问题
* ！important: ∞
* 内联样式style: 1000
* id选择器: 100
* 类、伪类、属性选择器: 10
* 标签、伪元素 : 1



# 全局样式和页面样式
定义在`app.wxss`的样式为全局样式   
定义在页面的`wxss`样式为页面样式，页面样式会覆盖全局样式。
