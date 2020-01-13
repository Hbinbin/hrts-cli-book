
### 1.安装hrts-cli脚手架工具
全局安装hrts-cli
```
npm i hrts-cli -g
```
### 2.新建项目
初始化项目模板
```
hrts-cli init [项目名称]
```
### 3.安装依赖、启动项目
mac终端执行
```
sh init.start.sh
```
或
```
npm i
npm start
```
### 4.编辑器设置（vscode）
代码保存自动修复的配置：修改vscode的配置文件 **settings.json**
```
// 增加需要自动修复的语言
  "eslint.validate": [
    ...
    "html",
    "javascript",
    "react",
    "typescript",
    "typescriptreact",
    ...
  ],
  // 开启自动修复
  "eslint.autoFixOnSave": true,（此设置已废弃）
  此项已修改为：
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
```

**注：{% em type="orange" %}配置完不生效时，请重启编辑器{% endem %} **
