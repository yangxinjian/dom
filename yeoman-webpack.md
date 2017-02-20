#Yeoman -- webpack -- react

##Yeoman的含义
Yeoman ： yo ------ 脚手架
<div style="margin-left:70px">grunt ------ 构建工具 </div>

<div style="margin-left:70px">bower ------ 包管理器 </div>
##Yeoman的特性

###闪电般的初始化：  
项目开始阶段，可以基于现有的模板框架（例如：HTML5 Bolierplate、Twitter Bootstrap）进行项目初始化的快速构建。  
###了不起的构建流程： 
不仅仅包括JS、CSS代码的压缩、合并，还可以对图片和HTML文件进行优化，同时对CoffeScript和Compass的文件进行编译。  
###自动编译CoffeScript和Compass：  
通过LiveReload进程可以对源文件发生的改动自动编译，完成后刷新浏览器。  
###自动Lint代码：  
对于JS代码会自动进行JSLint测试，确保代码符合最佳编程实践。  
###内置的预览服务器：  
不再需要自己配置服务器了，使用内置的就可以快速预览。  
###惊人的图片优化：  
通过使用OptiPNG和JPEGTran来优化图片，减少下载损耗。  
###杀手级包管理：  
通过bower search jQuery，可以快速安装和更新相关的文件，不再需要打###开浏览器自己搜索了。  
###PhantomJS单元测试：  
可以非常方便的使用PhantomJS进行单元测试，一切在项目初始的时候都准备好了。 
###自动刷新
网页内容设置好后，每一次修改，内容会自动刷新，不需要手动操作  
##Yeoman的安装
###第一步：  
安装node.js：在官网下载，自定义默认安装，在cmd中运行npm -v查看是否完成安装，需要在环境变量中配置node，（找到node的文件夹，进入到bin，复制地址到环境变量中即可）
###第二步：
接下来安装yeoman  

       npm install -g yo(-g代表全局安装)
由于我们下载的地址来自于国外，网速会很慢，我们可以使用淘宝镜像，在搜索中找到.npmrc文件，之后双击打开，进入页面之后，在末尾添加

		registry=http://registry.npm.taobao.org

添加后保存，在执行安装命令  
##Yeoman--React--webpack使用
###Yeoman的官网  ------  http://yeoman.io/generators/
###项目的建立
为了防止我们的项目会有意外的损坏，我们在github上新建项目，并在本地的盘中（建议盘中有一个workspace的工作空间）clone下我们的github的项目(github上有明确命令步骤)  
<span style="color:red">注意*</span>	必须在有git的前提下哦

###Yeoman的react使用
在官网的discoveirng generators中搜索到react(如果要使用angular，直接搜索angular即可)，我们会看到react-webpack，点击进去  
在cmd中运行

		npm install -g generator-react-webpack
之后在cmd中进入到我们的项目，运行  
	
		yo react-webpack

成功后打开我们的项目
##项目组成的介绍
####src文件夹：  
	源代码所在目录  
####test文件夹：
	测试代码所在目录
####.editorconfig文件  
	同来统计、适应不同版本的编辑器
####.jshintrc文件
	一般以hint、lint为中心，均为代码风格检测工具，子不过hint不支持JSX语法
####.yo-rc文件  
	当前项目的信息
####Gruntfile.js
	grunt自动编译的配置文件（新版的generator已经没有这个了）
####karma.conf.js
	测试框架的配置文件
####package.json
	node下项目的配置文件，生成当前项目都依赖了哪儿些npm包
####webpack.config.js
	webpack的开发环境
####webpack.dist.config.js
	webpack的生产环境
	


