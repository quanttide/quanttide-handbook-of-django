# 日期和时间字段

## `created_at`

创建时间/日期。`DateTimeField`或者是`DateField`。

示例：

```python
created_at = models.DateTimeField(auto_now_add=True, verbose_name='<模型>创建时间')
```

## `updated_at`

（最近）修改时间/日期。类型同`created_at`字段。

示例：

```python
updated_at = models.DateTimeField(auto_now=True, verbose_name='<模型>修改时间')
```
