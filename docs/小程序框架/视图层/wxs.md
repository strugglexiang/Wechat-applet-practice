# 参考
[官网](https://developers.weixin.qq.com/miniprogram/dev/reference/wxs/)

# wxs
**wxs**: `wxs`是微信内置的新的脚本语言，用来描述`wxml`页面结构。

虽然`wxs`和`javascript`有很多相似的地方，但是他们是两种完全不同的脚本语言，使用`wxs`要
参考上述官网的规则。

用途：
1. `wxml`的数据绑定只能做简单绑定，不能进行复杂的操作(如函数调用)，复杂操作要借助于`wxs`脚本语言。

# 目录
- [模块](#模块)
- [数据类型](#数据类型)



# 模块
wxs模块：`wxs`脚本语言写在**单独的wxs文件**或者**wxml中的wxs标签**中。

每个模块在整个小程序解析为单例模式，即若多方引入使用的是一个模块。   
模块内部维护自身的作用域，对其他模块不可见。需要使用`module.exports`导出变量和函数供其他模块访问。  
如要访问其他模块，使用`require(文件相对路径)`引入
  


- - -
**wxs文件书写脚本**
1. 创建单独的`wxs`文件，在内书写脚本。
```
//useWxs.wxs文件内

/*
引入其他模块
var otherModule = require('./some/wxs')
*/

var name = 'strugglexiang'

var getName = function() {
    return name
}

module.exports = {
    getName,
}

```

2. `wxml`文件使用
```
//useWxs.wxml文件
<view>
    <wxs src='./useWxs.wxs' module='use' />
    <text>
        {{ use.getName() }}
    <text>
</view>
```

- - -
**wxs标签内书写脚本**
某`wxml`文件内
```
//src 引入其他模块
//use 定义自身模块名
<wxs  module='use'>
    var name = 'strugglexiang'
    module.exports.name = name
<wxs>

<view>
    {{ user.name }}
</view>
```


# 数据类型
和`js`不同的是，`wxs`有8种数据类型。   
- number: 数值
- string: 字符串
- boolean: 布尔值
- object: 对象
- array: 数组
- function: 函数
- date: 日期
- regexp: 正则



