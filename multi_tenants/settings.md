# 声明式配置

## `INSTALLED_APPS`、`SHARED_APPS`和`TENANT_APPS`

如果缺少`INSTALLED_APPS`，Django应用无法被正常加载。因此有两种方案：

1. 手动配置三个设置项。

如果采用方案1，维护`INSTALLED_APPS`的同时，需要注意`TENANT_APPS`也需要手动更新，
否则`migrate`不会正常地迁移数据模型到租户schema的表结构，
从而报错数据库操作异常。

2. 修改`settings.py`，加载后用后两个生成前一个，代码如下。

```python
INSTALLED_APPS = list(SHARED_APPS) + [app for app in TENANT_APPS if app not in SHARED_APPS]
```

此方案违反了尽量不使用Python模块做声明式配置的安全原则，不利于后续通过微服务配置中心管理，
因此尽可能避免使用、只作为备选项列举。
