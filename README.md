## 原生小程序 
### 微信小程序简述  
微信小程序，小程序的一种，英文名Wechat Mini Program，是一种不需要下载安装即可使用的应用，它实现了应用“触手可及”的梦想，用户扫一扫或搜一下即可打开应用。 
***
### 如何开发一个原生微信小程序（所需开发工具：微信开发者工具，VSCode） 
1.确认需求，确认UI，提前构思好开发思路和逻辑，开始动工；  
2.在[微信公众平台](https://mp.weixin.qq.com/)内添加开发人员，appid（如暂无appid可使用测试id号），将接口域名放进服务器域名内；  
3.创建一个微信小程序项目，将项目用vscode打开（强烈建议使用vscode开发工具来开发小程序，插件库里有很多支持微信小程序开发的插件，开发起来比较友好）；  
4.微信小程序使用mvvm模式框架，使用`{{}}`双大括号赋值，语法大致与vue相同，熟悉vue项目开发的同学相信不难开发小程序；  
5.在微信开发者工具中的某个文件夹右键可创建一个新的page，一个page包括wxml，js，json，wxss四个文件，其中wxml，js，wxss分别对应前端中的html，js，css文件，我们按照前端开发页面来开发就行，json文件为配置文件，页面的title，导航栏颜色以及各种配置可在此配置；  
ps:习惯用less预渲染的同学可以在vscode插件库搜索easy less插件并安装，安装该插件后，可在page文件夹内创建一个less后缀文件，插件默认会生成一个同名wxss后缀文件，并在每次保存less文件时同时编译wxss文件，使我们的开发效率大大提高；  
6.开发ing... （开发过程中可以使用工具内预览功能随时查看页面效果，或使用真机调试）；  
7.开发完成，点击微信开发者工具上传按钮，上传小程序至体验版（体验版并非线上版本，只能供体验权限的成员观看，可在微信公众平台内配置体验成员）； 
8.根据自身小程序的功能及定位选择类目，提交至线上版，自此，一个小程序从开发到发布的流程结束，等待官方审核，如审核失败则会提示你如何修改配置，如类目不匹配，违反微信相关规定等。  
***
### Q&A  
1.Q：小程序是否有体积限制，如何优化小程序体积及性能？  
  A：一个小程序包的体积上限为2m，我们可以通过以下方法来优化体积及性能：  
  （1）避免多次使用`this.setData()`赋值，尽量将多个值一次性用`this.setData()`赋值到data里；  
  （2）除了tabbar栏内的icon图片必须要用本地图片外，其他图片最好使用网络资源，图片资源占用是很大的，我们可使用cdn来保存并展示这些图片；  
  （3）分包加载，当我们的小程序项目确实庞大，小程序本身2m的体积限制满足不了我们的需求时，可以使用分包加载功能，该功能可以将我们的小程序体积限制最高提升到16m，并且可以同时开启分包预下载功能，进一步提升我们的项目性能。 参考文档：[分包加载](https://developers.weixin.qq.com/miniprogram/dev/framework/subpackages.html) [分包预下载](https://developers.weixin.qq.com/miniprogram/dev/framework/subpackages/preload.html)  
2.Q：为什么设置hidden属性不生效，有什么解决办法？  
  A：hidden的元素必须为block元素，不是block元素不生效该属性，说到底hidden也只是控制元素显隐，可使用`style='display: none'`来代替。  
3.Q：小程序如何引入组件？常用的组件有什么？  
  A：和vue项目一样通过npm引入，须在微信开发者工具-详情-本地设置中开启“使用npm模块”选项，一般本人使用的是vantUI组件库，更多组件根据项目需求可自行度娘。[小程序引入组件库（vant官方文档）](https://youzan.github.io/vant-weapp/#/quickstart#an-zhuang)  
4.Q：小程序可以在wxml内使用js语法吗？  
  A：具体请参考[wxs官方文档](https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxs/)，wxs并非js语言，他是小程序的一套脚本语言，部分js功能不能在wxs中使用，如es6语法，时间函数等。  
***
## uniapp
### uniapp多端开发工具简述  
uni-app 是一个使用 Vue.js 开发所有前端应用的框架，开发者编写一套代码，可发布到iOS、Android、H5、以及各种小程序（微信/支付宝/百度/头条/QQ/钉钉/淘宝）、快应用等多个平台。  
***
### uniapp和原生小程序对比有什么优点？  
1.一套代码可自动打包发布至多个平台，开发效率大大提高；  
2.使用vue.js开发语言，学习成本降低；  
3.uniapp小程序开发流程基本与原生小程序开发无异，uniapp开发工具内置多种优化手段，如自动合并`this.setData()`、分包加载、分包预下载、H5摇树优化、代码自动混淆等 参考文档：[官方文档（优化建议）](https://uniapp.dcloud.io/performance)    
4.uniapp有自己的插件市场，开发者可自行根据项目需求进行插件导入；[uniapp官方插件市场](https://ext.dcloud.net.cn/)   
5.uniapp可使用差异化编译，通过`#ifdef`、`#ifndef`条件编译进行各平台个性化实现 参考文档： [官方文档（条件编译）](https://uniapp.dcloud.io/platform)  
