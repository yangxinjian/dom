#Vue
##安装
1.检查是否有node

	node -v
2.安装vue-cli

	sudo npm install -g vue-cli
3.创建vue项目

	vue init webpack sell(文件名称)
4.以此步骤：进入项目，安装依赖，运行项目

	cd sell
	sudo npm install
	npm run dev
##基本知识点
1.从一个主vue中获取其他vue的模版

	<script>
		//第一步：获取其他vue模版的路径
		import "其他组件名" from "路径"
		//第二步：导出其他vue模版
		export default: {
			components: {
				"其他vue名"
			}
		}
	</script>
2.在创建项目时，把公用的文件新建一个common文件夹包含，一般为js文件夹，fonts文件夹，stylus文件夹（也可以选择sass or less）。
3.当我们在全局建立data.json文件时，我们需要在build文件夹下的dev-server中绑定数据

	var appData = require('../data.json');//获取json数据
	var seller = appData.seller;//seller为json数据中的一个
	var goods = appData.goods;
	var ratings = appData.ratings;
	
	var apiRoutes = express.Router();//获取路由
	
	apiRoutes.get('/seller', function (req, res) {//返回数据
	  res.json({
	    errno: 0,
	    data: seller
	  });
	});
	
	apiRoutes.get('/goods', function (req, res) {
	  res.json({
	    errno: 0,
	    data: goods
	  });
	});
	
	apiRoutes.get('/ratings', function (req, res) {
	  res.json({
	    errno: 0,
	    data: ratings
	  });
	});
	
	app.use('/api', apiRoutes);//应用数据
4.new对象实例在js中需要赋值给一个变量，但是在vue下的es6是不需要的，但是一定要在new之前加上注释
	
	／* eslint-disable no-new*／
5.当我们使用部分组件vue之后，我们可以直接在app.vue下引用组件标签
	
	//script
	import header from './components/header/header.vue'
	  export default {
	    components: {
	      'v-header': header
	    }
	  }
	//template
	<v-header></v-header>
6.一般在我们安装vue-cli之后，就自动配置了vue-route，可以在package.json中查看，没有的自行安装

	在package.json中的dependences下，"vue-route":"官网自行查询版本信息"
	mac下： sudo npm install
7.路由实现点击不同板块实现不同内容的变化
	
	1.需要在app.vue中设置点击点
		<route-link to="/组件板块名称">a</route-link>
	2.创建组件板块
	3.在主main中引用组件模版路径
	4.需要在main.js中配置路由
		Vue.config.productionTip = false
		Vue.use(Router)
		Vue.extend(App)
		const routes = [
		  {path: '/goods', component: goods},组件引用
		  {path: '/ratings', component: ratings},
		  {path: '/seller', component: seller}
		]
		const router = new Router({
		  routes
		})
		new Vue({
		  el: '#app',
		  router,
		  template: '<App/>',
		  components: { App }
		})
8.router.push('./goods') 将一个组件模版放到加载展示首页（默认值）  
9.点击切换的时候，为了告诉使用者，哪一个模块正在被使用，要对router-link标签设置active样式，虽然我们写的是router-link标签，但是实际应用的是a标签，所以我们设置样式的时候设置a标签的样式即可，点击样式可以通过main.js配置
	
	app.vue文件下
	&代表一个子元素的父级元素
		& > a
          display: block
          width: 100%
          font-size: 14px
          color: rgb(77, 85, 93)
          &.active//设置点击样式
            color: rgb(240, 20, 20)
    main.js文件下
    const router = new Router({
		  linkActiveClass: 'active',//配置点击样式
		  routes
		})
10.ajax绑定内部的json文件 ------ vue-resource

	1.安装vue-resource依赖
	  在官网查找版本后，在package.json下配置（dependences），之后sudo npm install  
	2.在main.js中配置vue-resource
	  import VueResource from 'vue-resource'
	  Vue.use(VueResource)
	3.在app.vue下获取数据（export default下）
	  data () {
	    return {
	    	seller: {}
	    }
	  },
	  created () {
	  	this.$http.get('/api/seller').then(response => {
	  	  response = response.body//获取数据的json格式
	  	  if (response.errno === 0) {//本地json数据需要在web-server。js中配置
	  	  	this.seller = response.data
	  	  }
	  	})
	  }
	  
##经典错误
1. Starting dev server...events.js:182 throw er; // Unhandled 'error' event  
  这个错误说明，你已经开启了一个dev的服务，你无法再次运行。  
  解决的办法就是：关闭，重新打开运行。  
  
2. ✘  http://eslint.org/docs/rules/no-multiple-empty-lines  More than 1 blank line not allowed  src/router/index.js:3:1  
	这个错误代表，在代码中两个标签内有空行