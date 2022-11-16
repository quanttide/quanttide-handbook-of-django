# 用户权限类设计

内部应用的权限控制需要细粒度更高的方案，DRF的Permission类一般对API控制，也可能需要考虑Django原生的用户级Permission控制（https://docs.djangoproject.com/en/3.1/topics/auth/），或者DRF的Object-level权限控制方案（https://www.django-rest-framework.org/api-guide/permissions/#djangoobjectpermissions）。
