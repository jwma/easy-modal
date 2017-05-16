一个简单的Vue模态组件
===
写这个组件的的目的是为了：
* 尝试使用 Webpack + Vue 封装一个独立的 Vue 组件，以便于能在不同的使用环境使用；
* vue-loader 搭配 Sass-loader、Postcss 简化组件样式开发；

Modal 类型
---
EasyModal 有两种类型：
1. 较为常规的模态层，包含标题、主体内容、关闭、确定按钮、取消按钮、蒙层；
2. 完全自定义 Modal 主体部分加上蒙层；

使用
---
详细可以查看 [index.html](./index.html) 