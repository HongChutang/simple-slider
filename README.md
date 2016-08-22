# Simple_Slider
A Simple Slider Build on Vuejs.

一个简单的轮播组件，使用Vuejs制作，支持父组件直接嵌套使用，利用props传送配置参数，参数有：  

1. items: Json格式图片数组，元素为对象，有两个字段，一个为图片链接src，一个为图片替代文本；
2. count: 图片数组元素数量，默认为4；
3. speed: 轮播切换图片的速度，默认为1.5秒每张；
4. delay: 自动轮播时停留的时间，默认为2秒；
5. paus: 鼠标放上图片是否停止自动轮播，默认为true；
6. autoplay: 是否自动轮播，默认为true；
7. dots: 是否需要显示轮播切换定位点，默认为true；
8. arrows: 是否需要显示左右点击切换箭头，默认为true。

其中，items,count为必须传的配置参数，其他可以不传而使用默认值。
