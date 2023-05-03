# 请求拦截器

## 1.新建拦截器JS文件
```
   直接在所有API文档
   import 'axiosInterceptors.js'  即可
   主要引入到封装Api的js中每次请求都会先走请求拦截器
```
## 2.添加请求拦截器
```
axios.interceptors.request.use(function (config) {
    // 在发送请求之前做些什么
    return config;
  }, function (error) {
    // 对请求错误做些什么
    return Promise.reject(error);
//   这个reject里面可以自己定义错误信息
//   如：{...error, myerror:'为什么错了'}
  });
```
## 3.添加响应拦截器
```
axios.interceptors.response.use(function (response) {
    // 2xx 范围内的状态码都会触发该函数。
    // 对响应数据做点什么
    return response;
  }, function (error) {
    // 超出 2xx 范围的状态码都会触发该函数。
    // 对响应错误做点什么
    return Promise.reject(error);
  });

```
## 4.在前端的页面路由拦截鉴权主要是靠存储在本地localstore里面的token值
```
 例在react的Routes当中：
    <Route path=""  component=(Token ? <AdminHome/> : <Login/> ) /> 
```