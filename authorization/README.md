# 微服务用户鉴权

- SSO，用户登录一次无需重复鉴权。
- CAS，以集中在一个服务中鉴权的方式实现，是一个代理服务。
- Kerberos：一种网络鉴权协议（不区分用户和服务）。原文为：provide strong authentication for client/server applications by using secret-key cryptography。
- OAuth2：一种网络鉴权协议，适合用户。enables a third-party
   application to obtain limited access to an HTTP service, either on
   behalf of a resource owner by orchestrating an approval interaction
   between the resource owner and the HTTP service, or by allowing the
   third-party application to obtain access on its own behalf.
- OpenID：类似于OAuth2的效果。
- JWT：一种签名。可以用在OAuth2或者Kerberos。