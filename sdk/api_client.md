# APIClient类设计

封装Python SDK提供的APIClient类，方便在Django项目中使用。主要自定义过程包括：
- 在`settings`模块设置APIClient初始化需要的参数。
- 在`api`模块为`APIClient`提供以上默认参数，并提供一个`api_client`单例方便开发者直接使用。