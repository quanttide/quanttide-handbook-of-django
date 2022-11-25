# 序列化类

示例：

```python
from rest_framework import serializers

from .models import MyModel


class MyModelSerializer(serializers.ModelSerializer):
    class Meta:
        model = MyModel
        fields = '__all__'

```
