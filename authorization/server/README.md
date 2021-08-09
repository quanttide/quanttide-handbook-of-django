# 服务端

[//]: （2021-08-09）从项目里复制，还未维护。

本服务的目标是对外暴露一系列用户鉴权（Authorization）和用户信息（Profile）的API，用以为量潮应用系统的其他服务提供：
- 基于集中式认证服务协议（Central Authentication Service, CAS）的单点登录（Single Sign On, SSO）服务。
- 互相关联的用户身份（users）、用户信息（profiles）、密钥（secretkey）、员工身份（staff）、团队身份（teams）、协作者身份（collaborators）、会员身份（vip）等。

CAS客户端和用户信息组件库等本服务的消费者部分参考：
- 基于CAS的SSO架构：Django公共依赖 > django-practices-docs > authorization
- 基于JWT的CAS客户端的DRF插件：Django公共依赖 > drf-cas-jwt
- Flutter用户组件库：Flutter公共依赖 > 
- 微信小程序用户组件库：微信小程序公共依赖 > 

## 应用架构

基于领域驱动设计（Domain-Driven Design, DDD）的思想，我们把本服务内的Django应用从顶层至底层分为两层：
- 应用层，基于不同的鉴权协议划分，目前是OpenID Connect。
- 领域层，以业务逻辑需求划分为用户（users）、用户信息（profiles）、密钥（secretkey）、员工（staff）、团队（teams）、协作者（collaborators）、会员（vip）等身份。

应用层对外暴露API，需要调用本应用和其他数据模型应用的Django类。其中：
- 鉴权应用需要调用几乎所有数据模型层的数据，从而为外界提供统一的鉴权API。
- 用户信息应用需要调用本应用的基本用户信息，以及除了用户应用（users）以外的各个应用内的补充信息。

领域层分领域建模，每个应用划分了自建身份和第三方身份为不同的模块，通过建立他们的关联关系来匹配同一个用户的不同账号。
比如，在用户应用（users），自建用户（user）和微信用户（wechatuser）被划分为不同的模块，微信用户通过外键关联自建用户来匹配。
关联关系是业务逻辑的目标，独立的模块是为了方便独立迭代的工程管理。


## 应用层

### OpenID Connect Provider

计划对外暴露以下API：
- 登录：login和logout。
- 鉴权（auth）：verify和refresh接口。
- 用户信息（profile）：根据OpenID的userinfo标准。
- 辅助API：比如vcode等。

## 领域层

### 密钥应用`secretkey`

此应用的核心是提供一个SecretKey数据模型，核心字段包括：
- secret_id: SecretID字段
- secret_key: SecretKey字段
- is_active: 是否激活，此时`is_authenticated=True`，`is_anonymous=False`。
- is_staff: 是否拥有员工权限。
- is_admin: 是否拥有系统管理员权限（谨慎分配）。

关联字段包括：
- user: 关联User模型，计划在上线PaaS和SaaS服务需要提供API访问时支持。
- staff: 关联Staff模型，计划在给内部开发者分配权限时支持。
- team: 关联Team模型，计划在上线PaaS和Saas服务时提供团队级别权限支持。

考虑到系统初始化时无可用SecretKey，计划定制初始值为`secret_id='qtuser-admin'`和`secret_key={DJANGO_SECRET_KEY}`。
此机制将用以代替Django默认的Admin框架的create_superuser特性，提供在微服务系统里集中式鉴权的特性，为其他服务（比如CI命令行工具）签发SecretKey用以访问系统内服务提供便利。

计划支持的生成SecretKey的方式包括：
- 初始SecretKey签发，此时生成的SecretKey默认拥有系统管理员权限，也可以自定义签发权限水平（比如`is_staff=True`）。
- 用户或者团队申请，此时生成的SecretKey不超过此用户或者团队自己的权限集。
- 如果在PaaS和SaaS服务中需要支持项目级别的密钥账户，再联调具体的项目管理服务进行拓展。

**预期签发密钥的API可能在授权时遇到user或team权限集变动的问题。**
比如，原本用户拥有某个分级管理员权限，后来被关闭了，此时用户自己的授权集变小，但密钥的授权集不变。

此处可以有的解决办法：
- （required）在权限判断时显示约束用户和团队边界。
- 在更新权限时同时更新所有关联密钥，并且安排定时检查。
- 在下次用户改变授权时检查并且自动修复，或者提示用户此问题让用户重新授权。


## 备注

### 云计算框架的鉴权

云开发的框架里有一套鉴权系统，由于实现的水平一般且不好拓展，所以没有接入。
而实际上云开发或者弹性微服务有可能支持标准化的鉴权框架，让用户可以自定义地拓展鉴权方式，但目前来看他们没有这么高的设计水平。
因此我们暂时使用我们在DRF框架内的统一鉴权方案，即放在自建的服务内并通过端到端的方式设计。
