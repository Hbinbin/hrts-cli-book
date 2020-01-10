#### 1.vconsole调试插件的引入
`$ npm i vconsole --save-dev`
在入口文件index.tsx中import且创建vcosole实例
```
import VConsole from 'vconsole'
const vConsole = new VConsole()
```
在typescript中引入会报找不到对应ts的模块，在react-app-env.d.ts中增加全局声明:  
```
declare module 'vconsole'
```

#### 2.webpack生产打包去除console、debugger
```
// webpack之前的打包压缩插件是uglifyjs-webpack-plugin，现
在换成了terser-webpack-plugin
// webpack.config.js增加如下代码
  new TerserPlugin({
    terserOptions: {
      ...somecode
      compress: {
        ecma: 5,
        warnings: false,
        comparisons: false,
        inline: 2,
        drop_debugger: true, // 去除所有的debugger
        drop_console: true // 去除所有的console
      },
      ...somecode
    },
```
#### 3.webpack打包去除.map文件
```
// 修改webpack.config.js中的devtool配置
devtool: isEnvProduction
      ? shouldUseSourceMap
        ? 'source-map'
        : false
      : isEnvDevelopment && 'cheap-module-source-map'
改为：
devtool: isEnvProduction
      ? false
      : isEnvDevelopment && 'cheap-module-source-map'
```