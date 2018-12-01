# wepy-datetime

小程序日期时间选择组件，支持同时选择日期和时间。最近开发的一个小程序有同时选择日期和时间的需求，
小程序原生的日期和时间选择组件都是只能选择其中一个，所以就自己造了个轮子。



## 依赖

* wepy https://github.com/Tencent/wepy
* moment https://github.com/moment/moment
* 小程序原生 `picker-view` 组件 https://developers.weixin.qq.com/miniprogram/dev/component/picker-view.html

## 使用

1、将 `src/components/datetimepicker.wpy` 拷贝到自己的项目

2、在使用页面引入和使用组件

```javascript
// js 中引入组件
import Datetimepicker from '<你的 datetimepicker 组件路径>';

//  js 中申明组件
components = {
      datetimepicker0: Datetimepicker,
      datetimepicker1: Datetimepicker,
      datetimepicker2: Datetimepicker,
      datetimepicker3: Datetimepicker,
      datetimepicker4: Datetimepicker
};
```

```html
<!-- template 中使用组件 -->
	
<!-- 组件默认配置 -->
<datetimepicker0 @change.user="changeTime0">
</datetimepicker0>

<!-- 配置时间选择格式 -->
<datetimepicker1
                 minuteStep="5"
                 timeFormat="HH:mm"
                 @change.user="changeTime1">
</datetimepicker1>

<!-- 取消时间选择 -->
<datetimepicker2
                 timeFormat=""
                 @change.user="changeTime2">
</datetimepicker2>

<!-- 取消日期选择 -->
<datetimepicker3
                 dateFormat=""
                 @change.user="changeTime3">
</datetimepicker3>

<!-- 自定义时间样式 -->
<datetimepicker4
                 defaultShow="false"
                 dateFormat=""
                 timeFormat="HH:mm"
                 :value.sync="{{datetime[4]}}"
                 @change.user="changeTime4">
    <span style="font-size: 20px; color: red">{{datetime[4]}}</span>
</datetimepicker4>
```

> 详细的使用 Demo 可以参考 `src/pages/index.wpy`。效果看最后截图。

## 参数说明

| 参数名字    | 类型   | 默认值     | 说明             | 实例 |
| ----------- | ------ | ---------- | ---------------- | ---- |
| value       | String | 当前时间   | 设置组件时间     |      |
| defaultShow | String | true       | 是否使用默认显示 |      |
| minuteStep  | Number | 1          | 分钟选择间隔     |      |
| dateFormat  | String | YYYY-MM-DD | 日期格式         |      |
| timeFormat  | String | HH:mm:ss   | 时间格式         |      |
| params      | any    | {}         | 用户参数         |      |

> 1. 传入的 value 格式必须和 dateFormat 和 timeFormat 匹配，中间用空格（` `）分隔

## 事件说明

| 事件名称 | 说明                             |
| -------- | -------------------------------- |
| change   | 当用户改变时间值时触发事件       |
| confirm  | 当用户点击 `确定` 按钮时触发事件 |
| cancel   | 当用户点击`背景区域`时触发事件   |

### 事件参数

所有时间参数格式一样

```json
{
    value: '组件当前时间'
    params: '用户传入的 params 参数，数据类型和格式由传入值决定'
}
```



## 方法说明

| 方法名称 | 说明                                   |
| -------- | -------------------------------------- |
| input    | 通过 JS 调用打开 `datetimepicker` 组件 |

实例

```javascript
// js 中引入组件
import Datetimepicker from '<你的 datetimepicker 组件路径>';

//  js 中申明组件
components = {
      datetimepicker: Datetimepicker
};

// 在方法中调用 input 打开组件
methods = {
      onOpenDatetime() {
        this.$invoke('datetimepicker', 'input', {});
      }
}
```

# Demo 截图

![](https://ws3.sinaimg.cn/large/006tNbRwly1fxr2n4s2toj30ku1120tv.jpg)

![](https://ws2.sinaimg.cn/large/006tNbRwly1fxr2nquzjcj30ku112q3z.jpg)

![](https://ws1.sinaimg.cn/large/006tNbRwly1fxr2od6dtrj30ku112jsk.jpg)

![](https://ws2.sinaimg.cn/large/006tNbRwly1fxr2os4ca4j30ku112ab6.jpg)

![](https://ws3.sinaimg.cn/large/006tNbRwly1fxr2p246yij30ku1123zh.jpg)
