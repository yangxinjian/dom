#React.js
####用于构建用户界面的Javascript库
首先引用  
  

    react.min.js - React 的核心库
    react-dom.min.js - 提供与 DOM 相关的功能
    browser.min.js - 用于将 JSX 语法转为 JavaScript 语法
	<script src="http://static.runoob.com/assets/react/react-0.14.7/build/react.min.js"></script>
    <script src="http://static.runoob.com/assets/react/react-0.14.7/build/react-dom.min.js"></script>
    <script src="http://static.runoob.com/assets/react/browser.min.js"></script>  
如果我们需要使用 JSX，则  
    
    <script> 标签的 type 属性需要设置为 text/babel。  
####JSX存在的意义？
每一个XML标签都会被JSX转换工具转换成纯Javascript代码，利用JSX，组件的结构和组件之间的关系看上去更加清晰。 
##1.ReactDOM.render  
<b>·</b>将render中写的div的内容放在id为example的div下，注意！render中的书写的内容与获取id之间用<b style="color:red;">“，”</b>隔开  
<b>·</b>同时ReactDOM.render的内容（*...*）可以写在额外的js下，只需要引入src即可
  
	<div id='example'></div>
	<script type="text/babel">
        ReactDOM.render(
            *<div>
                <h1>Hello, world!</h1>
                <h2>啦啦啦啦阿里</h2>
                <p data-myattribute="somevalue">aaa</p>
            </div>,*

                document.getElementById('example')
        );
    </script>  
####Javascript表达式
JSX中可以使用js，但是必须把js放在{}中

	<div id='example'></div>
	<script type="text/babel">
        ReactDOM.render(
            *<div>
                {1+1}
            </div>,*

                document.getElementById('example')
        );
    </script>  
JSX中不可以使用if...else ，但是可以使用conditional(三元运算)来进行表达  

	<div id='example'></div>
	<script type="text/babel">
    	var i=1;
    	ReactDOM.render(
    		<div>
        		<h1>{i=1?'true':'false'}</h1>
    		</div>,
			document.getElementById('example')
   		);
	</script>  
####样式
React中推荐使用内联样式，并且会在指定的数字后面添加 px <span style='color:red'>切记!</span>属性值再加上' ',每个属性要用 ， 隔开   

	<div id='example'></div>
	<script type="text/babel">
   		var styleexp={
        	background:'red',
        	color:'green',
        	fontSize:60
    	}
    	ReactDOM.render(
        	<h1 style={styleexp}>aaaaa</h1>
            ,
        	document.getElementById('example')
   		);
	</script>  
####注释
要卸载花括号里面

	{/*注释...*/}  
####数组
数组会展开所有内容  
 
	<div id='example'></div>
	<script type="text/babel">
    	var arr=[
            <h2>我第二</h2>,
            <h1>我第一</h1>,
            <h3>我第三</h3>,
    	]
		ReactDOM.render(
        	<div>{arr}</div>
            ,
        	document.getElementById('example')
    	);
	</script>  
##2.React 组件  
React.createClass 方法用于生成一个组件类 HelloMessage。

	<HelloMessage /> 实例组件类并输出信息。

<b style='color:red'>注意</b> 原生HTML元素名以小写字母开头，而自定义的 React 类名以大写字母开头，比如 HelloMessage 不能写成 helloMessage。除此之外还需要注意组件类只能包含一个顶层标签，否则也会报错。  

	<div id='example'></div>
	<script type="text/babel">
    	var HelloMessage = React.createClass({
        	render:function(){
            	return <h1>HelloPig</h1>;
        	}
    	});
    	ReactDOM.render(
        	<HelloMessage />
            ,
        	document.getElementById('example')
    	);
	</script>  
####如果想进行传参，使用this.props.参数属性  

	<div id='example'></div>
	<script type="text/babel">
    	var HelloMessage = React.createClass({
        	render:function(){
            	return <h1>Hello~~~{this.props.name}</h1>;
        	}
    	});
    	ReactDOM.render(
        	<HelloMessage name='pig' />{/*参数放在这里*/}
            ,
        	document.getElementById('example')
    	);
	</script>    
#####this.props可以设置为默认值，方法是getDefaultProps  

	var HelloMessage = React.createClass({
  		getDefaultProps: function() {
    		return {
      			name: 'Runoob'
    		};
  		},
  		render: function() {
    		return <h1>Hello {this.props.name}</h1>;
  			}
	});

	ReactDOM.render(
  		<HelloMessage />,
  		document.getElementById('example')
	);
####复合组件  
谨记 return 后面加上（），这个例子中WebSite拥有Link,Name的实例

	var WebSite = React.createClass({
        render:function(){
            return (
                    <div>
                            <Name name={this.props.name} />
                            <Link site={this.props.site} />
                    </div>
            );
        }
    });

    var Name = React.createClass({
        render:function(){
            return (<h1>{this.props.name}</h1>);
        }
    });

    var Link = React.createClass({
        render:function(){
            return(
                    <a href={this.props.site}>{this.props.site} </a>
            );

            ;

        }
    })
    ReactDOM.render(
        <WebSite name='pig' site='http://baidu.com' />
            ,
        document.getElementById('example')
    );  
##3.React State  
React 把组件看成是一个状态机（State Machines）。通过与用户的交互，实现不同状态，然后渲染 UI，让用户界面和数据保持一致。

React 里，只需更新组件的 state，然后根据新的 state 重新渲染用户界面（不要操作 DOM）。

以下实例中创建了 LikeButton 组件，<b style='color:green'>getInitialState</b> 方法用于定义初始状态，也就是一个对象，这个对象可以通过 this.state 属性读取。当用户点击组件，导致状态变化，<b style='color:green'>this.setState </b>方法就修改状态值，每次修改以后，自动调用 this.render 方法，再次渲染组件。  
  
<b style='color:red'>注意！onClick调用时用 ' = ' ！</b>

	<div id="example"></div>
    <script type="text/babel">
        var LikeButton=React.createClass({
            getInitialState:function(){
                return{liked:false};
            },
            handleClick:function(event){
                this.setState({liked: !this.state.liked});
            },
            render:function(){
                var text=this.state.liked?'喜欢':'不喜欢';
                return(
                        <p onClick={this.handleClick}>
                            你<b>{text}</b>我。点我切换状态。
                        </p>
                );
            }

        })
        React.render(
            <LikeButton />,
            document.getElementById('example')
        );
    </script>  
##4.React的组件API
####(1)setState  

	setState(object nextState[, function callback])
*nextState，将要设置的新状态，该状态会和当前的state合并  
*callback，可选参数，回调函数。该函数会在setState设置成功，且组件重新渲染后调用。  

	<script type="text/babel">
        var Counter=React.createClass({
           getInitialState:function(){
               return {clickCount:0};
           },
           handleClick:function(){
               this.setState(function(state){
                   return {clickCount:state.clickCount+1};
               });
           },
           render:function(){
               return (
                       <h2 onClick={this.handleClick}>点我~此时你已经点击的次数:{this.state.clickCount}</h2>
               )

           }
        });
        ReactDOM.render(
                <Counter />,
                document.getElementById('example')
        );
    </script>  
####(2)替换状态：replaceState

replaceState(object nextState[, function callback])

    nextState，将要设置的新状态，该状态会替换当前的state。
    callback，可选参数，回调函数。该函数会在replaceState设置成功，且组件重新渲染后调用。

replaceState()方法与setState()类似，但是方法只会保留nextState中状态，原state不在nextState中的状态都会被删除。  
####(3)设置属性：setProps

setProps(object nextProps[, function callback])

    nextProps，将要设置的新属性，该状态会和当前的props合并
    callback，可选参数，回调函数。该函数会在setProps设置成功，且组件重新渲染后调用。



props相当于组件的数据流，它总是会从父组件向下传递至所有的子组件中。当和一个外部的JavaScript应用集成时，我们可能会需要向组件传递数据或通知React.render()组件需要重新渲染，可以使用setProps()。更新组件，我可以在节点上再次调用React.render()，也可以通过setProps()方法改变组件属性，触发组件重新渲染。  
####(4)替换属性：replaceProps

replaceProps(object nextProps[, function callback])

    nextProps，将要设置的新属性，该属性会替换当前的props。
    callback，可选参数，回调函数。该函数会在replaceProps设置成功，且组件重新渲染后调用。

replaceProps()方法与setProps类似，但它会删除原有  
####(5)获取DOM节点：findDOMNode

DOMElement findDOMNode()

    返回值：DOM元素DOMElement

如果组件已经挂载到DOM中，该方法返回对应的本地浏览器 DOM 元素。当render返回null 或 false时，this.findDOMNode()也会返回null。从DOM 中读取值的时候，该方法很有用，如：获取表单字段的值和做一些 DOM 操作。  
##5.React 组件生命周期  
通过 componentDidMount 方法设置一个定时器，每隔100毫秒重新设置组件的透明度  

	<div id="example"></div>
    <script type="text/babel">
        var Hello=React.createClass({
           getInitialState:function(){
               return {opacity:1.0};
           },
           componentDidMount:function(){
               this.timer=setInterval(function(){
                   var opacity=this.state.opacity;
                   opacity-=.05;
                   if(opacity<0.1){
                        opacity=1.0;
                   }
                   this.setState(
                           {
                               opacity:opacity
                           }
                   );
           }.bind(this),100);
           },
           render:function(){
               return (
                       <div style={{opacity:this.state.opacity}}>
                               Hello{this.props.name}~~~
                       </div>
               );
           }
        });
        ReactDOM.render(
                <Hello name='pig' />,
                document.getElementById('example')
        )
##6.React Refs
点击获取焦点  
React 支持一种非常特殊的属性 Ref ，你可以用来绑定到 render() 输出的任何组件上。

这个特殊的属性允许你引用 render() 返回的相应的支撑实例（ backing instance ）。这样就可以确保在任何时间总是拿到正确的实例。 

	<script type="text/babel">
        var MyComponent=React.createClass({
           handleClick:function(){
               this.refs.myInput.focus();
           },
           render:function(){
               return(
                    <div>
                          <input ref="myInput" />
                          <input type='button' value='点我获取焦点' onClick={this.handleClick} />
                    </div>
               );
           }
        });
        ReactDOM.render(
                <MyComponent />,
                document.getElementById('example')
        )
    </script>