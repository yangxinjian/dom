
#bootstrap知识点清单  
####1.bootstrap3 优先于移动设备，需要在头部添加    

    <head>
    	<meta name='viewport' content='width=device-width,initial-scale=1.0'>
    </head>  
width=device-width：设置设备的宽度可以自适应设备  
initial-scale=1.0：当页面加载时，最初的比例为1：1，不产生缩放  
user-scalable=no:禁止页面在设备上缩放  
maximum-scale=1.0 ：设置最大的页面比例，产生滚动的效果  
####2.响应式图像 ----让图像对响应式布局更友好  
    
    <img src='' class='img-responsive' alt='响应式布局'> 
(1)height:auto; 自适应高度  
(2)display:inline-block; 呈内联样式，可以改变高度和宽度  
(3)max-width='100%'; 重写width指定的宽度  
####3.容器(Container)  
设置了内填充左右各15px ,外边距左右自适应，一般放在大的div下，确保居中

####4.网络布局  
在容器里面添加行row ，行中添加列col,一行共有12各单元格 
    
    <div class="row">
		<div class="col-md-6"></div>//6代表占据了6个单元格
		<div class="col-md-6"></div>//6代表占据了6个单元格
		//确保数字相加等于12
	</div>   
xs、ms、md、lg形成自适应布局
####5.bootstrap里的强调

    <p class="text-left">向左对齐文本</p>
	<p class="text-center">居中对齐文本</p>
	<p class="text-right">向右对齐文本</p>
	<p class="text-muted">本行内容是减弱的,呈灰色</p>
	<p class="text-primary">呈浅蓝色</p>
	<p class="text-success">呈绿色</p>
	<p class="text-info">呈深蓝色</p>
	<p class="text-warning">呈黄色</p>
	<p class="text-danger">呈红色</p>  
####6.缩写
	
	<attr title="wholeworldwide" class='initailism'>www</attr>  
title：缩写的全称；  
class='initailism'：是缩写的部分更小一点  
####7.列表  
无序列表中，添加 class="list-unstyled" 可使列表样式清空  
无序列表中，添加 class="list-inline" 可使列表样式在同一行显示
定义列表中，添加 class="dl-horizontal" 可使dt、dd水平显示  
####8.表格  
    .table	//为<table>添加横向分隔线
    .table-striped	//在 <tbody> 内添加斑马线形式的条纹 (IE8不支持)（蓝白相间）
	.table-bordered	//为所有表格的单元格添加边框	
	.table-hover	//在 <tbody> 内鼠标滑过颜色有钱变深
	.table-condensed	//让表格更加紧凑
	.active		//将悬停的颜色应用在行或者单元格上
	.success	//表示成功的操作
	.info		//表示信息变化的操作
	.warning	//表示一个警告的操作
	.danger		//表示一个危险的操作
将table嵌套在class="table-responsive"的div下会产生横向滚动自适应屏幕的大小  
####9.表单  
	向父 <form> 元素添加 role="form"。
	把标签和控件放在一个带有 class .form-group 的 <div> 中--控制空间之间的间距
	向所有的文本元素 <input>、<textarea> 和 <select> 添加 class .form-control--调节间距和本身的格式
bootstrap默认空间的宽是100%；  
如果需要表单内联，向左对齐  

	在<form> 标签添加 class .form-inline。
btn-default：使 button 更美观好看  
.控件-inline 使内容在同一行显示  
select 中 multiple="multiple" 可以设置选择多个选项  
p标签内class .form-control-static 是这是静态显示，多用于纯文字  
控件填入 disabled 表示不可以操作该控件  
has-success、has-warning、has-error分别是绿色、黄色、红色输入框（input）  
用 class .input-lg/.input-sm 和 .col-lg-* 来设置表单的高度和宽度  
class="help-block"--帮助文本，字体为浅灰色  
####10.按钮
.btn-default ---------默认/标准按钮  
.btn-primary ---------原始按钮样式  
.btn-success ---------表示成功的动作  
.btn-info ---------该样式可用于要弹出信息的按钮  
.btn-warning ---------表示需要谨慎操作的按钮  
.btn-danger ---------表示一个危险动作的按钮操作  
.btn-link ---------让按钮看起来像个链接 (仍然保留按钮行为)  
.btn-lg ---------制作一个大按钮  
.btn-sm ---------制作一个小按钮  
.btn-xs ---------制作一个超小按钮  
.btn-block ---------块级按钮(拉伸至父元素100%的宽度)  
.active ---------按钮被点击  
.disabled ---------禁用按钮  
####11.图片  
.img-rounded： ---------添加 border-radius:6px 来获得图片圆角。  
.img-circle： ---------添加 border-radius:50% 来让整个图片变成圆形。  
.img-thumbnail： ---------添加一些内边距（padding）和一个灰色的边框。  
####12.布局控件
#####(1) 下拉菜单  
------------class='dropdown-toggle'  
#####(2) 按钮组  
------------class='btn-group'  
#####(3) 嵌套  
------------在大框里面添加data-toggle="dropdown" 在嵌套的部分添加class="dropdown-menu"  
#####(4) 输入框组  
------------class="input-group"  
#####(5) 导航菜单  
------------<b>ul</b> 里面放置*nav-tabs *nav-pills（nav-stacked垂直，.nav-justified两端对齐界面平分）<b>li</b> 里面哪儿个已显示放置class='active',禁用的放置class='disabled'   
#####(6) 徽章  
------------ class="badge"(class='pullright'向右对齐)  
#####(7) 缩略图  
------------ class="thumbnail"  
#####(8) 进度条  
------------ class="progress-bar" style="width: 20%;"（ progress-striped增添了条纹）（ active让进度条动起来）  
#####(9) 面板  
------------ class="panel panel-default"（里面包含div可以分为class="panel-body"、class="panel-footer"、class="panel-header"）
####13.插件(http://www.runoob.com/bootstrap/bootstrap-transition-plugin.html)
(1)Model------------点出新的页面框  
(2)Tab------------导航条切换  
(3)Carousel------------轮播  
(4)Tooltip------------提示工具  
(5)Popover------------弹出框（类似于对话的框）  
(6)Accordion------------折叠面板（ul li下的ul li）