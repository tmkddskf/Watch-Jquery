# Watch-Jquery1.0 [Download](https://github.com/tmkddskf/Watch-Jquery/master/src/watch.js)

## 关于

这是一个基于Watch.js 1.4.2实现的对象状态监控工具。类似Vue的部分功能。完全不使用html上的标记，有时候可能会对你有点用。（依赖JQuery!!）

## Compatible with all serious browsers :P
Works with: IE 9+, FF 4+, SF 5+, WebKit, CH 7+, OP 12+, BESEN, Node.JS , Rhino 1.7+

#### 引入
```html
<script src="watch.js" type="text/javascript"></script>
<!-- watch will be a global variable -->
```

## 定义操作

```javascript
$.formStatusControl().formReadOnly = function(result, el, newValue, oldValue, key) {
	//result是自定义(例如上面的"watch.formId")表达式的结果，可以是字符串，也可以是一个函数。
	//el是element所对应的JQuery对象
	//newValue是本次状态变动前的值
	//oldValue是本次状态变动后的值
	//key是本次触发改变的属性名称
}
```

## 使用代码

```javascript
//设置监控点
var watch = {"projStatus": 0, "formId" : null};
//设置监控操作
var statusCtl = $.formStatusControl();
statusCtl.init({
    watch: watch,
    elements: [
        {
            element: "#projectName,#projectCode,#wtCstName,#startDate",
            formReadOnly: "watch.formId != ''",
            formTitleRed: function(watch,el,newValue,oldValue) { return watch.projStatus != 1; }
        }
    ]
});
//触发监控，比如这个例子。只要formId变化就会执行formReadOnly这个操作。只要projStatus变化就会执行formTitleRed这个操作
watch.projStatus = 1;
watch.formId = getFormId();
```
