## Node upload-image demo
主要演示如何利用connect-multiparty中间间进行图片的上传。
* 需要在引入connect-multiparty

><pre><code>var mutipart= require('connect-multiparty')
            
</code></pre>

* 服务器端主要代码
 ```javascript
var express = require('express');
var mutipart= require('connect-multiparty');
var mutipartMiddeware = mutipart();
var app = express(); 
app.use(mutipart({uploadDir:'./linshi'}));
app.set('port',process.env.PORT || 3000);
app.get('/',function (req,res) {
    res.type('text/html');
    res.sendfile('public/index.html')

});
app.post('/upload',mutipartMiddeware,function (req,res) {
    console.log(req.files);
    res.send('upload success!');
});

 ``` 
 * 客户端主要代码：
 ```html
    <form action="/upload" enctype="multipart/form-data" method="post">
            <p>附件：<input type="file" name="myfile" style=""></p>
            <p>
                <input type="submit">
            </p>
        </form>
 ```
## 项目结构
* linshi     //上传文件存放路径
* public     //静态文件存放目录

## 项目启动方式
node app.js
