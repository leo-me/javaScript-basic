# Promise
## 背景
在promise出现之前，javascript的异步都是通过回调来实现的。

回调的问题

1.回调不符合顺序执行的大脑允许逻辑
对程序员来说，编写异步事件代码，特别是当回调是唯一的实现手段时，困难之处就在于这种思考 / 计划的意识流对我们中的绝大多数来说是不自然的。

一个回调地狱的例子：

```js
listen( "click", function handler(evt){
 setTimeout( function request(){
 ajax( "http://some.url.1", function response(text){
 if (text == "hello") {
 handler();
 }
 else if (text == "world") {
 request();
 }
 } );
 }, 500) ;
} );
```

2.回调最大的问题是控制反转，它会导致信任链的完全断裂

支付的例子,回调的第三方工具不可靠的话，不得不创建大量的混乱逻辑

内部工具函数,这等价于那条地缘政治原则：“信任，但要核实"


回调并没有为我们提供任何东西来支持这一点。我们不得不自己构建全部的机制，
而且通常为每个异步回调重复这样的工作最后都成了负担。



# 闭包

## 概念

1.一个包含数据的函数，以环境的形式包含数据

2.包含数据的方式：作用域链

3.函数：一般的函数，作用域链运行完就销毁，闭包对变量还有引用，作用域链不会销毁


应用:

管理私有变量和私有方法，将对变量（状态）的变化封装在安全的环境中
将代码封装成一个闭包形式，等待时机成熟的时候再使用，比如实现柯里化和反柯里化
需要注意的,由于闭包内的部分资源无法自动释放，容易造成内存泄露