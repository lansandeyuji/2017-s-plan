# 2017时间线
2017.1.3
 - 2017计划概要完成

 - vue 慕课网 入门教学：
 	1.使用vue-cli命令包
 	2.使用vue 脚手架-webpack打包方式进行初始化项目，实现页面自动编译刷新等。
 	3.使用es6编写，采用babel编译。 
 	4.实现一个todolist:可以在input框输入，按enter保存到todolist列表上，点击每个item可以实现完成状态的改变，在刷新页面时使用 localstorage来读取初始数据，并在watch这个list列表，保存到localstorage里。所用到的指令有：v:click = "" v-bind:title = "" v-model v-for  v-text v-html v-show <app> </app>  app即是一个自定义的vue组件，每一个组件.vue文件 包括三个部分：<template></template> <script></script> <style></style>
 	5.父组件 告诉子组件，通过子组件定义Props属性来决定，被定义的父组件的数据可以被子组建获取到。
 	  子组件通知父组件，通过父组件监听事件，子组件emit事件来完成
    6.http://www.alloyteam.com/2015/06/mvvm-xue-xi-vue-shi-jian-xiao-jie/
    7.https://www.zhihu.com/question/38213423
 - promise 温故而知新，jquery的deffered对象。 http://imweb.io/topic/57a0760393d9938132cc8da9
    三个状态，pending,resolve,reject。
    一定要返回promise对象，否则 会遗漏某个分支流程。 
    采用catch来捕获reject的promise 
    请大家记住三点：
		回调方法中一定要使用return语句，避免调用者丢失其处理状态与结果。
		在promise实例的最后使用catch方法，用来做整体的异常捕获与处理。
		利用Promise.then方法对回调函数返回结果的封装，写出清晰漂亮的链式调用代码。

2017.1.4
 - 作用域：函数作用域和块级作用域.块级作用域是指一对花括号包围的。而函数作用域是在一个函数内
 比如以下代码： 

 ```javascript
 	int main(){
 	int i=1;
 		if(i){
 		 int j= 1;
 		}
 		printf('%d\n',j) //这里是访问不到j变量的，因为c语言是块级作用域，在花括号外是访问不到花括号里面的变量的。
 	}

 	functin test(){ 
		for(var i=0;i<3;i++){ 
		} 
		alert(i); 
	} 
	test(); //这里是可以访问到i变量的。因为javascript是函数作用域。

	//所以为了较好的保护变量作用域，将代码使用函数包起来，可以防止变量暴漏在全局作用域

	(function (){ 
		//内容 
	})(); //这时候，我们是不是相当于给它们的外层添加了一个函数作用域呢？该作用域之外的程序是无法访问它们的。

```

- 闭包：了解了作用域，我们知道一般情况下，在函数外部是访问不到函数里面的变量的，但有时候我们需要访问函数内部的变量，这要怎么做呢？

 ```javascript
	function f1(){
　　　　var n=999;
　　　　function f2(){
　　　　　　alert(n);
　　　　} 
        return f2;
　　}
　  var result=f1();
　  result();// 弹出999
 ```

上面函数中的f2函数就是闭包，就是通过建立函数来访问函数内部的局部变量。

闭包可以用在许多地方。它的最大用处有两个，一个是前面提到的可以读取函数内部的变量，另一个就是让这些变量的值始终保持在内存中。

```javascript
	var name = "The Window";
　　var object = {
　　　　name : "My Object",
　　　　getNameFunc : function(){
　　　　　　return function(){
　　　　　　　　return this.name;
　　　　　　};
　　　　}
　　};
　　alert(object.getNameFunc()());//The Window

　  var name = "The Window";
　　var object = {
　　　　name : "My Object",
　　　　getNameFunc : function(){
　　　　　　var that = this;
　　　　　　return function(){
　　　　　　　　return that.name;
　　　　　　};
　　　　}
　　};
　　alert(object.getNameFunc()());//My Object

```

 - dns解析 反向代理

  http://imweb.io/topic/554b695fdca54b7c488f4040

 - 函数节流
 
 http://imweb.io/topic/577aa790ea7bb9b760c7adc3
 函数节流的经典应用场景：onresize，scroll，mousemove ,mousehover等事件回调函数的无间断执行。其主要实现思路就是通过setTimeout定时器，通过设置缓冲时间，在第一次调用时，创建定时器，并在定时时间结束调用。第二次调用时，会清除前一个定时器并设置新的定时器。如果这时前一个定时器暂未执行，则将其替换为新的定时器。目的在于在一定的时间内，保证多次函数的请求只执行最后一次调用。

 - clientHeight offsetHeight  scrollHeight scrollTop offsetTop http://imweb.io/topic/57c5409e808fd2fb204eef52 https://developer.mozilla.org/en-US/docs/Web/API/Element/clientHeight