---
title:  "weapp-start"
date:   2017-01-22
categories: weapp
tags: weapp-start
---

### 通过微信开发者工具快速创建了一个项目`暂称为GNY项目`,包含四种不同类型的文件:

      1.json 后缀的 JSON 配置文件
      2.wxml 后缀的 WXML 模板文件
      3.wxss 后缀的 WXSS 样式文件
      4.js 后缀的 JS 脚本逻辑文件
<img src="/assets/img/2017-12-01-weapp-start/weapp-structure.png">

### 1.小程序配置 app.json
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

### 2.工具配置 project.config.json
小程序开发者工具在每个项目的根目录都会生成一个 project.config.json，你在工具上做的任何配置都会写入到这个文件，当你重新安装工具或者换电脑工作时，你只要载入同一个项目的代码包，开发者工具就自动会帮你恢复到当时你开发项目时的个性化配置，其中会包括编辑器的颜色、代码上传时自动压缩等等一系列选项。

其他配置项细节可以参考文档 [开发者工具的配置](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/edit.html#项目配置文件) 。