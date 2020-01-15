# 模板的基本文件结构
<!-- api文件夹 -->
<!--sec data-title="api文件夹" data-id="api" data-show=true data-collapse=true ces-->
所有网络请求的api集中的文件夹  
具体的写法可参照模板里的`src/api/user.api.ts`文件：
```
export default class UserAPI {
  /** 获取用户信息API */
  private static readonly USER_API = 'IAccountRoles/getUser';
  /**
   * 获取用户信息
   * @static
   * @param {string} mobile - 用户手机号
   */
  static async getUser ({ mobile }: IGetUserParams) {
    const url = 'xxxx' + this.USER_API;
    const params = {
      mobile
    };
    return axios.post(url, params);
  }
}
```
所有的api可集中在`src/api/index.ts`中集中输出：
```
export { default as UserAPI } from './user.api';
...other api
```

参考文件结构：  
![](/assets/images/api.jpg)  
<!--endsec-->

<!-- assets文件夹 -->
<!--sec data-title="assets文件夹" data-id="assets" data-show=true data-collapse=true ces-->
所有样式、图片、字体集中的地方
+ **css**
  + **common**（公共组件样式文件夹）  
    index.scss（公共组件样式在此集中输出）  
    some-common-component.scss  
  + **index.scss**（所有组件样式在此集中输出）  
  + **some-component.scss**  
+ **iconfont**（图标、字体文件）  
+ **images**（图片）  

参考文件结构：  
![](/assets/images/assets.jpg)  
<!--endsec-->

<!-- common文件夹 -->
<!--sec data-title="common文件夹" data-id="common" data-show=true data-collapse=true ces-->
全局配置，全局方法集中在此文件夹  
全局常量、方法集中存储在`src/common/config.ts`：
```
/** 项目全局配置 */
export default class Config implements IConfig {
  /** 开发环境 */
  static readonly ENV = 'dev';
  /** 当前渠道 */
  static readonly CHANNEL = 'mall';
}
window.Config = Config;
```
注：要想在window上访问window.Config或全局访问Config，参考：[`实用的typescript特性`章节](../typescript/typescript.md)

参考文件结构： 
![](/assets/images/common.jpg)  

<!--endsec-->

<!-- components文件夹 -->
<!--sec data-title="components文件夹" data-id="components" data-show=true data-collapse=true ces-->
组件集中的文件夹  
{% em type="orange" %}此处的文件规范应该是比较灵活的，根据不同的项目可自行搭配，如手机商城项目会根据底部的tabbar分为三个模块文件夹，每个模块有index.tsx文件来管理router{% endem %}  

+ **common**（公共组件文件夹）  
    index.ts（公共组件在此集中输出）  
    SomeCommonComponent.tsx  
+ **component1**（组件component1文件夹）  
    component1.tsx  
+ **component2**（组件component2文件夹）  
    component2.tsx  
+ **index.tsx**（在此处可做路由router的管理）  

参考文件结构：  
![](/assets/images/components.jpg)  
<!--endsec-->

<!-- redux文件夹 -->
<!--sec data-title="redux文件夹" data-id="redux" data-show=true data-collapse=true ces-->
redux状态管理文件集中管理的文件夹  
+ **rootReducer.ts**（所有reducer集中combine的文件）  
+ **selector.ts**（selector方法集中的地方）  
+ **other.redux.ts**  

参考文件结构：  
![](/assets/images/redux.jpg)  
<!--endsec-->

<!-- typings文件夹 -->
<!--sec data-title="typings文件夹" data-id="typings" data-show=true data-collapse=true ces-->
typescript接口集中管理的文件夹  

具体的实用语法在[`实用的typescript特性`章节](../typescript/typescript.md)介绍  

#### 方式1：通过模块的方式，全局访问接口
`src/typings/api.d.ts`定义一个接口：
```
interface IGetUserParams {
  mobile: string;
}
```

`src/typings/index.d.ts`集中引入模块：
```
/// <reference types="./config.d.ts" />
/// <reference types="./common.d.ts" />
/// <reference types="./api.d.ts" />

interface Window {
  __REDUX_DEVTOOLS_EXTENSION__: Function;
  __wxjs_environment: any;
  ENV: any;
  Config: IConfig;
}

declare const Config: IConfig;
declare const ENV: any;
```
`src/tsconfig.json`的`include`选项增加配置：
```
"include": [
  "src",
  "src/typings/index.d.ts"
]
```
参考文件结构：  
![](/assets/images/typings1.jpg)  

#### 方式2：定义不同的接口文件`.ts` 在需要类型的地方`import`引入
`src/typings/api.typings.ts`定义一个接口：
```
export interface IGetUserParams {
  mobile: string;
}
```

`src/typings/user.api.ts`引入并使用接口：
```
import { IGetUserParams } from '@typings';
export default class UserAPI {
  ...some code
  static async getUser ({ mobile }: IGetUserParams) {
    ... some code
  }
}
```

参考文件结构：  
![](/assets/images/typings2.jpg)  
<!--endsec-->
<!--sec data-title="utils文件夹" data-id="utils" data-show=true data-collapse=true ces-->
工具方法集中的地方
<!--endsec-->