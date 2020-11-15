# 起步

## 1.安装node环境

- 官网：[https://node.js.org]()
- 安装：1.一路 next就可以了
- ​            2.对于已经安装的，从新安装就会升级
- 确认node确认是否安装成功：
- 打开命令行。输入 node --version
- 或 node-v

**node环境安装失败解决办法：**

错误代码2502、2503

失败原因：系统账号权限不足

解决办法：

- 以管理员身份运行powershell命令行工具
- 输入运行安装包命令msiexec /package node安装包位置

![image-20201001155123189](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201001155123189.png)

**执行命令报错**

失败原因：node安装目录写入环境变量失败

解决办法：将node安装目录添加到环境变量中

找到node安装目录—复制node.exe的路径—此电脑，右键点击属性，点击高级系统配置，在高级选显卡点击环境变量，在系统环境变量里面，找到一个变量的名字path，双击打开，点击新建，粘贴刚复制的路径—一直确定—重启命令行窗口

**path环境变量：**

存储系统的目录，在命令行中的时候系统会自动去这些目录查找命令的位置

# node.js快速入门

### 1.node.js的组成

node.js是由ECMAScript及node环境提供的一些附加API组成的，包括文件、网络、路径等一些更加强大的API

只要在命令行输入==clear==所有命令都会被清除。

在输入文件名称的时候一定要在前面加==node 文件名==，如果文件名过长，可以只输入文件名的开头部分，按==tab==补齐

# node 模块化开发

### 1.JavaScript开发弊端

JavaScript在使用时存在两大问题。==文件依赖==和==命名冲突==

# node.js中模块化开发

### 1.node.js中模块化开发规范

![image-20201001165833424](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201001165833424.png)

### 2.模块成员导入

node中模块化开发需要两步：

第一步： *通过 exports 对模内部的成员进行导出*

![image-20201001171953365](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201001171953365.png)

第二步： *通过 require方法对依赖的模块进行导入*

![image-20201001172012291](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201001172012291.png)

### 3.模块成员导出的另一种方式

```node.js
module.exports.version = version;
module.exports.sayHi = sayHi;
```

==exports==是==module.exports==的别名（地址引用关系），导出对象最终以module.exports为准

![image-20201002113349526](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201002113349526.png)

# 系统模块

### 1.系统模块==fs== 文件操作

f : file文件   s : system 系统   文件操作系统

```
const fs = require('fs')
```

**读取文件内容：**

```
fs.readFile('文件路径/文件名称' [,'文件编码'],callback);
```

![image-20201002115618432](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201002115618432.png)

文件读取出错：

![image-20201002115722703](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201002115722703.png)

**写入文件内容：**

```
fs.writeFile('文件路径/文件名称' ,'数据',callback);
```

![image-20201002194343944](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201002194343944.png)

### 2.系统模块==path==路径操作

**路径拼接语法：**

```
path.join('路径','路径'...)
```

![image-20201002195637712](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201002195637712.png)

![image-20201002195709340](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201002195709340.png)

**相对路径和绝对路径：**

- 大多情况下使用绝对路径，因为相对路径有时候相对的是命令行工具的当前工作目录
- 在读取文件或者设置文件路径时都会选择绝对路径
- 使用==—dirname==获取当前文件所在的绝对路径

# 第三方模块
### 1.什么是第三方模块

别人写好的、具有特定功能的、我们能直接使用的模块即第三方模块，由于第三方模块通常由多个问价组成并且被放置在一个文件夹中，所以又称==包==
#### 1.1第三方模块有两种存在形式：
- 以js文件存在，提供实现项目具体功能的API接口
  以命令行工具形式存在，辅助项目开发



### 2.获取第三方模块
==npmjs.com==：第三方模块的存储和分发仓库。
==npm（node package manager)==：node的第三方模块管理工具

**下载：npm install模块名称**

![image-20201003113818257](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201003113818257.png)

![image-20201003114533761](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201003114533761.png)

**卸载：npm uninstall package**


![image-20201003114338674](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201003114338674.png)

![image-20201003114501640](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201003114501640.png)

**全局安装与本地安装：**
1. 命令行工具：全局安装
2. 库文件：本地安装

### 3.第三方模块==nodemon==
nodemon是一个命令行工具，用以辅助项目开发。
在node.js中，每次修改文件都要在命令行工具中重新执行该文件，非常繁琐。

**使用步骤：**
1. 使用npm install nodemon-g(g代表全局安装)下载它
2. 在命令行中用==nodemon==命令代替==node==命令执行文件

![image-20201003115824393](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201003115824393.png)

**如何断开当前nodemon操作？直接ctrl + c**
**在命令行 ctrl + c是终止操作**
### 4. 第三方模块==nrm==
nrm : npm下载地址切换。
npm默认下载的地址在国外，国内的下载速度慢。

**使用步骤：**
1. 使用npm install nrm -g下载
2. 查询可用下载地址列表nrm ls
3. 切换npm下载地址 nrm use 下载地址名称

注：下载地址带有 * 默认你的下载地址

### 5. 第三方模块 ==Gulp==
1. 基于node平台开发的前端构键工具
2. 将机械化操作编写成任务，想要执行机械化操作时执行一个命令行命令任务就能自动执行了
3. 用机器代替手工，提高开发效率，如敲击一个命令就能实行css代码的压缩

#### 5.1 Gulp能做什么
1. 项目上线，HTML、CSS、JS文件压缩
2. 语法转换（es6、less...)
3. 公共文件抽离
4. 修改文件浏览器自动刷新
#### 5.2 Gulp使用
1. 使用npm install gulp 下载gulp库文件

   ![image-20201006114224559](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201006114224559.png)

2. 在项目根目录下建立gulpfile.js文件夹

   ![image-20201006114248557](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201006114248557.png)

3. 重构项目的文件夹结构 src 目录放置==源代码文件== dist目录放置==构建后文件==

   ![image-20201006114752000](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201006114752000.png)

4. 在gulpfile.js文件中编写任务

5. 在命令工具中执行gulp任务

#### 5.3 Gulp中提供的方法
1. ==gulp.src()==:获取任务要处理的文件
2. ==gulp.dest()==: 输出文件
3. ==gulp.task()==: 建立gulp任务
4. ==gulp.watch()==:监控文件的变化

```node
// 引入gulp模块
const gulp = require('gulp');
// 使用gulp.task建立任务
// 1.任务的名称
// 2.任务的回调函数
gulp.task('first', () => {
    console.log('第一个gulp任务执行');
    // 1.使用gulp要处理的文件
    gulp.src('./src/css/base.css');
    gulp.pipe(gulp.dest('dist/css'));
});
```

#### 5.4 gulp插件
gulp-htmlmin:html文件压缩
gulp-csso:压缩css
gulp-babel:JavaScript语法转化
gulp-uglify:压缩混淆javascript
gulp-file-include:公共文件包含
browsersync浏览器同步

**插件使用步骤：**
1. 下载
2. 引用
3. 调用

# package.json文件
### 1.node_modules文件夹的问题
1. 文件夹以及文件过多，当将项目整体拷贝给别人的时候，传输速度会很慢
可以不用传输node.modules文件夹，直接在命令行使用npm install即可
2. 复杂的模块依赖关系需要被记录，确保模块的版本和当前的保持一致，否则会导致当前项目运行报错

### 2.package.json文件的作用

项目描述文件，记录了当前项目信息，例如名称、版本、作者、github地址、当前项目依赖了那些第三方模块等
**使用==npm init -y==生成，要放在根目录下**

### 3.package.json文件

![image-20201011155444213](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201011155444213.png)

![image-20201011155512035](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201011155512035.png)

# node.js中模块加载机制

### 1.模块查找规则-当模块拥有路径但没有后缀

![image-20201011161425030](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201011161425030.png)

# 服务器端基本概念

### 1. URL

![image-20201014214611186](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201014214611186.png)

### 2. 开发过程中客服端和服务器端说明

![image-20201014214742017](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201014214742017.png)

# 创建web服务器

### 1.创建web服务器

![image-20201014220719160](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201014220719160.png)

### 2.http协议

**http协议的概念：**

![image-20201014221148177](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201014221148177.png)

**报文：**

![image-20201014221230121](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201014221230121.png)

**请求报文：**

![image-20201016215632880](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201016215632880.png)

**请求参数：**

请求参数分为：GET请求参数和POST请求参数

POST请求：

参数放置在请求体中进行传输

获取post参数需要使用data和end事件

使用querystring系统模块将参数转化为对象格式

```javascript
//处理请求参数方法
const querystring = require('querystring');
//3.为网站服务添加一个请求事件 当客服端有请求的时候
http.on('request', (req, res) => {
    //post参数是通过事件的方式接收的
    //data 当请求参数传递的时候触发data事件
    //end当参数传递完成的时候触发end事件
    //post请求参数，不是一次接收完的，为了减轻服务器压力，会分好几次接收
    let postParams = ''
    req.on('data', params => {
        postParams += params;
    });
    req.on('end', () => {
        // 调用querystring方法 把字符串转化为对象  
        console.log(querystring.parse(postParams));
    });
    req.end('ok');
});
```
**路由：**

![image-20201018153142891](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201018153142891.png)

```javascript
//1.引入系统模块http
const http = require('http');
const url = require('url');
//2.创建网站服务器
const app = http.createServer();

//3.为网站服务器对象添加请求事件  实现路由功能
app.on('request', (req, res) => {
    // 获取客户端的请求方式
    //req.method 返回的是大写的post 和大写的get 通常转化为小写，调用toLowerCase()
    const method = req.method.toLowerCase();
    // 获取客户端的请求地址
    // req.url()
    //url.parse 可以给url 进行解析， 返回url地址的各个部分
    // pathname 请求地址
    const psthname = url.parse(req.url).pathname;

    //在客户端看到的是一堆乱码  所以要响应报文的处理
    res.writeHead(200, {
        'content-type': 'text-html; charset=utf8'
    });

    if (method == 'get') {
        if (pathname == '/' || pathname == '/index') {
            res.end('欢迎来到首页')
        } else if (pathname == '/list') {
            res.end('欢迎来到列表页')
        } else {
            res.end('访问的页面不存在')
        }

    } else if (method == 'post') {

    }
});

//4.监听端口
app.listen(3000);
console.log('服务器启动成功');
```

**静态资源：**

什么是静态资源：服务器端不需要处理，可以直接响应给客服端就是静态资源，例如css、javascript、image文件

什么是动态资源：相同的请求地址不同的响应资源

```javascript
//1. 用于创建网站服务器模块
const http = require('http');
const url = require('url')
const path = require('path');
const { fstat } = require('fs');
http.on('request', (req, res) => {
    //获取用户的请求路径
    let psthname = url.parse(req.url).pathname;
    
    // 获取绝对路径
    // path.join(__dirname,'public' + pathname)
    //将用户的请求路径转化为实际的服务器硬盘路径
    let realPath = path.join(__dirname,'public' + pathname);
    
    //读取文件
    fs.readFile(realPath,(error,result) => {
        if(error != null){
            res.writeHead(200, {
                'content-type': 'text-html; charset=utf8'
            })
            res.end('文件读取失败');
            return;
        }
       
    })
});

//4.监听端口
app.listen(3000)
console.log('网站服务器启动成功');
```

# node.js 同步编程

### 1.同步API，异步API

![image-20201018164926678](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201018164926678.png)

### 2.同步API和异步API的区别（获取返回值）

```javascript
function getMsg(callback) {
    // 在getMsg不能通过return来拿到返回值
    setTimeout(function() {
        callback({
            msg: 'hello node.js'
        })
    }, 2000)
}
getMsg(function(data) {
    console.log(data);
});
```

### 3.同步API和异步API的区别（代码执行顺序）

![image-20201021213800051](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201021213800051.png)

![image-20201021213837852](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201021213837852.png)

### 4. node.js 中的异步API

![image-20201021221015883](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20201021221015883.png)