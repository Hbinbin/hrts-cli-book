### 用于快速创建组件模板

VSCode设置：`首选项`>`用户代码片段`>`新建全局代码片段文件`

#### 1. class组件
```
{
  "react": {
    "prefix": "react-class-ts",
    "body": [
      "import React, { Component } from 'react';",
      "import { connect } from 'react-redux';",
      "import { bindActionCreators, Dispatch } from 'redux';",
      "",
      "// interface",
      "interface IActions{ // redux的action集中放在这里",
      "}",
      "interface IProps{",
      "  actions: IActions;",
      "}",
      "interface IState{",
      "}",
      "",
      "class Name extends Component<IProps, IState> {",
      "  constructor (props: IProps) {",
      "    super(props);",
      "  }",
      "  readonly state: IState = {",
      "  }",
      "  render () {",
      "    return (",
      "      <div>",
      "      </div>",
      "    );",
      "  };",
      "}",
      "",
      "// connect",
      "const mapStateToProps = (state: any) => {",
      "  return {",
      "  };",
      "};",
      "const mapDispatchToProps = (dispatch: Dispatch) => {",
      "  return {",
      "    actions: bindActionCreators({}, dispatch)",
      "  };",
      "};",
      "export default connect(",
      "  mapStateToProps,",
      "  mapDispatchToProps",
      ")(Name);",
      ""
    ]
  }
}
```

### 2. hooks组件
```
{
  "react": {
    "prefix": "react-hooks-ts",
    "body": [
      "import React, { useState, useEffect } from 'react';",
      "import { connect } from 'react-redux';",
      "import { bindActionCreators, Dispatch } from 'redux';",
      "",
      "// interface",
      "interface IActions{ // redux的action集中放在这里",
      "}",
      "interface IProps{",
      "  actions: IActions;",
      "}",
      "interface IState{",
      "}",
      "",
      "function Name (props: IProps) {",
      "  const state: IState = {",
      "  };",
      "  return (",
      "    <div className=''>",
      "    </div>",
      "  );",
      "}",
      "",
      "// connect",
      "const mapStateToProps = (state: any) => {",
      "  return {",
      "  };",
      "};",
      "const mapDispatchToProps = (dispatch: Dispatch) => {",
      "  return {",
      "    actions: bindActionCreators({}, dispatch),",
      "  };",
      "};",
      "export default connect(mapStateToProps, mapDispatchToProps)(Name);",
      ""
    ]
  }
}
```