#### 面试经历
```
2019年8月参与了网易游戏前端的一场面试，这里重新整理总结一下，有错漏地方还望诸位雅正
一共经历了一轮笔试两轮技术面一轮主管面加上一轮HR面，前四轮是在现场面试，从下午两点面到下午五点，HR面另外约时间
虽然最后遗憾没拿到offer，但是也感谢这次机会
```
#### CSS
- [css布局题目](#css1)  

#### 浏览器移动端兼容性
- [考虑浏览器兼容性获取指定div中所有checkbox](#browser1)
- [移动端图片选择](#browser2)
- [base64相关](#browser3)


#### 计算机基础
- [前端安全（XSS CSRF 网络劫持攻击 控制台注入代码 钓鱼）](#computeBase1)  
- [什么是正向代理，什么是反向代理](#computeBase2)
- [https和握手的联系](#computeBase3)  
- [iframe跨域 多个页面间通讯](#computeBase4)  
- [jsonp跨域解决方案的缺点](#computeBase5)  
- [postMessage跨域通讯](#computeBase6)
- [CORS配置对某几个请求允许跨域](#computeBase7)
- [DNS服务器解析过程](https://zhuanlan.zhihu.com/p/38499577)  

#### 算法
- [矩阵从左上角到右下角有多少种走法](#algorithm1) 
- [快速打乱数组的方法（洗牌算法）](#algorithm2)  
- [模板编译](#algorithm3) 

#### js
- [写一个求和函数使得sum(1)(2) sum(1, 2) 两种最后取得结果相同（结果都是3）](#js1)

#### node.js
- [nodejs压测](#node1)  
- [buffer上限，stream和buffer对比](#node2)  
- nodejs除了封装接口外还可以用在那些方面
- [nodejs日志管理，是否有可视化界面](#node4)  


#### 框架
- [angular依赖注入的底层实现](#frame1)  
- [angular懒加载(ocLazyLoad,配合uiRouter使用)](https://www.cnblogs.com/sxz2008/p/6287958.html)  
- [angular相关面试题](https://www.w3cschool.cn/angularjs/angularjs-8c2q2ord.html)
- [vue组件重置数据的方法](#frame4)  
- [vuex和全局变量的本质区别](#frame5)  
- [vue生命周期以及每个生命周期都做了啥](https://juejin.im/post/5ba34e54e51d450e5162789b#heading-62)  


#### 项目相关
- 项目用gulp打包如何加载依赖（assest.js）gulp打包和webpack的区别 
- 现在假设要在一个系统的所有按钮上增加一个节流或者防抖方法，最快的方法是啥  
- 调用后端接口除了http请求外还有什么方法（graphQL）

#### 工程化及部署
- [docker image](https://juejin.im/post/5ad3172c5188257ddb10109a)  
- 如何回滚代码   
- docker回滚  
- [git rebase和Git merge的区别](https://juejin.im/post/5af26c4d5188256728605809) 
- [git rebase操作](https://blog.csdn.net/itfootball/article/details/44154121)
- [git 选择几个commit合并到某个分支（单个用cherryPick，单个用rebase）](https://blog.csdn.net/ybdesire/article/details/42145597)  

#### 数据库
- [redis操作，除了保存sesson token还可以做些啥](#database1)  
- [数据库 事物是啥](https://www.jianshu.com/p/eb150b4f7ce0)  
- mysql和mongo的区别(网上很多资料，这里不再赘述)


<html><span id="css1"></span></html>

####  css布局题目 
[效果图片](http://note.youdao.com/noteshare?id=f035e9f3b3dfde1d723e5a395f956b8d)
```
 <div class="box">
        <div class="content">
            <ul>
                <li>1</li>
                <li>2</li>
                <li>3</li>
                <li>4</li>
                <li>5</li>
            </ul>
        </div>
    </div>

    <style>
        .box {
            width: 400px;
            height: 400px;
            display: block;
            border: 1px solid blueviolet;
        }
        .content {
            width: 100%;
            height: 50%;
            margin-top: 200px;
        }
        ul {
            padding-left: 0;
            display: flex;
            flex-direction: row-reverse;
            justify-content: space-around;
            align-items: center;
            width: 100%;
            height: 100%;
        }
        li {
            list-style: none;
            border: 1px solid black;
            width: 50px;
            height: 100px;
            line-height: 100px;
            text-align: center;
            vertical-align: middle;
        }
        li:nth-child(3) {
            height: 200px;
            line-height: 200px;
            vertical-align: middle;
        }
    </style>
```

<html><span id="browser1"></span></html>

####  考虑浏览器兼容性获取指定div中所有checkbox
```
不兼容IE6 IE7。。。
document.querySelectorAll("div>input[type=checkbox]")
兼容IE6 IE7 链接 https://www.jianshu.com/p/872d69047dda
```

<html><span id="browser2"></span></html>

####  移动端图片选择
```
1.不用图片。很多时候会使用到很多修饰类图片，其实这类修饰图片完全可以用 CSS 去代替。
2.对于移动端来说，屏幕宽度就那么点，完全没有必要去加载原图浪费带宽。一般图片都用 CDN 加载，可以计算出适配屏幕的宽度，然后去请求相应裁剪好的图片。
3.小图使用 base64 格式
4.将多个图标文件整合到一张图片中（雪碧图）
5.选择正确的图片格式：

对于能够显示 WebP 格式的浏览器尽量使用 WebP 格式。因为 WebP 格式具有更好的图像数据压缩算法，能带来更小的图片体积，而且拥有肉眼识别无差异的图像质量，缺点就是兼容性并不好
小图使用 PNG，其实对于大部分图标这类图片，完全可以使用 SVG 代替
照片使用 JPEG
```

<html><span id="browser3"></span></html>

####  base64相关
```
DataURI 允许在HTML文档中嵌入小文件，可以使用 img 标签或 CSS 嵌入转换后的 Base64 编码，减少 HTTP 请求，加快小图像的加载时间。

经过Base64 编码后的文件体积一般比源文件大 30% 左右。

// Base64 在CSS中的使用
.box{
  background-image: url("data:image/jpg;base64,/9j/4QMZR...");
}
// Base64 在HTML中的使用
<img src="data:image/jpg;base64,/9j/4QMZR..." />
```


<html><span id="computeBase1"></span></html>

#### 前端安全（XSS CSRF 网络劫持攻击 控制台注入代码 钓鱼） [参考链接](https://juejin.im/entry/584b880a8e450a006c590576)
```
XSS
它允许恶意web用户将代码植入到提供给其它用户使用的页面中，简单理解为js代码注入
例子：在用户名中含有script标签，就可以执行其中的代码
解决方案：前端对输入输出数据都进行转义
例子：jquery的append往innerHTML中注入script
解决方案：对<script>标签进行转义
例子：利用img标签加载失败时调用onerror事件进行攻击
解决方案：还是转义。。。
例子：用get从url中获取参数的时候往参数中加入js代码
解决方案：不要拿url中的参数去eval
例子：黑客读取cookie
解决方案：使用cookie的HttpOnly属性，加了这个字段js是无法对cookie进行读写的

CSRF
跨站请求伪造，其实就是网站中的一些提交行为，被黑客利用，你在访问黑客的网站的时候，进行的操作，会被操作到其他网站上(如：你所使用的网络银行的网站)。
例子：读取get请求中的参数
解决方案：严格按照post请求去操作，不要使用jsonp去做提交型接口
例子：post请求，用户在不知情的情况下提交了表单，服务器也以为是用户提交过来的
解决方案：增加验证码 每次请求都校验token

网络劫持攻击
数据被中间代理层的劫持者截获盗取数据，如连接第三方WiFi
解决方案：用HTTPS 表单提交用非对称加密--即客户端加密，只有服务端能解开

控制台注入代码
解决方案：控制台警告用户不要做这种操作

钓鱼
在第三方网站输入账号密码，如QQ盗号
```

<html><span id="computeBase2"></span></html>

#### 什么是正向代理，什么是反向代理 [参考链接](https://juejin.im/entry/586e6835ac502e12d63ecd5c)
```
正向代理
科学上网，无法访问某个网站，在国务搭建一台代理服务器，让代理帮我请求那个网站,代理吧请求返回的结果再返回给我。
反向代理
拨打10086，背后有多个客服提供服务，客户只需要拨打10086总机号码不需要真正提供服务的是哪位
Nginx就是性能非常好的反向代理服务器，用来做负载均衡。
两者的区别在于代理的对象不一样：正向代理代理的对象是客户端，反向代理代理的对象是服务端
```

<html><span id="computeBase3"></span></html>

#### https和握手的联系 [参考链接](https://juejin.im/entry/5a644a61f265da3e4c07e334)
```
常说的三次握手四次挥手那是TCP传输层的，https是应用层的，不要搞乱了
https=http+ssl
HTTPS完整建立连接过程
1. 首先建立tcp 握手连接  
2. 进行ssl 协议的握手密钥交换(Handshake protocal)  
3. 然后通过共同约定的密钥开始通信  
```

<html><span id="computeBase4"></span></html>

#### iframe跨域 多个页面间通讯 [参考链接](https://zhuanlan.zhihu.com/p/50193200)
```
方法调用
父页面调用子页面方法：FrameName.window.childMethod();
子页面调用父页面方法：parent.window.parentMethod();
DOM元素访问
获取到页面的window.document对象后，即可访问DOM元素
跨域父子页面通信方法
如果iframe所链接的是外部页面，因为安全机制就不能使用同域名下的通信方式了。
父页面向子页面传递数据
实现的技巧是利用location对象的hash值，通过它传递通信数据。在父页面设置iframe的src后面多加个data字符串，然后在子页面中通过某种方式能即时的获取到这儿的data就可以了，例如：
1. 在子页面中通过setInterval方法设置定时器，监听location.href的变化即可获得上面的data信息
2. 然后子页面根据这个data信息进行相应的逻辑处理
子页面向父页面传递数据
实现技巧就是利用一个代理iframe，它嵌入到子页面中，并且和父页面必须保持是同域，然后通过它充分利用上面第一种通信方式的实现原理就把子页面的数据传递给代理iframe，
然后由于代理的iframe和主页面是同域的，所以主页面就可以利用同域的方式获取到这些数据。
使用 window.top或者window.parent.parent获取浏览器最顶层window对象的引用。
```

<html><span id="computeBase5"></span></html>

#### jsonp跨域解决方案的缺点
```
只能用get请求，只支持跨域HTTP请求这种情况，不能解决不同域的两个页面之间如何进行JavaScript调用的问题
JSONP的优势在于支持老式浏览器，弊端也比较明显：需要客户端和服务端定制进行开发，服务端返回的数据不能是标准的Json数据，而是callback包裹的数据。
```

<html><span id="computeBase6"></span></html>

#### postMessage跨域通讯
```
通常用于获取嵌入页面中的第三方页面数据。一个页面发送消息，另一个页面判断来源并接收消息
// 发送消息端
window.parent.postMessage('message', 'http://test.com');
// 接收消息端
var mc = new MessageChannel();
mc.addEventListener('message', (event) => {
    var origin = event.origin || event.originalEvent.origin; 
    if (origin === 'http://test.com') {
        console.log('验证通过')
    }
});
```

<html><span id="computeBase7"></span></html>

#### CORS配置对某几个请求允许跨域 [参考链接](https://www.jianshu.com/p/b587dd1b7086)
```
Access-Control-Allow-Origin只允许设置一个，所以只能通过代码来配置
先自己判断域名是否是允许的，如果是再设置允许跨域访问。那么代码应该改成如下形式
app.all('*', function(req, res, next) {
    if( req.headers.origin == 'https://www.juejin.com' || req.headers.origin == 'https://www.baidu.com' ){
        res.header("Access-Control-Allow-Origin", req.headers.origin);
        res.header('Access-Control-Allow-Methods', 'POST, GET');
        res.header('Access-Control-Allow-Headers', 'X-Requested-With');
        res.header('Access-Control-Allow-Headers', 'Content-Type');
    }
    next();
});
```

<html><span id="algorithm1"></span></html>

#### 矩阵从左上角到右下角有多少种走法
```
面试的时候是给出了一种效率有点低的做法，构造一棵树，获取一共有多少总走法 
2020.5.2更新，动态规划法
function matrixCount(i, j) {
  let dpList = [];
  for (let k = 0; k <= i; k++) {
    dpList.push([]);
    for (let y = 0; y <= j; y++) {
      dpList[k][y] = '';
    }
  }
  console.log(dpList);

  function dp(i, j) {
    if (i === 0 && j === 0) {
      dpList[i][j] = 0;
      return 0;
    }
    if (i === 0 || j === 0) {
      dpList[i][j] = 1;
      return 1;
    }
    let tempResult1 = dpList[i][j - 1] !== '' ? dpList[i][j - 1] : dp(i, j - 1);
    let tempResult2 = dpList[i - 1][j] !== '' ? dpList[i - 1][j] : dp(i - 1, j);
    dpList[i][j] = tempResult1 + tempResult2;
    return dpList[i][j]
  }
  dp(i, j);
  console.log(dpList);
  return dpList[i][j];
}

let result = matrixCount(8, 8);
console.log(result);
```

<html><span id="algorithm2"></span></html>

#### 快速打乱数组的方法（洗牌算法） [参考链接](https://www.zhihu.com/question/68330851)
```
1.Fisher–Yates shuffle 洗牌算法
2.lodash shuffle方法
```

<html><span id="algorithm3"></span></html>

#### 模板编译 [参考链接](https://www.yukapril.com/2017/01/09/js-template-compile.html)
```
var temp = '大家好，我是<%name/%>,我今年<%age/%>岁';
var obj = {name: 'eason', age: '24'}
function compile(temp, obj) {
    // 这里填充代码
    let resultStr = temp;
    for (let key in obj) {
        if (obj.hasOwnProperty(key)) {
            let reg = new RegExp('<%' + key + '/%>', 'g');
            resultStr = resultStr.replace(reg, obj[key]);
        }
    }
    return resultStr;
} 

// 返回结果'大家好，我是eason,我今年24岁
```


<html><span id="frame1"></span></html>

#### angular依赖注入的底层实现 [参考链接](http://www.alloyteam.com/2015/09/angularjs-study-of-dependency-injection/)
```
依赖注入简单理解：我自己的东西我自己不想来拿着，想要我依赖的那个人来帮我拿着，当我需要的时候他给我就行了
1.得到模块的依赖项
2.查找依赖项所对应的对象
3.执行时注入
```

<html><span id="frame4"></span></html>

#### vue组件重置数据的方法 [参考链接](https://www.jb51.net/article/148547.htm)
```
1. 重置data数据
Object.assign(this.$data, this.$options.data())
2.通过直接强制刷新 DOM 来达到重置组件的效果，这样可以重置一些组件的动画以及组件内初始的数据
原理：强制重新生成 DOM 可以通过 Vue 中的 key 来实现。在 Vue 更新 Dom 时，如果 key 值相同则会对原有组件进行复用，如果不同，则会重新生成。
3.vue强制刷新组件
把一个组件重置到初始状态是一个常见的需求，推荐的做法有两种，一种是父组件重置子组件的 prop，另一种是子组件暴露一个重置的方法供父组件调用。但有些时候，子组件既没有提供重置的方法，也没提供 prop 来重置自己的状态。更重要的是，这个子组件我们还动不了。于是我们就需要一种 hack 的方式来强制子组件重置到初始状态。方法如下：
v-if 在切换时，元素及它的绑定数据和组件都会被销毁并重建

vue官方文档原文：
如果需要，可以通过将 vm.$data 传入 JSON.parse(JSON.stringify(...)) 得到深拷贝的原始数据对象。
```

<html><span id="frame5"></span></html>

#### vuex和全局变量的本质区别
```
1)缺少时间旅行功能
2）vuex专做态管理，由一个统一的方法去修改数据，全部变量是可以任意修改的
3）做日志搜集，埋点的时候，有vuex更方便
4）全部变量多了会造成命名污染，vuex不会，同时解决了父组件与孙组件，以及兄弟组件之间通信的问题
```

<html><span id="js1"></span></html>

#### 写一个求和函数使得sum(1)(2) sum(1, 2) 两种最后取得结果相同（结果都是3）
```
function sum() {
    var sumResult = 0;
    for (let i of arguments) {
        sumResult += i;
    }       
    function chain() {
        for (let i of arguments) {
            sumResult += i;
        }        
        return chain;        // 返回自身
    }
    chain.valueOf = function() {
        return sumResult;
    }
    return chain;
}

var fun = sum(1)(2)(2, 3);
console.log(fun.valueOf());
```

<html><span id="node1"></span></html>

#### nodejs压测
```
wrk进行压测： https://www.jianshu.com/p/dfe1c12ebd2f
autocanno进行压测：https://juejin.im/post/5b827cbbe51d4538c021f2da
```

<html><span id="node2"></span></html>

#### buffer上限，stream和buffer对比 [参考链接](https://zhuanlan.zhihu.com/p/31355139)
```
注意的是buffer使用的是v8的堆外内存
一般情况下，单个 Node.js 进程是有最大内存限制的
Currently, by default v8 has a memory limit of 512MB on 32-bit systems, and 1.4GB on 64-bit systems.
The limit can be raised by setting –max_old_space_size to a maximum of ~1024 (~1 GB) (32-bit) and ~4096 (~4GB) (64-bit),
but it is recommended that you split your single process into several workers if you are hitting memory limits.
stream和buffer对比
buffer:为数据缓冲对象，是一个类似数组结构的对象，可以通过指定开始写入的位置及写入的数据长度，往其中写入二进制数据
stream:是对buffer对象的高级封装，其操作的底层还是buffer对象，stream可以设置为可读、可写，或者即可读也可写，
在nodejs中继承了EventEmitter接口，可以监听读入、写入的过程。具体实现有文件流，httpresponse等~~
```


<html><span id="node4"></span></html>

#### nodejs日志管理，是否有可视化界面
```
阿里：Pandora  感觉有点KPI产物
腾讯：TSW       代码乱
阿里云sls日志（公司在用的）
ELK（自己搭的）
```

<html><span id="database1"></span></html>

#### redis操作，除了保存sesson token还可以做些啥 [参考链接](https://segmentfault.com/a/1190000016188385)
```
1.缓存
2.排行榜
3.计数器
4.分布式会话
5.分布式锁
6.社交网络
7.最新列表
8.消息系统
```
