# web服务器说明文档（内部使用）
### 1.首先自定义数据文件，进行上传，上传地址：http://192.168.20.14:3000/pages/upload.html
***
### 2.配置项目跨域：
```
proxy: {
    '/': {
         target: 'http://192.168.20.14:3000/',
         ws: true,
         changeOrigin: true,
         pathRewrite: {
             '^/': ''
         }
     }
}
```
***
### 3.请求接口可用get，post，请求接口固定为 `'/get_data'`，参数为上传的文件名称
```
axios.post('/get_data', { 
    name: encodeURIComponent('test.data')}).then(function (res) {
        console.log(res.data)
    }).catch(function (error) {
        console.log(error);
    });
```
