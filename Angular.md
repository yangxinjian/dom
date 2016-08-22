#Angular.js
AngularJS 把应用程序数据绑定到 HTML 元素。  
AngularJS 可以克隆和重复 HTML 元素。  
AngularJS 可以隐藏和显示 HTML 元素。  
AngularJS 可以在 HTML 元素"背后"添加代码。
AngularJS 支持输入验证  


##1.Angular表达式
AngularJS 表达式写在双大括号内：{{ expression }}。  
AngularJS 表达式把数据绑定到 HTML，这与 ng-bind 指令有异曲同工之妙。  
AngularJS 将在表达式书写的位置"输出"数据。  
AngularJS 表达式 很像 JavaScript 表达式：它们可以包含文字、运算符和变量。  
	
	<div ng-app="">
 		<p>我的第一个表达式: {{ 5 + 5 }}</p>
	</div>
#####AngularJS 数字
	<div ng-app="" ng-init="quantity=1;cost=5">
		<p>总价： {{ quantity * cost }}</p>
	</div>
#####AngularJS 字符串  
	<div ng-app="" ng-init="firstName='John';lastName='Doe'">
		<p>姓名： {{ firstName + " " + lastName }}</p>
	</div>
#####AngularJS 对象  
	<div ng-app="" ng-init="person={firstName:'John',lastName:'Doe'}">
		<p>姓为 {{ person.lastName }}</p>
	</div>
#####AngularJS 数组  
	<div ng-app="" ng-init="points=[1,15,19,2,40]">
		<p>第三个值为 {{ points[2] }}</p>
	</div>
类似于 JavaScript 表达式，AngularJS 表达式可以包含字母，操作符，变量。  
与 JavaScript 表达式不同，AngularJS 表达式可以写在 HTML 中。  
与 JavaScript 表达式不同，AngularJS 表达式不支持条件判断，循环及异常。  
与 JavaScript 表达式不同，AngularJS 表达式支持过滤器
##Angular指令
#####ng-app 指令告诉 AngularJS，div元素是 AngularJS 应用程序的"所有者"。  
#####ng-model 指令把输入域的值绑定到应用程序变量 name。  


	<div ng-app="">
        <p>名字:<input type="text" ng-model="name">
        <h1>您的名字是{{name}}</h1>
    </div>  
#####ng-init 指令初始化 AngularJS 应用程序变量。  
#####ng-bind 指令把应用程序数据绑定到 HTML 视图。
  
	<div ng-app="" ng-init="firstname='pig'">
        <p>姓名是:<span ng-bind="firstname"></span></p>
    </div>
#####ng-repeat 指令会重复一个 HTML 元素：
	<div ng-app="" ng-init="names=['Jani','Hege','Kai']">
  		<p>使用 ng-repeat 来循环数组</p>
  		<ul>
    		<li ng-repeat="x in names">
      		{{ x }}
    		</li>
  		</ul>
	</div>
#####ng-repeat 指令用在一个对象数组上：
	<div ng-app="" ng-init="names=[
						{name:'Jani',country:'Norway'},
						{name:'Hege',country:'Sweden'},
						{name:'Kai',country:'Denmark'}]">

	<p>循环对象：</p>
	<ul>
  		<li ng-repeat="x	in names">
    	{{ x.name + ', ' + x.country }}
  		</li>
	</ul>

	</div>
#####创建自定义的指令
	<body ng-app="myApp">
	<runoob-directive></runoob-directive> //第一种方法
	<script>
		var app = angular.module("myApp", []);
		app.directive("runoobDirective", function() {
    		return {
        		template : "<h1>自定义指令!</h1>"
    		};
		});
	</script>
	</body>
调用指令的四种方法： 
 
(1)元素名
	
	<runoob-directive></runoob-directive>
(2)属性
	
	<div runoob-directive></div>
(3)类名 ---- 前提是在return里面添加 restrict : "C"

	<div class="runoob-directive"></div>
(4)注释 ---- 前提是在return里添加restrict : "M",
        replace : true,

	<!-- directive: runoob-directive -->  
restrict 值可以是以下几种:  
E 作为元素名使用  
A 作为属性使用  
C 作为类名使用  
M 作为注释使用  
restrict 默认值为 EA, 即可以通过元素名和属性名来调用指令。  
##2.Angular模型
	
#####ng-model指令 
ng-empty  
ng-not-empty  
ng-touched  
ng-untouched  
ng-valid  
ng-invalid  
ng-dirty  
ng-pending  
ng-pristine  

	<div ng-app="myApp" ng-controller="myCtrl">
        名字：<input type="text" ng-model="name">
    </div>
    <script type="text/javascript">
        var app=angular.module("myApp",[]);
        app.controller('myCtrl',function($scope){
            $scope.name="小猪";
        });
    </script>
###双向绑定模板

	<div ng-app="myApp" ng-controller="myCtrl">
        <p>
            请您输入<input type="text" ng-model="name">
        </p>
        <h1>您输入了：{{name}}</h1>
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.controller("myCtrl",function($scope){
            $scope.name="pig";
        });
    </script>  
###验证信息
	<form ng-app="" name="Form">
        邮箱:
        <input type="email" name="Email" ng-model="text">
        <span ng-show="Form.Email.$error.email">请输入正确的邮箱哦</span>
    </form>
###应用状态
ng-model 指令可以为应用数据提供状态值(invalid, dirty, touched, error):

	<form ng-app="" ng-init="pig='835361977@qq.com'" name="Form">
        Email:
        <input type="email" name="pigAddress" ng-model="pig" required>
        <h1>状态分配</h1>
        <p>
            <h2>Valid:{{Form.pigAddress.$valid}}---如果输入的信息合法则为true</h2>
            <h2>Dirty:{{Form.pigAddress.$dirty}}---如果信息的值发生了改变则为true</h2>
            <h2>Touched:{{Form.pigAddress.$touched}}---如果发生了触屏点击则为true（text文本框之外）</h2>
        </p>
    </form>  
###css类
	<style type="text/css">
    	input.ng-invalid{
        	background:red;
    	}
	</style>
	<body>
    	<form ng-app="" name="Form">
        	输入您的名字：<input ng-model="text" required>
    	</form>
	</body>
##3.Angular作用域（scope）
AngularJS 应用组成如下：  
View(视图), 即 HTML。  
Model(模型), 当前视图中可用的数据。  
Controller(控制器), 即 JavaScript 函数，可以添加或修改属性。  
scope 是模型。  
scope 是一个 JavaScript 对象，带有属性和方法，这些属性和方法可以在视图和控制器中使用。  

	<div ng-app="myApp" ng-controller="myCtrl">
        <h1>{{pigname}}</h1>
    </div>
    <script>
        var app=angular.module("myApp",[]);
        app.controller("myCtrl",function($scope){
            $scope.pigname="小猪";
        });
    </script>
###作用域范围

	<div ng-app="myApp" ng-controller="myCtrl">
    	<ul>
        	<li ng-repeat="x in names">{{x}}</li>
    	</ul>
    </div>
    <script>
        var app=angular.module("myApp",[]);
        app.controller("myCtrl",function($scope){
            $scope.names=["猪头","猪脑","猪尾巴"];
        });
    </script>
###根作用域
所有的应用都有一个 $rootScope，它可以作用在 ng-app 指令包含的所有 HTML 元素中。  
$rootScope 可作用于整个应用中，是各个 controller 中 scope 的桥梁。  
用 rootscope 定义的值，可以在各个 controller 中使用。

	<div ng-app="myApp" ng-controller="myCtrl">
        <h1>姓{{lastname}}的成员有：</h1>
        <ul>
            <li ng-repeat="x in names">{{lastname}}{{x}}</li>
        </ul>
    </div>
    <script>
        var app=angular.module("myApp",[]);
        app.controller("myCtrl",function($scope,$rootScope){
            $scope.names=["小妹","小弟","小丫"];
            $rootScope.lastname="猪";
        });
    </script>  
##4.Angular控制器
AngularJS 应用程序由 ng-app 定义。应用程序在div内运行。  
ng-controller="myCtrl" 属性是一个 AngularJS 指令。用于定义一个控制器。  
myCtrl 函数是一个 JavaScript 函数。  
AngularJS 使用$scope 对象来调用控制器。    
在 AngularJS 中， $scope 是一个应用象(属于应用变量和函数)。
控制器的 $scope （相当于作用域、控制范围）用来保存AngularJS Model(模型)的对象。

	<div ng-app="myApp" ng-controller="myCtrl">
        <input type="text" ng-model="firstName"><br>
        <input type="text" ng-model="lastName"><br>
        您的姓名为:{{fullName()}}
    </div>
    <script>
        var app=angular.module("myApp",[]);
        app.controller("myCtrl",function($scope){
            $scope.firstName="小";
            $scope.lastName="猪";
            $scope.fullName=function(){
                return $scope.firstName+" "+$scope.lastName;
            }
        });
    </script>  
##5.Angular过滤器
####AngularJS 过滤器可用于转换数据：  用管道字符（|）
 
1 . currency	格式化数字为货币格式。  
2 . filter	从数组项中选择一个子集。  
3 . lowercase	格式化字符串为小写。  
4 . orderBy	根据某个表达式排列数组。  
5 . uppercase	格式化字符串为大写。

#####uppercase实例 / / 输出的是PIG
#####lowercase实例 / / 输出的是pig

	<div ng-app="myApp" ng-controller="myCtrl">
        <h1>姓名是:{{lastName | uppercase}}</h1> 
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.controller("myCtrl",function($scope){
            $scope.lastName = "piG";
            $scope.firstName = "小妹";
            $scope.fullName = function(){
                return $scope.lastName + "" + $scope.firstName;
            }
        });
    </script>    
####currency实例
	
	<div ng-app="myApp" ng-controller="myCtrl">
        数量：<input type="number" ng-model="quantity">
        单价：<input type="number" ng-model="price">
        总价是:{{quantity * price | currency}}
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.controller("myCtrl",function($scope){
            $scope.quantity = 12;
            $scope.price = 3.5;
        });
    </script>
输出的值是

	数量：12  单价：3.5  总价是:$42.00  
####orderBy实例（向指令添加过滤器）
	<div ng-app="myApp" ng-controller="myCtrl">
        <ul>
            <li ng-repeat="x in names | orderBy:'name'">{{x.name+","+x.food}}</li>
        </ul>
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.controller("myCtrl",function($scope){
            $scope.names=[
                {name:"pig",food:"肉"},
                {name:"cow",food:"草"},
                {name:"chicken",food:"米"}
            ];
        });
    </script>
输出的是
	
	chicken,米
	cow,草
	pig,肉
####filter 输入过滤（通过test输入值筛选）

	<div ng-app="myApp" ng-controller="myCtrl">
        <p>输入通过什么过滤</p>
        <p><input type="text" ng-model="test"></p>
        <ul>
            <li ng-repeat="x in names | filter:test | orderBy:'name'">
                {{(x.name | uppercase)+","+x.food}}
            </li>
        </ul>
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.controller("myCtrl",function($scope){
            $scope.names=[
                {name:"pig",food:"meet"},
                {name:"cow",food:"grass"},
                {name:"fish",food:"shrimp"}
            ];
        });
    </script>
##6.Angular服务
在 AngularJS 中，服务是一个函数或对象，可在你的 AngularJS 应用中使用。  
AngularJS 内建了30 多个服务。
####1.location服务：（获取当前地址）
	<div ng-app="myApp" ng-controller="myCtrl">
        <p>当前的URl</p>
        <h1>{{myUrl}}</h1>
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.controller("myCtrl",function($scope,$location){
            $scope.myUrl = $location.absUrl();
        });
    </script>
####2.timeout 相当于setTimeOut
	<div ng-app="myApp" ng-controller="myCtrl">
        <p>{{review}}</p>
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.controller("myCtrl",function($scope,$timeout){
            $scope.review = "good good study";
            $timeout(function(){
                $scope.review = "day day up";
            },2000);
        });
    </script>
####3.interval 相当于setInterval
显示当前的时间

	<div ng-app="myApp" ng-controller="myCtrl">
        <p>现在的时间是：</p>
        <p>{{nowTime}}</p>
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.controller("myCtrl",function($scope,$interval){
            $scope.nowTime = new Date().toLocaleTimeString();
            $interval(function(){
               $scope.nowTime = new Date().toLocaleTimeString();
            },1000);
        });

    </script>
####4.自定义服务（service）
	<div ng-app="myApp" ng-controller="myCtrl">
        <p>255的16进制是：</p>
        <p>{{hex}}</p>
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.service('hexafy',function(){
            this.Fanc = function(x){
                return x.toString(16);
            }
        })
        app.controller("myCtrl",function($scope,hexafy){
            $scope.hex = hexafy.Fanc(255);

        });
    </script>
####5.在过滤器中使用服务

	<div ng-app="myApp">
    	在过滤器中使用服务:
		<h1>{{255 | myFormat}}</h1>
	</div>

	<script>
    	var app = angular.module('myApp', []);
    	app.service('hexafy', function() {
        	this.myFunc = function (x) {
           	 return x.toString(16);
        	}
    	});
    	app.filter('myFormat',['hexafy', function(hexafy) {
       	 	return function(x) {
            	return hexafy.myFunc(x);
        	};
    	}]);

	</script>
##7.select
方法一：使用ng-option

	<div ng-app="myApp" ng-controller="myCtrl">
        <select ng-model="selectedName" ng-options="x for x in names"></select>
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.controller("myCtrl",function($scope){
            $scope.names=["zhu","gou","yang"];
        })
    </script>
方法二：使用ng-repeat
	
	<div ng-app="myApp" ng-controller="myCtrl">
        <select>
            <option ng-repeat="x in names">{{x}}</option>
        </select>
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.controller("myCtrl",function($scope){
            $scope.names = ["zhu","xiao","mei"];
        });
    </script>
ng-options 使用对象作为数据源, x 为键(key), y 为值(value):

	<div ng-app="myApp" ng-controller="myCtrl">
        <select ng-model="selectedCar" ng-options="x for (x,y) in names">
        </select>
        <div>
            <h1>你选择的是: {{selectedCar.brand}}</h1>
            <h2>模型: {{selectedCar.model}}</h2>
            <h3>颜色: {{selectedCar.color}}</h3>
        </div>
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.controller("myCtrl",function($scope){
            $scope.names ={
                car01 : {brand : "Ford", model : "Mustang", color : "red"},
                car02 : {brand : "Fiat", model : "500", color : "white"},
                car03 : {brand : "Volvo", model : "XC90", color : "black"}
            };
        });
    </script>
##8. 表格
$index+1显示序列号

	<div ng-app="myApp" ng-controller="myCtrl">
        <table>
            <tr ng-repeat="x in names | orderBy : 'country'">
                <td>{{ $index + 1 }}</td>
                <td>{{x.name}}</td>
                <td>{{x.country}}</td>
            </tr>
        </table>
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.controller("myCtrl",function($scope){
            $scope.names=[
                {name:"pig",country:"China"},
                {name:"dog",country:"us"},
                {name:"cow",country:"usa"},
                {name:"sheep",country:"koren"}
            ];
        })
    </script>
##9. Angular Html Dom
###1.ng-disabled 
ng-disabled 指令直接绑定应用程序数据到 HTML 的 disabled 属性。

	<div ng-app="" ng-init="mySwitch=true">
        <p>
            <button ng-disabled="mySwitch">aa</button>
        </p>
        <p>
            <input type="checkbox" ng-model="mySwitch">选我
        </p>
        <p>{{mySwitch}}</p>
    </div>
###2.ng-show 指令
ng-show 指令隐藏或显示一个 HTML 元素。

	<p ng-show="true">sssss</p> //这个是显示的
    <p ng-show="false">aaaa</p> //这个是不显示的
###3.ng-hide 指令
ng-show 指令隐藏或显示一个 HTML 元素。

	<p ng-hide="true">sssss</p> //这个是不显示的
    <p ng-hide="false">aaaa</p> //这个是显示的
##10. Angular事件
ng-click 指令定义了 AngularJS 点击事件。

	<div ng-app="myApp" ng-controller="myCtrl">
        <button ng-click="touch()">点我消失噢</button>
        <p ng-hide="myView">
            <input type="text" ng-model="firstname">
            <input type="text" ng-model="lastname">
            姓名:{{firstname+" "+lastname}}
        </p>
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.controller("myCtrl",function($scope){
            $scope.firstname="杨";
            $scope.lastname = "pig";
            $scope.myView = false;
            $scope.touch=function(){
                $scope.myView = !$scope.myView;
            }
        });
    </script>
##11. Angular 表单
angular.copy()可以复制属性对象...

	<div ng-app="myApp" ng-controller="myCtrl">
        <form>
            firstname:<br>
            <input type="text" ng-model="user.firstname"><br>
            lastname:<br>
            <input type="text" ng-model="user.lastname"><br>
            <button ng-click="reset()">RESET</button>
        </form>
        <p>USER:{{user}}</p>
        <p>MASTER{{master}}</p>
    </div>
    <script>
        var app = angular.module("myApp",[]);
        app.controller("myCtrl",function($scope){
            $scope.master={firstname:'zhu',lastname:'pig'};
            $scope.reset=function(){
                $scope.user=angular.copy($scope.master);
            };
            $scope.reset();
        })
    </script>

##12. Angular 路由

	
	<head>
    <meta charset="utf-8">
    <title>AngularJS 路由实例 - 菜鸟教程</title>
	</head>
	<body ng-app='routingDemoApp'>
		<h2>AngularJS 路由应用</h2>
    	<ul>
        	<li><a href="#/">首页</a></li>
        	<li><a href="#/computers">电脑</a></li>
        	<li><a href="#/printers">打印机</a></li>
        	<li><a href="#/blabla">其他</a></li>
    	</ul>

    	<div ng-view></div>
    	<script src="http://apps.bdimg.com/libs/angular.js/1.4.6/angular.min.js"></script>
    	<script src="http://apps.bdimg.com/libs/angular-route/1.3.13/angular-route.js"></script>
    	<script>
        angular.module('routingDemoApp',['ngRoute'])
                .config(['$routeProvider', function($routeProvider){
                    $routeProvider
                            .when('/',{template:'这是首页页面'})
                            .when('/computers',{template:'这是电脑分类页面'})
                            .when('/printers',{template:'这是打印机页面'})
                            .otherwise({redirectTo:'/'});
                }]);
    	</script>
		</body>




