# Slider-neighbor

mx_time
0.9
mx_time

`slider-neighbor` 组件提供与`slider` 组件类似的功能。 `slider-neighbor`用来滑动显示一张一张的幻灯片（主要是图片），滑动过程中伴随有动画效果。 

## 子组件

它支持所有类型的weex组件作为其幻灯片，尤其是只能作为`slider`和`slider-neighbor`子组件的`indicator`组件。

## 属性

* `auto-play`: <boolean> `true` | `false`设置幻灯片是否自动播放，默认值是 `false`。
* `interval`: <number> 单位是毫秒。设置幻灯片切换的间隔时间，默认值是`3000`。
* `index`: <number>  设置初始化时显示的幻灯片索引值，默认是 `0`。
* `currentItemScale`: <float> 当前（居中）显示的幻灯片的缩放比例，默认值是`0.9`。
* `neighborScale`: <float> 设置两边显示的幻灯片的缩放比例，默认值是 `0.8`。
* `neighborSpace`: <float> 设置两边显示的幻灯片与居中显示的幻灯片的间距，默认值是 `25`。
* `neighborAlpha`: <float> 设置两边显示的幻灯片在滑动时的透明度，默认值是 `0.6`。
* `scrollable`: <boolean>设置组件是否可以滚动幻灯片，默认值是`True`。

其它属性请查看 [通用属性](https://weex-project.io/cn/references/index.html).

## 样式

* 通用样式：支持所有通用样式，查看 [组件通用样式](https://weex-project.io/cn/references/common-style.html)
  - 盒模型
  - `flexbox` 布局
  - `position`
  - `opacity`
  - `background-color`


## 事件

- `change`: 当轮播索引改变时，触发该事件。

  事件中 event 对象属性：

  - `index`：展示的图片索引

- 通用事件

  支持以下事件：

  - `click`
  - `appear`
  - `disappear`

  查看 [通用事件](https://weex-project.io/cn/references/common-event.html)



## 示例

```html
<template>
	<div style="flex-direction: column; background-color: #ffffff;width:750;height:600;border-width: 0;">
		<div style="width:700;height:400; border-width:1; border-style:solid; border-color:#000000;margin:0;">
		<slider-neighbor style="width:700;height:400;" neighbor-scale="0.8" neighbor-space="30" current-item-scale="0.90" interval="3000" neighbor-alpha="0.8" auto-play="{{attr_auto_play}}" index=1>
				<image style="width:600;background-color:#FFFFDF;height:400;" src="https://gw.alicdn.com/tps/TB1dzanMVXXXXXQXVXXXXXXXXXX-573-412.png"></image>
				<image style="width:600;background-color:#FFFFDF;height:400;" src="https://gw.alicdn.com/tps/TB1p9CCMVXXXXa_XFXXXXXXXXXX-450-340.png"></image>
				<image style="width:600;background-color:#FFFFDF;height:400;" src="https://gw.alicdn.com/tps/TB1zpSiMVXXXXchXFXXXXXXXXXX-448-338.png"></image>
				<image style="width:600;background-color:#FFFFDF;height:400;" src="https://gw.alicdn.com/tps/TB1EuGIMVXXXXcoXpXXXXXXXXXX-452-337.png"></image>
			<indicator style="height:60;position:absolute;bottom:15;width:700;left:0;itemSelectedColor:#0000FF;itemSize:20;itemColor:#FF0000;"></indicator>
		</slider-neighbor>
		</div>
		<div style="height:100; border-width:0; margin:10;">
			<TC_Support_SubTitle title="auto-play"></TC_Support_SubTitle>
			<div repeat="btnList2100" style="flex-direction:row">
				<text onclick="update2100" flagid="{{index}}" repeat="row" style="width:310; height:50;text-align: center; border-width: 1;border-color: #696969;border-style:solid;border-radius:5; margin:10; background-color: {{bgc}}">auto play: {{value}}</text>
			</div>
		</div>
	</div>
</template>


<script>
	module.exports = {
		data : {
			log_detail:[],
			attr_auto_play:false,
			btnList2100: [
				{row:
					[
						{value: "false",bgc:'#EEEEEE',index:0},
						{value: "true",bgc:'#EEEEEE',index:1},
					],
				},
			],
		},
		methods : {
			update2100: function (e) {
				var self = this
				var index = e.target.attr.flagid
				for (var i = 0; i < self.btnList2100.length; i++) {
					var row = self.btnList2100[i];
					var columnlist = row.row;
					for (var j = 0; j < columnlist.length; j++) {
						var column = columnlist[j];
						if (column.index === index) {
							column.bgc = '#B2DFEE'
							switch (index) {
								case 0:
									self.attr_auto_play=false;
									break;
								case 1:
									self.attr_auto_play=true;
									break;
								default:
									break;
							}
						}
						else {
							column.bgc = '#EEEEEE'
						}
					}
				}
			},
		},
	}
</script>
```

[try it](http://dotwe.org/f9b8552db4c633d1543955ee4c6e24f5)