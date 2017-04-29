# 什么是事件委托
	对事件处理过多问题的解决方案就是事件委托
# 事件委托的原理
	利用了事件冒泡，只指定一个事件处理程序，就可以管理某一类的所有事件

#Demo(index.html)
	这是我们通常写代码的做法，给每个点击事件添加相对应地函数
	var item1=document.getElementById("goSomewhere");
	var item2=document.getElementById("doSomewhere");
	var item3=document.getElementById("dclick");

	var EventUtil={
		addHandler:function(ele,type,handler){
			if(ele.addEventListener){
				ele.addEventListener(type,handler,false);
			}else if(ele.attachEvent){
				ele.attachEvent("on"+type,handler);
			}else{
				ele["on"+type]=handler;
			}
		}
	};
	EventUtil.addHandler(item1,"click",function(event) {
		location.href="http://www.baidu.com";
	});
	EventUtil.addHandler(item2,"click",function(event) {
		document.title="变化的document标题"
	});
	EventUtil.addHandler(item3,"click",function(event) {
		alert("这是item3的点击事件");
