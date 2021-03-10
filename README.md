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
  * 相关第三方解决方案。网易易盾，GEETEST等

* Login by third-party
  * strategy. 可以使用登录和登录+绑定等多种策略，参见 http://www.woshipm.com/pd/437357.html
  * 提供方. 国内: github, 微信，QQ， 国外： facebook, google
  * 技术实现. 多使用Oauth2.0技术，用户确认授权，由认证服务器返回授权码等其它参数。参见： http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html 。
    * QQ第三方登录. 一个具体的例子，需要网站在QQ平台备案，然后使用Oauth2.0技术。 参见： https://zhuanlan.zhihu.com/p/35651406

* Single sign-on 对于复杂平台网站会用到单点登录，即一次登录，可访问多个子系统。如阿里系，登录淘宝后，可访问支付宝，飞猪旅行等。 原理主要是单独抽出一个认证中心来统一登录管理，可参考： https://www.zhihu.com/question/22992471/answer/65164090 ， 文中也提及到了手机APP, 登录判断，登出等实际问题。

### Microservice
