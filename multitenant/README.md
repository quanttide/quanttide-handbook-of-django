# 多租户隔离

## 使用场景

专门用于PaaS/SaaS服务。

## 方案

### 数据库隔离

三种方案隔离租户数据：

- 数据库隔离。
- schema隔离。PG原生支持；MySQL的schema等于表，需要框架层面自己支持。
- 租户ID标记。

由于我们的云开发以服务为单位进行隔离，因此schema隔离最适合服务内隔离多租户。但由于我们使用MySQL，而MySQL原生不支持，因此需要框架层面支持或者自己定制，或者考虑把这类服务的数据库替换成PG。

### API访问

对外不同的组织不同的子域名访问同样的服务。

## 参考资料

Django包：

- [Welcome to django-tenant-schemas documentation! &mdash; django-tenant-schema dev documentation](https://django-tenant-schemas.readthedocs.io/en/latest/)
- [Welcome to django-tenants documentation! &mdash; django_tenants dev documentation](https://django-tenants.readthedocs.io/en/latest/)
- [GitHub - citusdata/django-multitenant: Python/Django support for distributed multi-tenant databases like Postgres+Citus](https://github.com/citusdata/django-multitenant)
- [Django Packages : Multi-tenanc](https://djangopackages.org/grids/g/multi-tenancy/)
- [GitHub - mik3y/django-db-multitenant: A simple multi-tenancy solution for Django apps](https://github.com/mik3y/django-db-multitenant)

社区实践：

- [实现saas多租户方案比较 - kkyong - 博客园](https://www.cnblogs.com/codemind/p/13081336.html)
