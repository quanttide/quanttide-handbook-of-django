# 多租户隔离

## 使用场景

专门用于PaaS/SaaS服务。

## 隔离思路

### 租户数据

三种方案隔离租户数据：

- 数据库隔离。
- schema隔离。PostgreSQL原生支持；MySQL的schema等于表，需要框架层面自己支持。
- 租户ID标记。

由于我们以数据库单位隔离微服务，因此schema隔离最适合服务内隔离多租户。
由于MySQL原生不支持且定制困难，因此后台数据库需要更换成PostgreSQL。

### 租户API

有两种方案：

- 通过子域名（subdomain）访问。
- 通过子路径（subfolder）访问。

## 方案

框架使用[django-tenants](https://django-tenants.readthedocs.io/en/latest/)库。

数据库使用PostgreSQL。

## 参考资料

- [Welcome to django-tenants documentation! &mdash; django_tenants dev documentation](https://django-tenants.readthedocs.io/en/latest/)
- [Django Packages : Multi-tenacy](https://djangopackages.org/grids/g/multi-tenancy/)
