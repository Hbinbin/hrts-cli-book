# 模板的基本文件结构
<!-- api文件夹 -->
<!--sec data-title="api文件夹" data-id="api" data-show=true data-collapse=true ces-->
所有网络请求的api集中的文件夹，具体的写法可参照模板里的use.api.ts文件
```
// use.api.ts
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
所有的api可集中在api/index.ts中集中输出
```
// index.ts
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
全局常量集中存储在config.ts
```
// config.ts
export default class Config {
  /** 当前渠道 */
  static readonly CHANNEL = 'mall'
}
window.Config = Config;
```
注：要想在window上访问window.Config还需在入口文件引入以及在react-app-env.d.ts中加入以下代码：
```
interface Window {
  __REDUX_DEVTOOLS_EXTENSION__: Function;
  __wxjs_environment: 'miniprogram' | 'browser';
  Config: any;
}
```

参考文件结构： 
![](/assets/images/common.jpg)  

<!--endsec-->

<!-- components文件夹 -->
<!--sec data-title="components文件夹" data-id="components" data-show=true data-collapse=true ces-->
组件集中的地方  
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
redux状态管理文件集中管理的地方  
+ **rootReducer.ts**（所有reducer集中combine的文件）  
+ **selector.ts**（selector方法集中的地方）  
+ **other.redux.ts**  

参考文件结构：  
![](/assets/images/redux.jpg)  
<!--endsec-->

<!-- typings文件夹 -->
<!--sec data-title="typings文件夹" data-id="typings" data-show=true data-collapse=true ces-->
所有typescript接口  

具体的实用语法在[`typescript语法`章节](README.md)介绍

参考文件结构：  
![](/assets/images/typings.jpg)  
<!--endsec-->
<!--sec data-title="utils文件夹" data-id="utils" data-show=true data-collapse=true ces-->
工具方法集中的地方
<!--endsec-->