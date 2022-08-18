# 关联表

常用格式：

```python
<related_model> = models.ForeignKey(<Model>, related_name='<children>', on_delete=models.CASCADE, verbose_name='<关联模型名称>')
```

`ForeignKey`可以根据需要换成`OneToOneField`或`ManyToManyField`。
