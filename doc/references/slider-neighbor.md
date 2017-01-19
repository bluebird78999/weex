# Slider-neighbor

mx_time
0.11
mx_time

The <slider-neighbor> component provides similar features with the <slider> component. The <slider-neighbor> component is used to  show slides (mostly as pictures) one page by another with animation. 

## Child Components

It supports all kinds of weex components as its slides, especially the `indicator` component which only can be used as a child component of `slider`  and a child component of `slider-neighbor`.

## Attributes

* `auto-play`: <boolean> `true` | `false`. This value determines whether the `slider-neighbor`  component play automatically after the page rendering finished. The default value is `false`.
* `interval`: <number> millisecond. This value determines time interval for each page displayed in `slider-neighbor` component.The default value is `3000`.
* `index`: <number> . This value determines the index of current shown slide. The default value is `0`.
* `currentItemScale`: <float> . This value determines the scale of current shown slide. The default value is `0.9`.
* `neighborScale`: <float> . This value determines the scale of neighbor shown slide. The default value is `0.8`.
* `neighborSpace`: <float> . This value determines the space between neighbor shown slides and current shown slide. The default value is `25`.
* `neighborAlpha`: <float> . This value determines the alpha of neighbor shown slides when slide the slides. The default value is `0.6`.
* `scrollable`: <boolean> . This value determines whether the `slider-neighbor` is scrollable. The default value is `True`.

Other attributes please check out the [common attributes](https://weex-project.io/doc/references/common-attrs.html).

## Styles

common styles: check out [common styles for components](http://alibaba.github.io/weex/doc/references/common-style.html)

* support flexbox related styles
* support box model related styles
* support position related styles
* support opacity, background-color etc.


## Events

- `change`: triggerd when the index of `slider-neighbor` is changed. The event object contains the attribute of `index`, which is the index number of the currently shown slide.

**common events**: check out the [common events](https://weex-project.io/references/references/common-event.html)

- support `click` event. Check out [common events](https://weex-project.io/references/references/common-event.html)
- support `appear` / `disappear` event. Check out [common events](https://weex-project.io/references/references/common-event.html)


## example

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

