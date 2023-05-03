# 父子组件传值

> 在使用子组件中 show={open} setShow={setOpen}  父组件直接在子组件当中将值传入

>子组件直接接受结构出值
>export default function Son(props) 
>    父组件传过来的props里面包含show，setShow值，直接结构出来便可
>   const {show,setShow}=props


## 父组件
```
import { Button } from 'antd';
import { useState } from 'react';
import Son from './子组件'
export default function father() {
    const [open,setOpen]=useState(false)
    // 在该父组件改变状态
    const handClick = ()=>{
        setOpen(!open)
    }

    return (
        <div>
            {/* 在子组件从show获取open值 */}
            {/* 通过这种形式传值给该子组件 */}
            <Son show={open} setShow={setOpen} />

             <Button size={'large'} onClick={handClick}  >点击显示抽屉，实现组件传值（父组件按钮）</Button>
             
        </div>
    )
}
```

## 子组件
```
import {  Drawer } from 'antd';
export default function Son(props) {
    // 父组件传过来的props里面包含show，setShow值，直接结构出来便可
    const {show,setShow}=props
    // 该函数子组件控制show状态
    const onClose = () => {
        setShow(false);
      };
    return (
        <div>
         <Drawer
        title="子组件抽屉"
        placement={'bottom'}
        closable={false}
        onClose={onClose}
        // open接收的是从父组件传来的show参数里面的open值
        open={show}
      >
        <p>Some contents...</p>
        <p>Some contents...</p>
        <p>Some contents...</p>
      </Drawer>
        </div>
    )
}
```