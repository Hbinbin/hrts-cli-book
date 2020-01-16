### 代码分割与路由
之前模块代码分割、代码的动态引入需要插件如：`react-loadable`，或者使用`import()`，在react16.8版本后可以使用`React.lazy()`，下面展示结合react-router的代码分割：

`routeConfig.ts`
```
const MallHome = React.lazy(() => import('@cps/mallHome'))
const MallCart = React.lazy(() => import('@cps/mallCart'))
const MallUser = React.lazy(() => import('@cps/mallUser'))
const routes = [
  {
    path: '/mall',
    component: MallHome
  },
  {
    path: '/cart',
    component: MallCart
  },
  {
    path: '/user',
    component: MallUser
  }
]
```
入口：
```
<Suspense fallback={null}>
  <Switch>
    <Route exact path='/' render={() => <Redirect to={this.handleEntry()} />} />
    {
      routes.map((route, i) => {
        return (
          <Route
            key={i}
            exact
            path={route.path}
            // component={route.component} // 此种引入方法，某些react版本会报ts的错误，如果报错可采用下面render的方法
            render={props => (
               <route.component {...props} />
             )}
          />
        )
      })
    }
  </Switch>
</Suspense>
```