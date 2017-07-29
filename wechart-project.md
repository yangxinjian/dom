#小程序入门
###首先自行下载官方提供的小程序开发工具
##了解内部构造
###部分功能操作前期理解：
1.source中后缀名为[sm]的js就是代表我们源代码文件  ------ 用来调试断点  
2.source中后缀名仅为js代表编译后的代码文件  
3.f10单步断点  
4.f8跳到下一个断点  
5.Ctrl+s ------ 在页面中查找文件元素等    
6.NetWork中Name下是网络连接的页表  
7.小程序中支持本地存储Storage  
8.AppData里的内容与页面有关   
9.Wxml ------- UI元素查看代码的排布  
10.在左上角帮助--关于--可以查看小程序官方帮助文档  
11.在总页面的json配置下的“pages”中写入一个文件夹下的名字，会在pages文件夹下自动生成四种文件，wow.js;wow.wxss;wow.wxml;wow.json

	"pages":[
	    "pages/wow"
	 ],
###页面构成简述
1.page文件夹下每一个文件夹代表一个页面    
2.app.js app.json app.wxss 全局唯一，掌控整个应用程序  
3.就近原则 ------ 譬如（css、json）,自己页面内权重大于app全局权重  
4.每一级页面均有：wxml、wxss、json、js构成，理论上每一级页面的数量都是无限的   
5.小程序现在限定最多有五级界面  
6.json配置过程中，不可以使用注释  
7.wxml是编写小程序骨架的文件  
8.image组件默认图片（我们不给宽高的前提下）宽：300px,高225px  
9.文字可以不再text组件内部，但是，只有在text组件内部的文字才可以在手机端长摁选中  
10.px在小程序中仅仅代表手机端的逻辑分辨率像素，而rpx代表物理像素，px = rpx * 2 ，
但是在应用过程中，我们使用rpx，好处在于在不同屏幕分辨率下，rpx会等比例放大缩小，而不是固定值  
11.设计师设计图稿的时候以iphone6为佳  
12.一般静态样式写在class中，一般我们要动态获取样式的时候写在style行内样式中  
13.display:flex ------ 弹性盒子 flex-direction确定盒子内部内容的方向：row水平排布，column垂直排布  
14.align-items ------ 实现盒子内部内容居中  
15.如果一个样式我们使用的次数非常多，我们就把他放到全局的app.wxss中  
16.小程序为我们wxml界面添加一个最最最外层page标签，可设置整体背景颜色  
17.小程序在主界面中会默认给我们添加一个标题，清除标题在json中windows下配置navigationBarBackgroundColor，让他调节到和我们背景颜色一样就好  
18.pt是逻辑像素，与屏幕大小有关，可显示长度，px是物理像素，与屏幕大小无关，仅仅为点（10），1个pt可以有>=1个px构成  
19.使用rpx，小程序会在不同分辨率下自动调节  
20.数据缓存最大为10兆，需要手动清除  
21.navigationBarBackgroundColor设置必须是#颜色（真机显示）   
22.json配置文件中，pages数组下第一个值为启动显示的页面  
23.单独目录下配置的json文件只能配置window下的属性，并且不需要写window：{}，只需要设置旗下的属性值即可  
24.我们一般垂直方向设为px。水平设为rpx  
25.我们滚动的时候，vertical="true"代表数值滚动 ，vertical={{false}}为水平滚动     
26.alt+shift+f 整理对齐代码格式   
27.每一个新建的json文件都要填充{}     
28.每新建一个页面都要在app.json下配置一下  
29.AppData可以调试查看我们绑定的数据  
30.音乐是不可以存在本地的，线上音乐  
31.小程序的缓存是不可以清除的在真机运行时，如果我们想清楚缓存，需要在页面中添加一个摁钮，调用wx.clearStorage()  
32.template 模版中使用图片路径最好为绝对路径  
33.我们在使用豆瓣的api图片信息时，只能在“电影条目信息下的required scope为basic时”采用信息。  
34.在模版中设置样式的时候，应取名专属的class名称，否则引用之后，相同的class名会被覆盖。  
35.在使用弹性盒子的时候（flex），使用类似vertical-align:middle,就会失效。
弹性盒子下的justify-content包含：space-between内容左右陈列，space-center内容剧中陈列，space-around内容平均分布。  
36.公共部分的js文件封装完方法之后，我们需要输出，在引用。

	输出：module.exports = {
		  convertToStarArray: convertToStarArray
		}
	引用：（在需要的js文件下的头部）
	var util = require('../../utils/util.js');
	
37.在模版中无法运行我们书写的js代码，必须在调用模版的js文件下，才会执行。  
38.动态获取导航条的名称

	wx.setNavigationBarTitle({
      title: category,／／可以为“字符串”，也可以为变量
    })  
39.支持css3的模糊等样式

	webkit-filter: blur(20px);
	white-space: nowrap;／／不允许换行
##组件部分功能
###滑动轮播 ------ swiper
1.swiper-item 每一个swiper-item都代表一个要滚动的框，里面可以放置图片摁扭文字等信息  
2.swiper-item 默认的宽高都是100%，继承父类swiper的宽高  
3.组件轮播默认的是水平滚动，如果你想要垂直滚动，新增属性值vertical="true"即可（开发者文档并没有给出，其余属性均在开发者文档中）  
###js脚本 ------ page()生命周期
1.on开头代表监听函数（onload/onready/...）  
2.先加载onload，在加载onshow，在加载onready  
3.小程序没有dom节点，如果我们想要绑定数据，在page中的数据data部分添加属性以及内容，在wxml中{{引用这个属性}}

	//json中
	data:{
		date:"111"
		}
	//wxml
	{{date}}

4.数据绑定为单向绑定，js改变wxml，wxml改变js不变  
5.一个标签的内容可以嵌套多个{{}}  
6.wx:if="{{false}}"是指让标签不显示的一个属性，我们也可以通过在js动态控制数据  
7.{{}}里面可以进行字符串拼接，也可以变量数值的值计算相加减  
8.block标签包裹住要循环的标签内容，相当于一个括弧，for循环组件，整个一个文章内容框架，wx:for-item代表子元素的对象，默认值为item，
wx:for-index为子元素的序列值。默认值为index，post_key为我们在js中设置的数据数组，分别将我们所对应的数据值依次{{}}填入标签中
	
	<block wx:for="{{post_key}}" wx:for-item="item" wx:for-index="index"></block>
9.当我们json数据存放的是一个数组var data = []，但是我们export导出的是一个对象的时候 module.exports = {
        postList: local_database
    }，获取数组的内容时会是undifined，所以我们需要data.postList[0]


###事件
1.在所有的的事件名词前面都要加上bind绑定，或者catch，eg：bindtap  
2.wx.navigateTo（）跳转页面代表从父级页面跳转到子页面，并且可以从子页面返回到父级页面，wx.redirectTo()跳转页面代表平级页面的跳转，不具有返回功能  
3.wx.navigateTo（）跳转页面后，本身页面属于onhide部分，wx.redirectTo()跳转页面后，本身页面属于onUnload部分  
4.冒泡事件：点击子元素的事件也触发父元素的事件bind绑定，如果想让子元素单独自己执行事件，就使用catch绑定  
5.小程序总是会读取data对象来做数据绑定，这个动作我们称为A，而这个动作A的执行，是在onload事件执行之后发生的    
6. event.currentTarget.dataset.postid;event代表方法本身自带的参数，currentTarget代表当前我们点击的对象，dataset表示自定义的属性，postId使我们自定义属性的名字，可以为多个自定义属性  
7.如果想要发生跳转页面事件，并把一个参数传递进去，在父页面传递，在子页面接受。

	父级：onMoreTap: function(event){//"更多"跳转方法
		    var category = event.currentTarget.dataset.category;//获取点击的“更多”，代表哪儿一个分类
		    wx.navigateTo({//跳转子页面
		      url: 'more-movie/more-movie?category=' + category,
		    })
		  },
	子级： onLoad: function (options) {
		    var category = options.category;//接受从主js传过来的点击的类别信息
		  },
		  
8.预览图片事件
	
	wx.previewImage({
      current: src,//当前显示图片的http链接
      urls: [src]//需要预览的图片http链接
    })
###模板------template
1.可以把我们要用for循环写出的代码放到模板中，新建一个wxml文件，用template组件包裹住要存放的组件，name是给模板起一个名字，is 后面接着模板的name名字，data后面接的是循环遍历的子元素，需要{{}}包裹起来

	//新建的模板wxml
	<template name="postItem"> 
    	<view class="post-container">
    	</view>
	</template>

	//原本的需要引入模板的wxml文件
	第一步：
	<import src="模板的wxml文件路径" /> ------ 在头部
	第二部：
	<template is="postItem" data="{{item}}" /> ------ 引入模板

2.我们使用模板的目的：使多个页面共同使用模板内容（编程的复用思想）  
3.在我们用模板封装了wxml的时候，也要对这个部分的wxss样式进行封装  
4.在我们想要在引用的地方引用wxml模板用<imgport /> , （同时必须引用模版的样式）引用wxss的时候用@import "";  
5.正常的逻辑引用wxss，第二层模版引用第三层模版，第一层模版引用第二层模版，显示模板的主样式文件中引用第一层模版。  
6.在引用wxss之后需要在结尾加上；号，否则样式报错。 
7.

	<text class="post-date">{{item.date}}</text>
引入子对象元素的date属性的另一种写法：

	<text class="post-date">{{date}}</text>
注意：要把item前面加上...，目的是把子元素对象散开平铺

	<template is="postItem" data="{{...item}}" /> 
###自定义属性
1.以data-开头+自己起的字母名字="";  
2.我们可以用自定义属性来添加id，一般一个循环体下的模板分为1，2,3，...多个，判断点击事件，点击大模板判断具体点击了大模板下的哪儿个子元素  
3.在编译之后，小程序会把我们自定义的date-..-.解析为驼峰命名规则，eg：data-postId会解析为postid，所以在js获取的时候要注意
###storage缓存
1.除非用户主动清除缓存。否则一定存在  
2.设置缓存同步方式wx.setStorageSync('名字',"内容")，内容可以为一个string字符串，也可以为一个对象  ，获取缓存使用get  
3.如果你想更改缓存的内容,wx.setStorageSync('名字',"更换的内容")，名字必须一样的时候  
4.删除指定缓存：wx.removeStorageSync('名字') ， 删除所有缓存wx.clearStorageSync()  
5.缓存的上限最大不能超过10MB  
6.同步缓存方式与异步缓存的对比，一般情况我们多用同步缓存的方式，异步缓存会在加载整个方法很快速，同步在获取'posts_collected'，如果这个方法很大，那么获取的时间就会消耗很多

	//异步获取缓存的方式
    getPostsCollectedAsy: function () {
        var that = this;//因为我们success要调用的使我们page下的this，需要先转换
        wx.getStorage({
            key: "posts_collected",//我们获取的操作对象
            success: function (res) {//res自带的data属性
                var postsCollected = res.data;
                var postCollected = postsCollected[that.data.currentPostId];
                //收藏变成未收藏，未收藏变成收藏
                postCollected = !postCollected;
                postsCollected[that.data.currentPostId] = postCollected;
                that.showToast(postsCollected, postCollected);
            }
        })
    },
	//同步获取缓存的方式
	getPostsCollectedSyc: function () {
        var postsCollected = wx.getStorageSync('posts_collected');
        var postCollected = postsCollected[this.data.currentPostId];
        //收藏变成未收藏，未收藏变成收藏
        postCollected = !postCollected;
        postsCollected[this.data.currentPostId] = postCollected;
        this.showToast(postsCollected, postCollected);
    },
###切换图片
------else if判断，如果是真就加载collection图片，否则加载collection-anti图片

	<image wx:if="{{collected}}"src="../../../images/collection.png"></image>
     	<image wx:else src="../../../images/collection-anti.png"></image>
------直接在src中判断变量，根据变量切换图片

	src="{{isPlayingMusic?'../../../images/music-stop.png':'../../../images/music-start.png'}}

###校验用户提示信息
1.------wx.showToast({})  提示框  
判断是否成功或者取消，我们可以采用js的三元判断法

	title:postCollected?"收藏成功":"取消成功" ------ title:为提示的内容
	duration: 1000  ------ 设置提示消失的时间
	icon:success(默认)还有一个loading
可以自动消失

2.------wx.showModal({})  模型页面，不点击摁扭不关闭

	title:标题名称
	content：内容
	showCancle：设置取消摁扭 true or false
	cancel ：取消摁扭文本
	confirmText：确认摁扭文字
	confirmColor:确认文字颜色
当我们在wx.showModal({})里面中使用success function的时候，如果想调用上一个方法（出了showModal之外），this不在有效果（因为他指代上下文文本），所以我们要在showModal方法里重新定义一个变量保存下来this

	var that = this;
	that.setData({
        collected: postCollected
    })
3.------wx.showActionSheet({})  动作连接，在页面底部呈现，譬如分享给其他（朋友圈，微博等）

	itemList:[
                "分享给微信好友",
                "分享给朋友圈",
                "分享到QQ",
                "分享到微博"
            ],
    itemColor:"#405f80"
###音乐播放
1.wx.playBackgroundAudio({  
<span style="margin-left:60px">	url:"音乐的网络地址",  
<span style="margin-left:60px">	title:"音乐的名字"，  
<span style="margin-left:60px">	coverImgUrl:"音乐的背景图片"  
<span style="margin-left:60px">})  
2.wx.pauseBackgroundAudio() ------ 暂停播放音乐（模拟器下面是停止播放，再次播放会重头，但是真机中会是正常暂停音乐）  
3.主屏幕监听页面音乐播放同步效果 ------ 由框架调用代码

	wx.onBackgroundAudio(function(){
		可以把之前我们设置播放的变量值重新更改 -- 播放
	})
	wx.onBackgroundAudio(function(){
		可以把之前我们设置播放的变量值重新更改 -- 暂停 
	})
4.不同页面不同的音乐播放，我们需要在appjs中设置两个全局变量，一个存储当年播放的音乐的id，一个存储在主屏幕播放的是哪儿一个音乐，之后在我们js中获取app的对象，通过getApp()获取全局变量，在监听事件中判断该执行哪儿一种变换
###不同组件调用统一事件方法
####方法一：wxml文件，在最外层调用一个大方法，每一个img给一个id值，js文件使用event.target.dataset获取id，target指的是当前点击的组件（冒泡机制），currentTarget 指的是事件捕获的组件，target这里指的是image，而currenttarget指的是swipper
	
		<swiper catchtap="onSwiperTap" indicator-dots="true" autoplay="true" interval="2000">
        <swiper-item>
            <image  src="../../images/rain.png" data-postId="{{2}}"></image>
        </swiper-item>
        <swiper-item>
            <image src="../../images/tired.png" data-postId="{{3}}"></image>
        </swiper-item>
        <swiper-item>
            <image src="../../images/umbrella.png" data-postId="{{4}}"></image>
        </swiper-item>
    </swiper>
    
    	／／js文件
    	onSwiperTap: function(event){
	    //当前点击的图片
	    var postId = event.target.dataset.postid;
	
	    wx.navigateTo({
	      url: 'post-detail/post-detail?id=' + postId
	    })
	  },
####方法二：给每一个img组件都添加一个事件，在js调用事件的时候使用currentEvent.target.dataset获取id
	
		<swiper-item>
            <image catchtap="onSwiperItemTap" src="../../images/rain.png" data-postId="{{2}}"></image>
        </swiper-item>
        
        ／／js文件
    	onSwiperItemTap: function(event){
	    //当前点击的图片
	    var postId = event.currentTarget.dataset.postid;
	
	    wx.navigateTo({
	      url: 'post-detail/post-detail?id=' + postId
	    })
	  },
	
###选项卡 ------ tabBar
1.我们想从登陆界面点击进入带有选项卡的页面，跳转的方法必须改为wx.switchTab  
2.选项卡需要在app.json中配置  
3.选项卡最少为2个，最多为5个，我们要在登陆之后的界面看到选项卡，也必须把这个界面的路径填入到list中  

	"tabBar": {
    "list": [
      {
        "pagePath": "pages/posts/post",
        "text": "文章"
      },
      {
        "pagePath": "pages/movies/movies",
        "text": "电影"
      }
    ]
    }
    
4.tabbar边框颜色 -- borderStyle（默认：黑色）  
5.选项卡填入图片，在list中的iconPath中添加  
6.如果想在选项卡中呈现图片，需要设置两张，一张为点中的，一张为未点中的样式

	"iconPath": "images/dianying.png",
	"selectedIconPath": "images/dianying_hl.png"
	
###获取服务器端数据api
1.获取api写法，"Content-Type": "application/xml"application下绝对不可以写json,可能因为我们的data的内容为空，页面会尝试对象转换，所以报错了。

	Page({
		  onLoad: function(event){
		    wx.request({
		      url: 'https://api.douban.com/v2/movie/top250',／／路径
		      data: {},
		      method: 'GET',／／获取请求
		      header: {
		        "Content-Type": "application/xml"
		      },
		      success: function(res){
		        console.log(res)
		      },
		      fail: function(){
		        console.log('fail')
		      }
		    })
		  },
		
		})
2.当我们获取的数据超过我们要的数量的时候，我们可以通过在路径后面添加起始（start）限制（count限制数目）：

	var inTheatersUrl = app.globalData.doubanBase//全局的http:// 
	api.douban.com + "/v2/movie/in_theaters" + "?start=0&count=3";
3.当我们想初始值数据对象的时候，并要在onload方法中调用，我们要早data中定义变量，并且给予一个空对象。
	
		 data:{
		    inTheaters:{},
		    comingSoon:{},
		    top250:{}
		  },／／定义变量
		  
		  this.getMovieListData(inTheatersUrl , "inTheaters");／／调用方法
		  
###上滑实现加载数据
1.在加载数据的模板或者组件中，添加scroll-view组件

	 <scroll-view class="grid-container" 
	 scroll-y="true" ／／纵向滚动
	 scroll-x="false" 
	 bindscrolltolower="onScrollLower"／／为滚动刷新添加方法（在调用模版的js中）>
2.在实现这个功能时，需要注意你现在所展示的信息空间必须有高度，否则程序无法判断是否到底部，无法制定加载操作。  
3.当我们在某一个api下获取20时条数据的数据的时候，我们要在家20条数据，就需要在路径中设置count值。设置完成后，加载数据，发现当我们滚动后，后来的二十条数据替换了之前的数据，并没有实现一个叠加的效果。为了解决这个问题，在小程序没有dom的结构下，我们只能叠加数据。

	第一步：需要在整体data数据中，定一个变量
	isEmpty: true//指代当前数据是否为空
	
	第二步：判断是否是第一次加载数据，第一次加载数据执行20条数据，否则叠加数据
	 var totalMovies = {};//设置一个对象保存加载前后的总数据
	if(!this.data.isEmpty){//判断是否不是第一次加载数据
      totalMovies = this.data.movies.concat(movies);//将之前的数据与后加载的20条数据结合在一起
    }else{
      totalMovies = movies;
      this.data.isEmpty = false;
    }
    
    第三步：
    this.setData({
      movies: totalMovies//绑定所有数据
    });
4.书写良好校验信息，当我们进行加载数据的时候，需要让我们的用户知晓，所以我们在调用方法的时候，给出校验，在数据加载后，校验截止。

	wx.showNavigationBarLoading();／／出现
	wx.hideNavigationBarLoading();／／截止
	
###表单组件
1.input :输入组件
	
	<input type="text"//定义类型
	placeholder="我的前半生" //定义初始值
	placeholder-class="placeholeder" //定义初始值的样式
	bindfocus="onBindFocus" //定义焦点获取事件
	bindchange="onBindChange"/>//定义text改变触发事件
当我们用焦点事件切换不同的view的时候，我们可以在wxml的view中通过变量隐藏和显示

	<view class="search-panel" wx:if="{{searchPanelShow}}">
	
	／／在绑定事件的时候，更改初始值的boolean
	 onBindFocus: function(event){
	    this.setData({
	      containerShow: false,
	      searchPanelShow: true
	    })
	  },
	  
获取用户在input中输入的文字：
	
	 onBindChange: function(event){
	    var text = event.detail.value;//获取用户输入的text值
	  },
	
2.icon组件：小程序专门为开发者设计的使用图标  

	type:图标类型
	size:图标大小
	color:图标颜色
	
###图片的裁剪
在小程序中，image标签，不光有src属性，同时也具备裁剪的属性--mode（三种缩放模式，9种裁剪模式）具体可查看小程序文档。（一定要定义图片的长和宽，否则裁剪无意义）默认为scaleToFill。aspectFit的属性让长的一边完全显示。aspectFill保证图片比例，只让短边完全显示(将长边裁剪，取中间显示)。

	<image src="{{movie.movieImg}}" class="head-img" mode="aspectFill"/>
        
##问题汇总
###1pages/posts/post-detail/post-detail 出现脚本错误或者未正确调用 Page()
	在新建的文件夹下的js文件中添加page（{}）就好啦
###2.VM3774:2 pages/posts/post-detail/post-detail.json
Expecting 'STRING','NUMBER','NULL','TRUE','FALSE','{','[', got EOF
    | ^    

	在新建的文件夹下的json文件中添加{}就好啦
###3.VM3935:2 ./pages/posts/post.wxml
 end tag missing, near 'import'
	
	<import src="post-item/post-item-template.wxml" >
	<import>标签未闭合<import />
	
###4.如果写入的tempalte内容并没有出现时，应先检查头部引用import模版路径是否正确。
###5.通过js页面的page中的onload，wx.request获取服务器端的url中出现过一个问题，在路径写对的前提下，发现调试中一直有一个错误：说我们的api请求一直不在合法。这个原因是因为我们使用了appid，解决办法：在基础信息中将限制条件勾上，重新加载即可。
###6.WAService.js:3 thirdScriptError

	processDoubanData is not defined;at pages/movies/movies 
	getMovieListData function;at api request success callback 
	functionReferenceError: processDoubanData is not defined
	

这个错误使用的情况是：当我们想在一个发放中调用另一个方法的时候，直接写了a（）调用。原因是当我们在方法里面中使用success function的时候，如果想调用下一个方法，this不在有效果（因为他指代上下文文本），所以我们要在使用success的方法中里重新定义一个变量保存下来this.

	that.a();
###6.callBack is not defined;at "pages/movies/more-movie/more-movie" page lifeCycleMethod onLoad functionReferenceError: callBack is not defined
在我们使用回调函数时，书写callBack方法后，调用方法时，忘记加this.

	onLoad: function (options) {
    util.http(dataUrl , this.callBack);
    },
    callBack: function(data){
    }
 







 

