#JSON入门指引
####一、JSON的使用语法

JSON 语法是 JavaScript 对象表示法语法的子集。  
1 . 数据在名称/值对中  
2 . 数据由逗号分隔  
3 . 花括号保存对象  
4 . 方括号保存数组  

JSON 数据的书写格式是：名称/值对。  
名称/值对包括字段名称（在双引号中），后面写一个冒号，然后是值：
	
/ / json对象
	
	姓名：<span id="jname"></span><br>
    年龄：<span id="jage"></span><br>
    电话: <span id="jphone"></span><br>
    <script>
        var JsonObject={
            "Name":"pig",
            "Age":21,
            "Phone":13069106015,

        };
        document.getElementById("jname").innerHTML=JsonObject.Name;
        document.getElementById("jage").innerHTML=JsonObject.Age;
        document.getElementById("jphone").innerHTML=JsonObject.Phone;
    </script> 
/ / json 数组（可以使用js调用）

	    姓名：<span id="jname"></span><br>
    年龄：<span id="jage"></span><br>
    电话: <span id="jphone"></span><br>
    <script>
        var JsonObject=[
            {"name":"小红子","age":15},
            {"name":"小李子","age":20},
            {"name":"小种子","age":35}
        ];
        document.getElementById("jname").innerHTML=JsonObject[1].name;
    </script>  
/ /来自字符串的对象

	姓名：<span id="jname"></span><br>
    年龄：<span id="jage"></span><br>
    电话: <span id="jphone"></span><br>
    <script>
        var test='{info:['+
            '{"name":"zhu","age":17},'+
            '{"name":"niu","age":20}]}';
        var obj=eval("("+test+")");
        document.getElementById("jname").innerHTML=obj.info[0].name;
    </script>

#####eval：它的功能是把对应的字符串解析成 js 代码并运行，缺点是：不安全，非常耗费性能，（两次执行，一次解析成js代码，一次执行）
