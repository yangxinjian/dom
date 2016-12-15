#Yeoman
##一、什么是Yeoman（官网http://yeoman.io/）

　　Yeoman帮助我们创建项目，提供更好的工具来使我们的项目更多样化。

　　Yeoman提供generator系统，一个generator是一个插件，在我们在一个完整的项目上使用‘yo’命令时，会运行该generator。通过这些官方的Generators，推出了Yeoman工作流，工作流是一个健壮、有自己特色的客户端堆栈，包含能快速构建漂亮的网络应用的工具和框架。Yeoman提供了负责开始项目开发的一切，没有任何让人头痛的手动配置。

　　采用模块化结构，Yeoman利用从几个开源社区网站学习到的成功和教训，以确保栈开发人员越来越智能的进行开发。基于良好的文档基础以及深思熟虑的项目构建过程，Yeoman提供测试和其他更多技术 ，因此开发人员可以更专注于解决方案而不用去担心其他小事。

　　Yeoman主要提供了三个工具：脚手架（yo），构建工具（grunt），包管理器（bower）。这三个工具是分别独立开发的，但是需要配合使用，来实现我们更高效的工作流模式。
##二、安装Yeoman  
###1.安装node.js（下载官网https://nodejs.org/en/download/）
###2.安装git（下载官网https://git-scm.com/downloads）
###3.windows下打开cmd，检查npm是否安装成功（npm --version）
###4.安装yeoman  
	npm install -g yo *环境变量的配置，将yo所在位置配置在path中，重启机器生效！
	
#####下载yeoman过程中，可以使用淘宝镜像，因为原下载的渠道在国外很慢
	在c盘用户下找到.npmrc文件，在后面补充添加registry=http://registry.npm.taobao.org
