# vue-photo-preview

> \"基于photoswipe的vue图片预览插件\"

## 说明
1.简化了photoswipe的默认设置    
2.取消了图片需设定尺寸的要求    
3.默认关闭了分享按钮   
4.简化了html结构   

## 使用
``` bash
# 安装
npm install vue-photo-preview --save
```
```
# 引入
import preview from 'vue-photo-preview'
import 'vue-photo-preview/dist/skin.css'
Vue.use(preview)
//或者 
//var option={....} option配置请查看 http://photoswipe.com/documentation/options.html
//Vue.use(preview,option)
```
```
# umd
<link rel="stylesheet" type="text/css" href="路径/dist/skin.css"/>

<script src="路径/dist/vue-photo-preview.js" type="text/javascript" charset="utf-8"></script>
<script type="text/javascript">
	var options={
		fullscreenEl:false //关闭全屏按钮
	}
	
	Vue.use(vuePhotoPreview,options)
	
	new Vue({
		el:'#app'
	})
</script>
```
```
# html
//在img标签添加preview属性 preview值相同即表示为同一组
<img src="xxx.jpg" preview="0" preview-text="描述文字">

//分组
<img src="xxx.jpg" preview="1" preview-text="描述文字">
<img src="xxx.jpg" preview="1" preview-text="描述文字">

<img src="xxx.jpg" preview="2" preview-text="描述文字">
<img src="xxx.jpg" preview="2" preview-text="描述文字">
```

```
# 2018-09-28 更新
//添加对原插件photoswipe的事件响应，示例：
this.$preview.on('close',())=>{//close只是众多事件名的其中一个，更多请查看文档
	console.log('图片查看器被关闭')
})

//添加图片查看器实例--this.$preview.self 注意：此实例仅在图片查看器被打开时生效
this.$preview.on('imageLoadComplete',(e,item)=>{
	console.log(this.$preview.self)  //此时this.$preview.self拥有原插件photoswipe文档中的所有方法和属性
})

//demo文件夹中index.html可以供参考写法
//本次更新后继承了原插件的所有事件、方法和属性，如需复杂使用请多多查看[原插件文档](http://photoswipe.com/documentation/api.html) 

//应性能要求 新增大图查看 large标签填写大图路径 （插件的思路是 img的src默认为缩略图），如不填写large，则展示src
<img src="xxx.jpg" large="xxx_3x.jpg" preview="2" preview-text="描述文字">
```
```
# 2018-05-17 更新
//如果图片是异步生成的，在图片数据更新后调用：
this.$previewRefresh()
```


## Options   
[插件配置文档](http://photoswipe.com/documentation/options.html) 

## DEMO   
[地址](https://826327700.github.io/vue-photo-preview/demo/)  

