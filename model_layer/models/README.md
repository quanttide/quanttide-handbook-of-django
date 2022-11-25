# 模型类

示例：

```python
import uuid

from django.db import models


class MyModel(models.Model):
    id = models.UUIDField(primary_key=True, editable=False, default=uuid.uuid4, verbose_name='ID')

```

## 导入

当Django应用中的models是packages时，导入到`models.__init__`模块的类才会被`makemigrations`识别。因此：

- 可以用这个特性当模型类的特性开关。
- 如果发现没有被正确地生成数据库迁移时，检查`__init__`模块。
