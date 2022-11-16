# 文件模板

这里提供一些常用的Django文件模板，建议加入到[PyCharm的文件模板](https://www.jetbrains.com/help/pycharm/using-file-and-code-templates.html)以方便使用。

## 模型层

```python
import uuid

from django.db import models


class MyModel(models.Model):
    id = models.UUIDField(primary_key=True, editable=False, default=uuid.uuid4, verbose_name='ID')

```

## 序列化层

```python
from rest_framework import serializers

from .models import MyModel


class MyModelSerializer(serializers.ModelSerializer):
    class Meta:
        model = MyModel
        fields = '__all__'

```

## 单元测试

```python 
from django.test import TestCase


class MyTestCase(TestCase):
    def test_something(self):
        self.assertTrue(False)

```