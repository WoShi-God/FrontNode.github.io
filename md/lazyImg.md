# 图片懒加载

## 方法一(通过图片到顶部距离与可视高度和滚动条到顶部距离判断)
```
let arr =  document.querySelectorAll('img');
window.onload= LazyImg;//可视区域一看见就开始加载（初始加载）
     document.onscroll=LazyImg;//滚动条滚动监听执行
     function LazyImg(){
         // 获取屏幕显示高度（可视高度）
         const clientHeight =document.documentElement.clientHeight;
         // 获取滚动条顶部到屏幕顶部高度
         const scroll = document.documentElement.scrollTop;
         // 遍历图片数组
         for(let i = 0; i<arr.length;i++){
             // 图片顶部到屏幕顶部的距离
             let top = arr[i].offsetTop;
             // 图片到顶部距离小于可视高度和滚动条到顶部高度
             // 图片越往下高度越大，而可视高度是固定的，只有加上滚动条才满足
             if(top<clientHeight+scroll){
                 // 获取元素中的对象，对象元素是事先写入的
                 const src = arr[i].getAttribute('data-src')
                 // 为元素添加对象
                 arr[i].setAttribute('src',src)
             }
         }
     }
```

## 方法二（交叉观察，利用自带的IntersectionObserver）
```
let arr =  document.querySelectorAll('img');
// 创建交叉观察
    let observer = new IntersectionObserver(callback);
    // 遍历每一个img元素
    arr.forEach(image=>{
        // 写观察哪一个元素，i就是每一个img元素
        observer.observe(image);
    })
    // 交叉观察的回调函数
    function callback(e) {
        // e是观察的所有的img元素
        e.forEach(item=>{
            // 只要在可视区范围 item.isIntersecting 值等于true
            // 不在可视范围的都为false，不显示图片
            if(item.isIntersecting){
                // img获取的显示了的图片元素
                const img = item.target;
                const src= img.getAttribute('data-src');
                img.setAttribute('src',src);
                // 取消observer的观察动作，使其不会一直观察
                observer.unobserve(img);
            }
        })
    }
```