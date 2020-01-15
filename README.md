#  hrts-cli是react-typescript的脚手架工具

用于快速的构建react-typescript项目，实现零配置且开箱即用。让前端开发只关心业务代码逻辑，而无需关心其他任何配置。

#  hrts-cli集成了react项目的最佳开发实践
是在create-react-app创建的项目下的二次封装，具体如下：
#### 1. eslint规则
+ **javascript**语法规则使用**standard**  
+ **react**语法规则使用**standard-react**  
+ **typescript**语法规则使用**typescript-eslint**  

{% em type="green" %}定制化的规则见项目模板的 **.eslint.js** 文件{% endem %}  
具体的规则参照对应的插件规则，传送门：[**standard**](https://github.com/standard/standard/blob/master/docs/README-zhcn.md) 
[**standard-react**](https://github.com/standard/eslint-config-standard-react) 
[**typescript-eslint**](https://github.com/typescript-eslint/typescript-eslint#readme)
#### 2. webpack配置
基本沿用 ```npm run eject```后的webpack配置，详细配置见：[`webpack配置`章节](./book/webpack/webpack.md)
#### 3. 集成的插件
+ **antd/antd-mobile** UI框架  
+ **axios** HTTP库  
+ **immutability-helper** 更好的操作不可变数据的插件，例如redux修改state，修改深层嵌套的数据时  
+ **reselect** redux的中间件，缓存redux的数据，减少计算和渲染压力  

传送门：[**antd**](https://ant.design/docs/react/introduce-cn) [**antd-mobile**](https://mobile.ant.design/docs/react/introduce-cn) [**axios**](http://www.axios-js.com/zh-cn/docs/) [**immutability-helper**](https://github.com/kolodny/immutability-helper#readme) [**reselect**](https://github.com/reduxjs/reselect#readme)