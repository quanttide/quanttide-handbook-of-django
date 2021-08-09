# OAuth2协议

## 标准协议

https://datatracker.ietf.org/doc/html/rfc6749

## Python社区实现

- oauthlib: https://oauthlib.readthedocs.io/en/latest/index.html。
- authlib: https://docs.authlib.org/en/latest/index.html。

## Django社区实现

官方提供的项目列表：https://djangopackages.org/grids/g/oauth/

### `django-oauth-toolkit`

**主流库**。

https://django-oauth-toolkit.readthedocs.io/en/latest/index.html

核心特性是：

- 支持OAuth1、OAuth2、OpenID Connect。
- 提供了开箱即用的搭建鉴权服务端的工具。
- 为OAuth2鉴权客户端（即资源服务器）提供了可自定义的中间件Middleware、AuthBackend。
- 支持DRF，拓展了DRF的Permission。

优点是：
- 特性更全面。

缺点是：
- 侵入性更强、不适合拓展。
- 没有对DRF的原生支持。

#### `django-rest-framework-oauth`

地址：https://jpadilla.github.io/django-rest-framework-oauth/

主要特性是：
- 实现了一个自定义的DRF的Authentication类。
- 拓展了一个DRF的Permission类。

优点是：
- 更轻量级。

缺点是：
- 特性比较少。