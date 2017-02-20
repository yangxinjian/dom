#Webpack随记
###Source Maps（使调试更容易）

开发总是离不开调试，如果可以更加方便的调试当然就能提高开发效率，不过打包后的文件有时候你是不容易找到出错了的地方对应的源代码的位置的，Source Maps就是来帮我们解决这个问题的。通过简单的配置后，Webpack在打包时可以为我们生成的source maps，这为我们提供了一种对应编译文件和源文件的方法，使得编译后的代码可读性更高，也更容易调试。
###/*__dirname是node.js中的一个全局变量，它指向当前执行脚本所在的目录。*/
###自动刷新
安装通过以下命令全局安装

	npm install --save-dev webpack-dev-server
	
	npm install webpack-dev-server -g

启动服务器

	
	webpack-dev-server --progress --colors
http://localhost:8080/index.html打开 对于 js 修改就自动更新了

	config配置
	devServer: {//自动监听代码的修改
		contentBase: "./public",//本地服务器所加载的页面所在的目录
		colors: true,//终端中输出结果为彩色
		historyApiFallback: true,//不跳转
		inline: true//实时刷新
	}
###Loaders的配置选项包括以下几方面：

test：一个匹配loaders所处理的文件的拓展名的正则表达式（必须）  
loader：loader的名称（必须）  
include/exclude:手动添加必须处理的文件（文件夹）或屏蔽不需要处理的文件（文件夹）（可选）；  
query：为loaders提供额外的设置选项（可选）
###webpack提供两个工具处理样式表
	
	css-loader 和 style-loader
二者处理的任务不同，css-loader使你能够使用类似@import 和 url(...)的方法实现 require()的功能,style-loader将所有的计算后的样式加入页面中，二者组合在一起使你能够把样式表嵌入webpack打包后的JS文件中。
