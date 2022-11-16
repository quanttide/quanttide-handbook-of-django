# 鉴权协议

推荐使用OAuth2和OpenID Connect作为鉴权协议。

弃用其他协议的原因是：
- CAS: 比较适合无AJAX的模板型Web网页应用，对于客户端显得太笨重。
- Kerberos: Python社区没有轮子，且功能可以用OpenID Connect代替。