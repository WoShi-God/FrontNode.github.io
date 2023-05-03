# 其余八股文

## 1.闭包的概念
>闭包就是函数加上对应的变量，一般在外部还会加上一个函数，使变量私有化

>函数arr包裹的就是一个闭包
```
function arr () {
    let i = 0 ;
    function f () {
        let b = i++;
    }
}
```
## 2.var、let、const区别
>var是全局作用域，let和const是块级作用域

>var可挂载window属性，let和const不行

>let定义后必须赋值否则报错

>const存储不变的量，变量会报错

## 3.flex布局
>display:flex属性，

>居中
```
display:flex;
align-item:center;
justify-content:center;
```
## 4.自适应
>应用于商品的下拉列表，只需将最外面大盒子的height不进行设置即可

>height:auto或不设置高度，里面加载出来多少盒子自动撑大