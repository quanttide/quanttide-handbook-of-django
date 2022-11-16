# DRF框架

### 官方支持

自定义DRF的`Authentication`类，详见：https://www.django-rest-framework.org/api-guide/authentication/。

地位等同于Django的`AuthBackend`类，详见：https://docs.djangoproject.com/en/3.1/topics/auth/customizing/。


## 社区实现

不是基于标准协议实现，而是基于DRF的框架规定实现。

### `django-rest-framework-passwordless`

地址：https://github.com/aaronn/django-rest-framework-passwordless

提供验证码登录的特性。


### `knox`

地址：https://github.com/James1345/django-rest-knox

支持一个用户在不同设备使用不同Token鉴权。


### `durin`

地址：https://django-rest-durin.readthedocs.io/en/latest/index.html 

拓展DRF的Auth框架，提供了更丰富的服务端API和专用Authentication等客户端工具。