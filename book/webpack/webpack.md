### 1. 配置模块的别名alias
在`src/config/webpack.config.js`中增加方法和alias配置
```
const resolvePath = function (dir) {
  return path.join(__dirname, '..', dir)
}
...
alias: {
  // 增加如下配置
  '@cps': resolvePath('/src/components'),
  '@redux': resolvePath('/src/redux'),
  '@utils': resolvePath('/src/utils')
}
...
```
在`src/tscongfig.json`文件中compilerOptions中加如下配置
```
...
"baseUrl": "src",
"paths": {
  "@cps/*": [
    "components/*"
  ],
  "@redux/*": [
    "redux/*"
  ],
  "@utils/*": [
    "utils/*"
  ]
}
```
### 2. 配置多页面入口
### 3. webpack生产打包去除console、debugger
webpack之前的打包压缩插件是uglifyjs-webpack-plugin，现在换成了terser-webpack-plugin  
修改文件：`src/config/webpack.config.js`
```
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
### 4. webpack打包去除.map文件
修改文件`src/config/webpack.config.js`中的devtool配置
```
devtool: isEnvProduction
      ? shouldUseSourceMap
        ? 'source-map'
        : false
      : isEnvDevelopment && 'cheap-module-source-map'
```
改为：
```
devtool: isEnvProduction
      ? false
      : isEnvDevelopment && 'cheap-module-source-map'
```