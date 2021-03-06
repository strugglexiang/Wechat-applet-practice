# 参考
[官网](https://developers.weixin.qq.com/miniprogram/dev/reference/wxml/index.html)

# 前言
wxml: `.wxml`后缀文件，类似`html`，决定页面的显示结构。   

`wxml`的学习主要包括以下方面: 
- [数据绑定](#数据绑定)
- [共有属性](#共有属性)
- [列表渲染](#列表渲染)
- [条件渲染](#条件渲染)
- [模板](#模板)
- [引用](#引用)


# 数据绑定
1. 内容
```
<view>
    {{ message }}
</view>
```

2. 组件属性
```
<view class='item + {{ count }}'>
</view>
```

3. 控制属性
```
<checkbox wx:if='{{check}}'></checkbox>
```

4. 运算
```
<view >
    <!-- 三元运算 -->
    <text>
        {{ count === 0 ? 'you' : 'I' }}
    </text>
    <!-- 算数运算(不支持++) -->
    <text>
        {{ count + 1 }}
    </text>
    <!-- 字符串运算 -->
    <text>
        {{ 'hello' + count }}
    </text>
    <!-- 逻辑判断 -->
    <text>
        {{ count > 0 }}
    </text>
    <!-- 数据路径判断 -->
    <text>
        {{ list[0] }}
    </text>
</view>
```

5. 组合
```
<!-- 组合成数组 -->
<view wx:for='{{[msg, count, 'some1', 'some2']}}'>
</view>
<!-- 组合成对象 -->
<template name='test'>
    <block>
        name: {{name}}
    </block>
    <block>
        age: {{age}}
    </block>
</template>

<template is='{name, age}'></template>
```


# 共有属性
- id: 组件唯一标识
- class: 外联样式，在`wxss`书写
- style: 内联样式
- hidden: 组件是否显示
- data-*: 自定义属属性，传入事件对象
- bind/catch: 绑定事件


# 列表渲染
绑定数组数据，默认渲染项`item`, 默认序号`index`
```
<block wx:for='{{list}}' wx:for-item='item' wx:for-index='index' wx:key='index'>
    {{ item }}
</block>
```


# 条件渲染
是否渲染某组件
```
<view >
    <text wx:if='{{ count === 1 }}'>1</text>
    <text wx:elif='{{ count === 2 }}'>2</text>
    <text wx:else>other</text>
</view>

```

# 模板
```
定义
<template name='test'>
    <text>{{ name }}</text>
    <text>{{ age }}</text>
</template>

使用：
<template is='test' data='{...item}'>
</template>
```

# 引用
import: 引用目标文件声明的模板
```
<import src='./a.wxml'/>
```

include：引用目标文件模板以外的代码，相当于拷贝
```
<include src='./a.wxml'/>
```