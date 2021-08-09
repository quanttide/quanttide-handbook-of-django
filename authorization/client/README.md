# 鉴权客户端

[//]: （2021-08-09）从项目里复制，还未维护。

`django-qtauth`计划升级成`drf-remote-auth`项目，作为通用的微服务鉴权客户端插件，计划支持的特性包括：
- 支持SSO单点登录。
- 支持CAS集中式鉴权。
- 支持OpenID Connect鉴权协议。
- 支持JWT作为鉴权Token。

对于本项目的开发者用户，希望支持：
- 可以不需要深入理解认证服务搭建方式、用户鉴权协议、Token签名方式，**用户可以根据直观理解接入**，从而降低此复杂业务需求的接入难度。 
- 只需要根据使用场景（即输入值是服务端签发Token或者SecretKey）即可使用，内部根据输入值方式和声明式配置处理具体逻辑（直接发送或者签名后发送）。
- 基于DRF的机制，灵活地配置Authentication类指定服务允许的认证方式。
- 基于云原生的12-factors标准，灵活地配置认证服务API，安全便捷地在不同环境中使用不同API。

此库需要整合来自社区的大量在维护和过时的库。 
考虑到这些库的API不统一、功能可能重合或者冲突，还有很多库过时不好维护，且设计出发点和我们不一样，零零散散的库对用户接入也十分不方便，
在思考很久以后放弃了补充少量插件的计划，而用这个库来打包社区现有方案、提供一个相对完整的支持以上特性的微服务远程鉴权解决方案。

**目前的设计思路还很不清晰，分层设计思路、DRF框架特点、社区已有实现之间的关系不明，服务端的API及交互过程也还没有稳定。**

## 核心机制设计

### 分层设计

1. CAS客户端：主要任务是转发鉴权令牌到负责代理鉴权的CAS服务端。
2. OpenID Connect客户端：用户鉴权协议。
3. JWT：鉴权中使用到的Token协议。

### Authentication

基于DRF原生机制，只修改DRF的Authentication类，尽量不修改AuthBackend和AuthMiddleware。

由于DRF支持多个Authentication并列使用（只要一个通过即可），因此这里计划根据输入实现不同的Authentication类用于CAS客户端配置：
- `RemoteTokenAuthentication`: 输入值为远端服务器签发的Token，只负责转发到远端服务器和接收验证结果。不需要关心具体协议。
- `SecretKeyAuthentication`: 输入值为`secret_id`和`secret_key`，在Authentication类中计算签名以后签发。需要知道签名规则，但可以免去登录步骤。

settings需要允许Authentication类的远端认证服务API。可以考虑既允许它们使用同一个API，也可以分别设置不同的API。

