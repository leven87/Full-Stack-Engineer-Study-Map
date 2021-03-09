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
  
  
