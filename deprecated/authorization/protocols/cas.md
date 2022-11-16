# CAS协议

## Django社区实现

### `django-mama-cas`

**主流**的Django CAS服务端工具箱。

地址：https://github.com/jbittel/django-mama-cas

特性是开箱即用，直接配置URL。详见：https://django-mama-cas.readthedocs.io/en/latest/installation.html#configuring。

没有CAS客户端使用的AuthBackend，原文是
> "MamaCAS does not perform authentication itself, but relies on the active authentication backends"。

### `django-cas-ng`

**最主流的**Django CAS工具箱，支持客户端和服务端。

地址：https://djangocas.dev/docs/latest/index.html

这个库的核心机制是：
- 提供了一个类似于Django官方RemoteBackend的CASBackend，在CAS客户端接入。
- 提供了一些开箱即用的视图函数，在CAS服务端可以直接用，比如可以直接使用的login和logout的视图函数。

服务端特性详见：
- https://djangocas.dev/docs/latest/configuration.html#url-dispatcher
- https://djangocas.dev/docs/latest/view-wrapper.html
- https://djangocas.dev/docs/latest/modules/django_cas_ng.html#module-django_cas_ng.views

使用方法见：
- https://www.linkedin.com/pulse/integrate-django-cas-sso-ui-json-web-token-jwt-razaqa-dhafin-haffiyan/

问题是只兼容到了Django 3.0，不能升级项目到3.1或3.2。

### `djangorestframework-simplejwt-casng`

一个已经不维护的小库，只能做参考。

https://github.com/ChangshengYan/djangorestframework-simplejwt-casng

主要特性是加了一层JWT，实现了上述文章提到的使用JWT作为Token的方法。
