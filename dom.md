##DOM:document object model(文本对象类型)
####定义了访问和管理xml文档的标准方法

节点（node）：     
    &nbsp;&nbsp;&nbsp;&nbsp;*xml文档中的每个成分都是一个节点  
    &nbsp;&nbsp;&nbsp;&nbsp;*整个文档是一个文档节点  
    &nbsp;&nbsp;&nbsp;&nbsp;*每个xml标签元素是一个元素节点  
    &nbsp;&nbsp;&nbsp;&nbsp;*包含在xml元素中的文本是文本节点  
    &nbsp;&nbsp;&nbsp;&nbsp;*每一个xml属性也是一个属性节点  
    &nbsp;&nbsp;&nbsp;&nbsp;*注释属于注释节点  

节点级别：  
    &nbsp;&nbsp;&nbsp;&nbsp;·在节点树种，顶端的节点成为根节点  
    &nbsp;&nbsp;&nbsp;&nbsp;·根节点之外的每个节点都有一个父节点  
    &nbsp;&nbsp;&nbsp;&nbsp;·节点可以有任何数量的子节点  
    &nbsp;&nbsp;&nbsp;&nbsp;·叶子是没有子节点的节点  
    &nbsp;&nbsp;&nbsp;&nbsp;·同级节点是拥有相同父节点的节点  

Node属性：  
    &nbsp;&nbsp;&nbsp;&nbsp;1.childNodes--返回节点的子节点的节点列表  
    &nbsp;&nbsp;&nbsp;&nbsp;2.firstChild--返回节点的首个子节点  
    &nbsp;&nbsp;&nbsp;&nbsp;3.lastChild--返回节点的最后一个子节点  
    &nbsp;&nbsp;&nbsp;&nbsp;4.nextSibling--返回节点之后紧跟的同级节点  
    &nbsp;&nbsp;&nbsp;&nbsp;5.nodeName--返回节点的名称，根据其类型  
    &nbsp;&nbsp;&nbsp;&nbsp;6.nodeType--返回节点的类型    
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;元素——1  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;属性——2  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;文本——3  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;注释——8  
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;文档——9  
    &nbsp;&nbsp;&nbsp;&nbsp;7.nodeValue--设置或返回节点的值，根据其类型  
    &nbsp;&nbsp;&nbsp;&nbsp;8.parentNode--返回节点的父节点  
    &nbsp;&nbsp;&nbsp;&nbsp;9.previousSibling--返回节点之前紧跟的同级节点  
    &nbsp;&nbsp;&nbsp;&nbsp;10.textContent--设置或返回节点及其后代的文本内容  
    &nbsp;&nbsp;&nbsp;&nbsp;11.innerHTML - 添加节点（元素）的文本值  


Node方法：  
    &nbsp;&nbsp;&nbsp;&nbsp;1.appendChild()--向节点的子节点列表的结尾添加新的子节点  
    &nbsp;&nbsp;&nbsp;&nbsp;2.cloneNode()--复制节点  
    &nbsp;&nbsp;&nbsp;&nbsp;3.insertBefore()--在指定的子节点前插入新的子节点  
    &nbsp;&nbsp;&nbsp;&nbsp;4.removeChild()--删除（并返回）当前节点的指定子节点  
    &nbsp;&nbsp;&nbsp;&nbsp;5.replaceChild()--用新节点替换一个子节点   
    &nbsp;&nbsp;&nbsp;&nbsp;6.document.createElement()--创建节点    
    &nbsp;&nbsp;&nbsp;&nbsp;7.parent.removeChild()--删除节点  
    &nbsp;&nbsp;&nbsp;&nbsp;8.getElementById(id) - 获取带有指定 id 的节点（元素）  
    &nbsp;&nbsp;&nbsp;&nbsp;9.getElementsByTagName() 返回包含带有指定标签名称的所有元素的节点列表（集合/节点数组）。   
    &nbsp;&nbsp;&nbsp;&nbsp;10.getElementsByClassName() 返回包含带有指定类名的所有元素的节点列表。   
    &nbsp;&nbsp;&nbsp;&nbsp;11.getAttribute() 返回指定的属性值。   
    &nbsp;&nbsp;&nbsp;&nbsp;12.setAttribute() 把指定属性设置或修改为指定的值。   



eg1：
留言板
    HTML：
    <body>
<div id="wrap">
       		 <div id="left">
           	 	共<input type="text" class="bor" size="1" id="total" >楼
            	 	<br>
           	 	<div id="yilou" style="display:none">
                		<div id="louzhu" class="pl3"></div>
                		<div id="neirong" class="pl2"></div>
           	 	</div>
        	 </div>
        	<div id="right">
            		<br><br>
            		输入您的姓名：<input type="text" size="20" class="bor" id="text1">
            		<br><br>
            		输入您的留言: <textarea class="bor pl" rows="20" cols="45" id="text2">
			     	      </textarea>
           		<input type="button" value="留言啦" class="pl1" onclick="queren()">
            		
       		
    	     

	
    Javascript:
	var i = 0;
	var zhi=0;
	function queren(){
    		var a=document.getElementById("text1");
    		var b=document.getElementById("text2");
    		if(a.value==0){
       			 alert("请输入用户名");
   		 }else if(b.value==0){
        		alert("请输入用户名");
   		 }else{
        		var left=document.getElementById("left");
        		var div=document.getElementById("yilou").cloneNode(true);
       			left.appendChild(div);
        		div.style.display="block";
        		var dic=div.getElementsByTagName("div");
        		dic[0].innerHTML= a.value;
        		dic[1].innerHTML= b.value;
        		div.id="yilou"+i;
        		i++;
        		zhi++;
        		var sum=document.getElementById("total");
        		sum.value=zhi;
        }
    }

eg2:
利用select中的option的值改变body属性

        function bian(attr,value){
            if(document.body)
                eval('document.body.'+attr+'="'+value+'"');
            else
                notSupported();
        }

<body>
    <form>
        <p>text&nbsp;&nbsp;</p>
        <select onchange="bian('text',this.options[this.selectedIndex].value)">
            <option value="black">black</option>
            <option value="red">red</option>
        </select>
        <p>bgcolor</p>
        <select onchange="bian('bgColor',this.options[this.selectedIndex].value)">
            <option value="green">green</option>
            <option value="yellow">yellow</option>
        </select>
        <p>link</p>
        <select onchange="bian('link',this.options[this.selectedIndex].value)">
            <option value="orange">orange</option>
            <option value="blue">blue</option>
        </select>
        <a href="jquery跑马灯.html">hhhhh</a>
    </form>
</body>
</html>