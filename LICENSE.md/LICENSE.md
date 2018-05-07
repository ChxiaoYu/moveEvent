addEventListener 这个方法有兼容性问题 ， IE和FF下绑定事件方式不一样，在补充下。


var addHandler = function(element, type, handler){
if (element.addEventListener){
element.addEventListener(type, handler, false);
} else if (element.attachEvent){
element.attachEvent("on" + type, handler);
} else {
element["on" + type] = handler;
}
}

var move = 'ontouchmove' in document ? 'touchmove' : 'mousemove' ;

addHandler(document,move,function(e){
var ev = 'ontouchmove' in document ? e.touches[0] : e ;
var x = ev.pageX ; // 这样就能在PC 和 手机上都拿到坐标值了
console.log(x);
});
