# Full-Stack-Engineer-Study-Map
The purpose of this repository is to summarize the knowledge points that full-stack engineers will encounter. This is mainly used to help me find a job.

---
### Login
* Bot Detection （没有绝对的安全，难度如巅峰的google的reCAPTCHA，也能被破解）
  * 简单图形验证码 
    * 常用的图形验证码很简单，通过session即可实现。
    * 复杂的可以用到客户端的一些加密技术，flash等，参看 [https://www.zhihu.com/question/40564744/answer/87279667](https://www.zhihu.com/question/40564744/answer/87279667)
    
  * 点击，滑动验证 本质是收集web客户端的各种信息，通过JS混淆，加密发送到服务端。https://www.zhihu.com/question/35538123/answer/221045391
  * 短信，邮箱验证  绑定手机，发送短信，短信接口实现
  * 相关第三方解决方案。网易易盾，GEETEST等（适合小公司）

* Login by third-party
  * strategy. 可以使用登录和登录+绑定等多种策略，参见 http://www.woshipm.com/pd/437357.html
  * 提供方. 国内: github, 微信，QQ， 国外： facebook, google
  * 技术实现. 多使用Oauth2.0技术，用户确认授权，由认证服务器返回授权码等其它参数。参见： http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html 。
    * QQ第三方登录. 一个具体的例子，需要网站在QQ平台备案，然后使用Oauth2.0技术。 参见： https://zhuanlan.zhihu.com/p/35651406

* Single sign-on 对于复杂平台网站会用到单点登录，即一次登录，可访问多个子系统。如阿里系，登录淘宝后，可访问支付宝，飞猪旅行等。 原理主要是单独抽出一个认证中心来统一登录管理，可参考： https://www.zhihu.com/question/22992471/answer/65164090 ， 文中也提及到了手机APP, 登录判断，登出等实际问题。

### Microservice
* RPC VS HTTP. rpc即远端过程调用。为什么有了http还用rpc呢？ 其实http和rpc都有很长的发展历史，http最后成了互联网客户端请求通用的标准，但是rpc却也一直大型分布式调用中使用。rpc会比http更加灵活的自定义tcp报头，从而提升性能。但现阶段，在微服务内，两种协议都有使用，而且http2也会极大提升性能。参看： https://www.zhihu.com/question/41609070
* 完整架构. 可以参考： https://www.infoq.cn/article/micro-service-technology-stack , 里面讲的非常全面，主要是基于java技术栈的架构，java也是最适合微服务的技术栈，配套设施非常齐全。但这样的架构只适合大公司，小公司没有这么多的服务和流量，也没有足够的工程师去维护完整的微服务架构。
* 小公司架构. 我从不同的角度去描述一套小公司可行的类微服务架构。
  * CI/CD. 
    * 代码编写. python, php, java, node.js, .net 等。在开发机或者本机。
    * 测试. phpunit, jest等测试框架或工具。
    * 语法检查. ESLINT(javascript, node.js), PEP8(python)等
    * 版本控制. GIT
    * 集成管理. Jenkins + Kubernetes + docker. Jenkins is a continuous integration server, support building and testing virtually any project. Kubernetes: Manage a cluster of Linux containers as a single system to accelerate Dev and simplify Ops. 具体实践参见： https://blog.csdn.net/liuchunming033/article/details/105455050 
    * 上线. 

  * 服务发现. 我觉得还没有必要，对于小型网站，只有几台服务器，直接写在配置文件中即可。
  * 负载均衡，服务网关. 不用考虑太复杂，甚至直接用nginx即可，也可加上Kong. 参见： https://www.jianshu.com/p/b65259021d2b 
  * 云服务. 可接入亚马逊云，阿里云等。
  * 服务监控. 这块不太熟，小公司可以先实现日志监控，发现请求异常，负载高等问题，利用elasticsearch. 也需检测服务器的负载，内存等情况，及时报警，可使用Sensu. 
  * 服务容错. 这块暂不考虑自动化。这块主要还是通过报警，更改容器或服务器。
  * 后台服务.
    * 消息系统.
    * 缓存. 
    * 分布式数据访问. 分库分表，也可以有很多中间件。参看： https://blog.csdn.net/xcbeyond/article/details/54976983
  * 服务安全.  OAuth 2.0, Jwt. 

### 微信小程序
  *  目前有不少微信小程序的开发框架，可以将基于vue或者react的代码转化成wechat mini program. 详见： https://www.infoq.cn/article/87798qerszjekxhdu1ym
  *  Taro. 基于react, 社区发展良好。
   
### 前端框架
#### React
  * 工具链. 前端工具来进行复杂前端工程管理，提高易用性，可维护性和兼容性。   
    * npm + package.json 包管理工具
    * webpack（前端资源加载和打包工具），可以处理CSS,图片等
    * babel(编译器)，能将较新标准的JS代码(ES^)转换成较旧标准的代码(ES5),从而在兼容更多的浏览器。
  * 工具链实现方案. 参见： https://zh-hans.reactjs.org/docs/create-a-new-react-app.html   
    * create-react-app. 创建前端流水线，内置 Babel 和 webpack。 你无需了解任何细节，适合学习和创建单页应用。
    * 灵活的工具链. Neutrino, Nx等.
    * 从头打造. 参见： https://zh-hans.reactjs.org/docs/optimizing-performance.html#use-the-production-build
    * 无需工具链. 直接添加到<script>标签，开箱即用。 

### python后端框架
#### uWSGI + twisted 
  * 这是我在搜狗工作的时候，QQ输入法的后端架构。 
    * uWSGI是一个Web服务器，它实现了WSGI协议、uwsgi、http等协议。 参看：https://zhuanlan.zhihu.com/p/36448645  这里它往前端与nginx等代理服务器通信，获取用户请求。 往后端与twisted通信，处理用户请求。它本身又结合了mako网页模板，完成了现在前端框架（如：react,angular）等的工作。现在，人们通常使用react,vue等作为前端框架，同样，他们可以设置与Flask进行通讯。
    * 如果要部署生产环境，需要结合nginx,docker等。 
    * twisted
#### Flask
  * 如之前所写，现在都会用到Flask + 现代前端框架(vue, react等)
