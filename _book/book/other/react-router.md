### vconsole插件的使用
用于手机端H5调试

安装vconsole
```
npm i vconsole --save-dev
```
在入口文件index.tsx中import且创建vcosole实例
```
import VConsole from 'vconsole'
const vConsole = new VConsole()
```
在typescript中引入会报找不到对应ts的模块，在react-app-env.d.ts中增加全局声明:  
```
declare module 'vconsole'
```

