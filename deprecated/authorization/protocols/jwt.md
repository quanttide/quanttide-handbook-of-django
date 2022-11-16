# JWT协议

JWT协议只是Token协议而**不是完整的鉴权协议**。这里指的是基于JWT协议实现的鉴权库。

## Django社区实现

### `djangorestframework-jwt`

**主流库**。

地址：https://jpadilla.github.io/django-rest-framework-jwt/

此库已经不维护（https://github.com/jpadilla/django-rest-framework-jwt/issues/484）。官方建议使用：
- 原作者的新库：https://github.com/davesque/django-rest-framework-simplejwt
- 原项目的fork：https://github.com/Styria-Digital/django-rest-framework-jwt

### `django-rest-auth`

可以理解为上面库的拓展，相比于上面的库提供的服务端API更丰富完善。

地址：https://djoser.readthedocs.io/en/latest/index.html



