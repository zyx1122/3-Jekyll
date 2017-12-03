---
title:  "weapp-start"
date:   2017-01-22
categories: weapp
tags: weapp-start
---

# 一、weapp 项目结构
### 通过微信开发者工具快速创建了一个项目`暂称为GNY项目`,包含四种不同类型的文件:

      1.json 后缀的 JSON 配置文件
      2.wxml 后缀的 WXML 模板文件
      3.wxss 后缀的 WXSS 样式文件
      4.js 后缀的 JS 脚本逻辑文件
<img src="/assets/img/2017-12-01-weapp-start/weapp-structure.png">

## 1 .JSON 配置文件
### 1.1 小程序配置 app.json
是对当前小程序的全局配置，包括了小程序的所有页面路径、界面表现、网络超时时间、底部 tab 等。GNY 项目里边的 app.json 配置内容如下：
```js
{
  "pages":[
    "pages/index/index",
    "pages/logs/logs"
  ],
  "window":{
    "backgroundTextStyle":"light",
    "navigationBarBackgroundColor": "#fff",
    "navigationBarTitleText": "WeChat",
    "navigationBarTextStyle":"black"
  }
}
```
1.pages字段 —— 用于描述当前小程序所有页面路径，这是为了让微信客户端知道当前你的小程序页面定义在哪个目录。
2.window字段 —— 小程序所有页面的顶部背景颜色，文字颜色定义在这里的。

其他配置项细节参考文档 [小程序的配置 app.json](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/config.html) 。

### 1.2 工具配置 project.config.json
小程序开发者工具在每个项目的根目录都会生成一个 project.config.json，你在工具上做的任何配置都会写入到这个文件，当你重新安装工具或者换电脑工作时，你只要载入同一个项目的代码包，开发者工具就自动会帮你恢复到当时你开发项目时的个性化配置，其中会包括编辑器的颜色、代码上传时自动压缩等等一系列选项。

其他配置项细节可以参考文档 [开发者工具的配置](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/edit.html#项目配置文件) 。

### 1.3 页面配置 page.json
这里的 page.json 其实用来表示 pages/logs 目录下的 logs.json 这类和小程序页面相关的配置。

让开发者可以独立定义每个页面的一些属性。

其他配置项细节可以参考文档 [小程序的配置 page.json](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/config.html) 。

## 2 WXML模版
pages/index/index.wxml
{% highlight html linenos %}
<!--index.wxml-->
<view class="container">
  <view class="userinfo">
    <button wx:if="{{!hasUserInfo && canIUse}}" open-type="getUserInfo" bindgetuserinfo="getUserInfo"> 获取头像昵称 </button>
    <block wx:else>
      <image bindtap="bindViewTap" class="userinfo-avatar" src="{{userInfo.avatarUrl}}" background-size="cover"></image>
      <text class="userinfo-nickname">{{userInfo.nickName}}</text>
    </block>
  </view>
  <view class="usermotto">
    <text class="user-motto">{{motto}}</text>
  </view>
</view>
{% endhighlight %}

## 3 WXSS 样式
WXSS 具有 CSS 大部分的特性，小程序在 WXSS 也做了一些扩充和修改。

* 新增了尺寸单位。在写 CSS 样式时，开发者需要考虑到手机设备的屏幕会有不同的宽度和设备像素比，采用一些技巧来换算一些像素单位。WXSS 在底层支持新的尺寸单位 rpx ，开发者可以免去换算的烦恼，只要交给小程序底层来换算即可，由于换算采用的浮点数运算，所以运算结果会和预期结果有一点点偏差。

* 提供了全局的样式和局部样式。和前边 app.json, page.json 的概念相同，你可以写一个 app.wxss 作为全局样式，会作用于当前小程序的所有页面，局部页面样式 page.wxss 仅对当前页面生效。

* 此外 WXSS 仅支持部分 CSS 选择器
更详细的文档可以参考 [WXSS](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxss.html) 。

## 4 JS 交互逻辑
详细的事件可以参考文档 [WXML - 事件](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/view/wxml/event.html) 。

此外还可以在 JS 中调用小程序提供的丰富的 API，利用这些 API 可以很方便的调起微信提供的能力，例如获取用户信息、本地存储、微信支付等。更多 API 可以参考文档 [小程序的API](https://mp.weixin.qq.com/debug/wxadoc/dev/api/) 。

# 二、weapp 的启动
* 微信客户端在打开小程序之前，会把整个小程序的代码包下载到本地。

* 紧接着通过 app.json 的 pages 字段就可以知道当前小程序的所有页面路径,写在 pages 字段的第一个页面就是这个小程序的首页(打开小程序看到的第一个页面):
```js
{
  "pages":[
    "pages/index/index",
    "pages/logs/logs"
  ]
}
```

* 于是微信客户端就把首页的代码装载进来，通过小程序底层的一些机制，就可以渲染出这个首页。

* 小程序启动之后，在 app.js 定义的 App 实例的 onLaunch 回调会被执行:

整个小程序只有一个 App 实例，是全部页面共享的，更多的事件回调参考文档 [注册程序 App](https://mp.weixin.qq.com/debug/wxadoc/dev/framework/app-service/app.html)。