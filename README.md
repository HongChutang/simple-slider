# Simple_Slider
A Simple Slider Build on Vuejs.

一个简单的轮播组件，使用Vuejs制作，支持父组件直接嵌套使用，利用props传送配置参数，参数有：  

1. items: Json格式图片数组，元素为对象，有三个字段，分别为图片地址src、图片点击路由路径link（使用vue-router构建的单页面应用中的路由对应组件路径），图片替代文本alt；
2. count: 图片数组元素数量，默认为4；
3. speed: 轮播切换图片的速度，默认为1.5秒每张；
4. delay: 自动轮播时停留的时间，默认为2秒；
5. paus: 鼠标放上图片是否停止自动轮播，默认为true；
6. autoplay: 是否自动轮播，默认为true；
7. dots: 是否需要显示轮播切换定位点，默认为true；
8. arrows: 是否需要显示左右点击切换箭头，默认为true。

其中，items,count为必须传的配置参数，其他可以不传而使用默认值。  

功能很简单，长得也很简单：  
![组件图片](https://github.com/HongChutang/pictures_bed/blob/master/pic_0806/pic_0822.PNG?raw=true)

代码还是很简单的，扩展性由于是基于vue肯定挺好，在具体使用中可以根据需要修改还是不错的。
