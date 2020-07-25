


# vue-super-flow
* A flowchart editor component base on Vue.
* Vue flowchart.
* 一个基于 Vue 的在线流程编辑组件。
* [Demo](https://caohuatao.github.io/demo/)
* [docs](https://caohuatao.github.io)

## Installation

```
v1.3.1
```

```npm

npm install vue-super-flow

yran add vue-spuer-flow

```
```js

import SuperFlow from 'vue-super-flow'
import 'vue-super-flow/lib/index.css'

Vue.use(SuperFlow)

```

## Attributes

|属性                |类型                |默认值                   |描述                                     | 
|----                | ----              |----                     |----                                     |
|draggable           |`Boolean`          |`true`                   | 是否开启节点拖拽                         |
|linkAddable         |`Boolean`          |`true`                   | 是否开启快捷创建 `link`                  |
|linkEditable        |`Boolean`          |`true`                   | `link` 是否可编辑                       |
|hasMarkLine         |`Boolean`          |`true`                   | 是否开启拖拽辅助线                       |
|markLineColor       |`String`           |`#55abfc`                | 辅助线颜色                               |
|origin              |`Array`            |`[0, 0]`                 | `graph` 的二维坐标系原点                 |
|nodeList            |`Array`            |`[]`                     | 初始化节点列表                           |
|linkList            |`Array`            |`[]`                     | 初始化连线列表                           |
|graphMenu           |`Array`            |`[]`                     | `graph` 的右键菜单列表配置               |
|nodeMenu            |`Array`            |`[]`                     | `node` 右键菜单列表配置                  |
|linkMenu            |`Array`            |`[]`                     | `link` 右键菜单配置                      |
|enterIntercept      |`Function`         |`() => true`             | 创建连线进入节点限制                     |
|outputIntercept     |`Function`         |`() => true`             | 节点生成连线限制函数                     |
|[linkDesc](#linkdesc)           |`Function`           |`null`           | 生成 `link` 定制描述文字           |
|[linkStyle](#linkstyle)         |`Function`           |`null`           | 根据 `link` 定制样式               |
|[linkBaseStyle](#linkbasestyle) |`Object`             |`{}`             | 连线默认样式配置                    |


### linkDesc
```js
function linkDesc(link) {
   /**
     根据 link 对象的属性判断定制连线描述
   */
   return link.meta ? link.meta.info : ''
}
```

### linkBaseStyle
```json5
/*
// 内置默认样式配置
{
   hover: '#FF0000',        // 连线 hover 时颜色
   color: '#666666',        // 连线颜色
   textColor: '#666666',    // 连线描述文字颜色
   textHover: '#FF0000',    // 连线 hover 时描述文字颜色
   font: '14px Arial',      // 连线 描述文字 font 参考 https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/font
   dotted: false,           // 连线 是否是虚线
   lineDash: [4, 4],        // 为虚线时 虚线参数  参考：https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/setLineDash
   background: 'rgba(255,255,255,0.6)'  // 描述文字背景  
}
*/

{
  // ... 可选属性 参考内置默认样式 用来覆盖连线样式的默认值
}
```

### linkStyle
```js
function linkStyle(link) {
   /**
     1、根据 link 对象的属性判断定制连线样式
     2、描述非字符串或为空时不会渲染描述文字
   */
   return {
      // ... 可选属性 参考：[linkBaseStyle](#linkBaseStyle)
   }
}
```



## Methods

|方法名               |说明                                        |参数                                    | 
|----                | ----                                       |----                                    |
|selectedAll         | 选中所有进行拖拽修改 `origin`               |----                                    |
|toJSON              | 将 `graph` 对象转为普通 json 对象           |----                                    |
|getMouseCoordinate  | 获取当前鼠标在 `graph` 坐标系的坐标          |clientX, clientY                        |
|addNode             | 添加节点                                    |options                                 |

## Examples

![例1](https://s1.ax1x.com/2020/07/11/UQ3IsJ.gif)

![例2](https://s1.ax1x.com/2020/07/11/UQ37ZR.gif)

![例3](https://s1.ax1x.com/2020/07/11/UQ3oL9.gif)
