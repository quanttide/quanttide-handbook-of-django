# SSO单点登录

单点登录指在多个系统中，用户只需一次登录，各个系统即可感知该用户已经登录。

完整介绍详见：https://juejin.cn/post/6844903845424971783。

注意，SSO是一种**特性**而不是一种**协议**。

## Django社区实现

### `django-rest-framework-sso`

地址：https://github.com/namespace-ee/django-rest-framework-sso。

特性：
- 这个库为微服务SSO设计，使用JWT作为Token。
  
备注：
- StackOverflow的一个讨论提到了这个库和CAS的库：https://stackoverflow.com/questions/47591102/making-sso-with-django-rest-framework。
