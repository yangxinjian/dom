#ES6&nbsp;&nbsp;features  
traceur可查看
###1.=>  
   用箭头代替function，箭头左边是参数，右边是return返回值  
 
    function(a){
       return a+1;
    }
     转换为
     a=>a+1;
###2.添加了对类的支持，引用了class关键字  
在原生的class支持后，对象的创建，继承更加直观了，并且父类方法的调用，实例化，静态方法和构造函数等概念都更加形象化。

    class Parent{//定义了一个父类
      //新型构造器
      constructor(name){
        this.name=name;
      }
      //实例方法
      sayName(){
        alert("This is a name id"+this.name);
      }
    }

    class Son extends Parent{
      //直接调用父类构造器进行初始化
      constructor(name){
        super(name);
      }
      //孩子自己的方法
      own(){
        alert("This is son's method");
      }
    
    }
   
    var parent=new Parent("吃霸");
    var son=new Son("小吃货");
    parent.sayName();//输出了“This is a name 吃霸 ”
    son.sayName();//输出了“This is a name 小吃货 ”
    son.own();//输出了“This is son's method”
###3.增强的对象字面量
可以在对象字面量里面定义原型  
定义方法可以不用function关键字  
直接调用父类方法

    var boss={
    	eat(){
			alert("I love eating");
		}
    };

	var employee={
		__proto__:boss;//相当于employee继承了boss
		company:"吃货公司";
		work(){
			alert("Eating is my dream");
		}
	}

	boss.eat();//输出了I love eating
	employee.eat();//输出了I love eating  
###4.字符串模板  
用反引号 ` 来创建字符串，可以包含由美元符号加花括号包裹的变量$()

    var a=Math.random()*10;
	alert('The number is $(a)');  
###5.解构  
利用解构这一特性，可以直接返回一个数组，然后数组中的值会自动被解析到对应接收该值的变量中

    var [x,y]=getResult();
	[name,,age]=['猪'，'美'，'21'];

	function getResult(){
		return [1,2];
	}
	
	alert('x:'+x+',y:'+y);//输出x，y值x:1,y:2
	alert('name:'+name+',age:'+age);//输出name，age值name:猪，age:21
###6.参数  
#####（1）默认参数值

	function(x,y=3,z=9){//y,z均位定义仍可计算
		return x+y+z;
	}
	f(1)===1+3+9=12
#####（2）不定参数

	function add(x,y,...a){
		return (x+y)*a.length;
	}
	add(1,3,"hello",true,a);===(1+3)*3=12
#####（3）扩展参数

	one：  
	var arr=["小猪","小马","小猴子"];
	function add(name1,name2,name3){
		alert("Hello"+${name1}+${name2}+${name3});
	}
	add(...arr);---输出了Hello小猪小马小猴子
	two：
	var shu="hello";
	var char=[...shu]---char=="h","e","l","l","o"相当于把字符串分割放入数组中
###7.Let、const(定义常量)
let和var一样，均可以定义变量，只不过let限定在了特定范围内才能使用，而离开这个范围则无效

	for(let i=0;i<3;i++){
		alert(i);//i:0,1,2
	}
	alert(i);//i为undefined
###8.for of 值遍历

	var arr=["a","b","c"];
	for(d of arr){
		alert(d);//a,b,c
	}
###9.Binary & Octal Literal二进制八进制字面

	0b111110111 === 503//将二进制的数表示为十进制
	0o767 === 503//将八进制的数表示为十进制
