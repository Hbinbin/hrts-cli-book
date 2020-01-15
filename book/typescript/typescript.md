
## TypeScript的实用语法

### 1. 在window增加属性
#### 方法1：在`src/typings/index.d.ts`或react-app-env.d.ts中直接增加window的接口（推荐）

`src/typings/index.d.ts`
```
/// <reference types="./config.d.ts" />
/// <reference types="./common.d.ts" />
/// <reference types="./api.d.ts" />

// 增加此Window接口，此时可通过**window.Config**访问
interface Window {
  __REDUX_DEVTOOLS_EXTENSION__: Function;
  __wxjs_environment: any;
  ENV: any;
  Config: IConfig;
}

// 声明全局变量Config，此时可直接通过 Config 访问
declare const Config: IConfig;

```
在`src/index.tsx`中引入全局配置，给**Config**赋值
```
import '@common/config'; // 全局配置
```
`console.log(Config)`直接全局访问

#### 方法2：`src/index.tsx`中增加全局**window**声明
```
declare global {
  interface Window {
    __REDUX_DEVTOOLS_EXTENSION__: Function;
    __wxjs_environment: any;
    ENV: any;
    Config: any;
  }
}
```
### 2. 对于插件没有ts包的
```
// 在react-app-env.d.ts中增加
declare module 'react-lazy-load' {
  const LazyLoad: any
  export default LazyLoad
}
```
### 3. 匿名函数的this
回调中直接使用this会报错 'this 隐式具有类型 any，因为它没有类型注释' 

方法1：this必须作为回调的第一个参数传入，类型为：void | any
```
  ele.addEventListener('touchmove', function(this: any,evt: any) {
    console.log(this);
  })
```
方法2：tsconfig.js增加配置
```
"noImplicitThis": false
```
### 4. setState如何使用属性名表达式赋值
```
  interface IState{
  }
  type StateKey = keyof IState
  handleChange = (key: StateKey, val: any) => {
    this.setState({
      [key]: val
    } as Pick<IState, typeof key>)
  }
```
### 5. 对象、数组对象的表示
```
  const obj: {
    [key: string]: any
  } = {}
  const arrObj: {
    [key: string]: any
  }[] = []
```