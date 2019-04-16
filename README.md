# Wechat-applet-practice
微信小程序入门练习

# 目录
- [1-小程序配置](#1-小程序配置)
- [2-小程序框架](#2-小程序框架) 
  - [视图层](#视图层)

 

# 1-小程序配置
一个小程序的运行至少需要两个配置文件
1. app.js: 注册小程序应用
2. app.json：小程序全局配置文件



# 2-小程序框架

## 视图层
视图层：`.wxml`后缀文件，类似`html`，决定页面的显示结构。`wxml`的学习主要包括以下方面：
1. 数据绑定
2. 共有属性
3. 列表渲染
4. 条件渲染
5. 模板声明与使用
6. 引入



### 数据绑定
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


### 共有属性
- id: 组件唯一标识
- class: 外联样式，在`wxss`书写
- style: 内联样式
- hidden: 组件是否显示
- data-*: 自定义属属性，传入事件对象
- bind/catch: 绑定事件


### 列表渲染
绑定数组数据，默认渲染项`item`, 默认序号`index`
```
<block wx:for='{{list}}' wx:for-item='item' wx:for-index='index' wx:key='index'>
    {{ item }}
</block>
```


### 条件渲染
是否渲染某组件
```
<view >
    <text wx:if='{{ count === 1 }}'>1</text>
    <text wx:elif='{{ count === 2 }}'>2</text>
    <text wx:else>other</text>
</view>

```

### 模板
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

### 引用
import: 引用目标文件声明的模板
```
<import src='./a.wxml'/>
```

include：引用目标文件模板以外的代码，相当于拷贝
```
<include src='./a.wxml'/>
```
