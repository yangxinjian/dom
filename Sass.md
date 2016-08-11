#Sass
Sass可以简化Css工作流，并使Css的扩展和维护工作变的更加容易！
####sass安装命令  
linux ： sudo su -c "gem install sass"  
windows ： gem install sass ； sass  -v

####sass 书写
sass没有{}、和 ' ; ' , 用两个空格缩进代表代码的嵌套  

	#sky
      display: block
      width: 120px
      height: 600px
####scss书写
scss书写几乎与css一样。有 { } 和 ' ;   '
##用法
###1.变量
sass里可以使用变量 , 用 $ 定义  

	$color:red;
	div{
		color:$color
	}  
    　　}

如果变量需要镶嵌在字符串之中，就必须需要写在#{}之中。
	
	$direct:left;
	.pig{
		margin-#{&direct}:5px;
	}  
###2.计算功能
	$color:red;
	body{
		margin:(5px+10px)*2;
		color:$color-#fe67ee;
	}
###3.嵌套
	
	#content{
		#header{
			h1{
				width:200px;
				}
			h2{
				width:150px;
				}	
				}
		#footer{
			margin:10px;
				}
#####可以用 $ 代替父器
  
	article a {
 	 	color: blue;
  		&:hover { color: red }
	}  
#####群组选择器

	.container {
  		h1, h2, h3 {margin-bottom: .8em}
		}
#####其它选择器
	article {
  		~ article { border-top: 1px dashed #ccc }//同层选择器
  		> section { background: #eee }//子选择器
  		dl > {
    		dt { color: #333 }
    		dd { color: #555 }
  		}
  		nav + & { margin-top: 0 }//相邻选择器
		}
##### ! default（相当于css的! important ）
如果这个变量被声明赋值了，那就用它声明的值，否则就用这个默认值。  
###4.注释
1 . /* */  
2 . //
###5.代码的重用
####1.继承
可以一个选择器继承另一个选择器@extend
	    
		.class1 {
    　　　　border: 1px solid #ddd;
    　　}
    　　.class2 {
    　　　　@extend .class1;
    　　　　font-size:120%;
    　　}
####2.Minxin
用 @mixin 命令定义代码块  
用 @include 命令调用这个 @mixin  
mixin的强大之处，在于可以指定参数和缺省值。

	    @mixin rounded($vert, $horz, $radius: 10px) {
    　　　　border-#{$vert}-#{$horz}-radius: $radius;
    　　　　-moz-border-#{$vert}#{$horz}-radius: $radius;
    　　　　-webkit-border-#{$vert}-#{$horz}-radius: $radius;
    　　}


    　　#navbar li { @include rounded(top, left); }
		#footer { @include rounded(top, left, 5px); }  
####3.颜色函数
SASS提供了一些内置的颜色函数，以便生成系列颜色。

    　　lighten(#cc3, 10%) // #d6d65c（加亮）
    　　darken(#cc3, 10%) // #a3a329（变暗）
    　　grayscale(#cc3) // #808080(灰阶)
    　　complement(#cc3) // #33c(补充)  
####4 插入文件

@import命令，用来插入外部文件。

    　　@import "path/filename.scss";
##4.高级用法
####1.条件语句

	@if lightness($color) > 30% {
		background-color: #000;
	} @else {
		background-color: #fff;
	}
####2 循环语句

SASS支持for循环：

    　　@for $i from 1 to 10 {
    　　　　.border-#{$i} {
    　　　　　　border: #{$i}px solid blue;
    　　　　}
    　　}

也支持while循环：

    　　$i: 6;
		@while $i > 0 {
    　　　　.item-#{$i} { width: 2em * $i; }
    　　　　$i: $i - 2;
    　　}

each命令，作用与for类似：

    　　@each $member in a, b, c, d {
    　　　　.#{$member} {
    　　　　　　background-image: url("/image/#{$member}.jpg");
    　　　　}
    　　}
####3. 自定义函数

SASS允许用户编写自己的函数。

    　　@function double($n) {
    　　　　@return $n * 2;
    　　}

    　　#sidebar {
    　　　　width: double(5px);
    　　}






	
	

