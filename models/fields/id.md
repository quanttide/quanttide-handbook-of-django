# ID字段

## UUID字段`id`

使用UUID而不是默认的自增主键，以确保在分布式的微服务系统内唯一。

使用uuid4算法，主要考虑到其代码效率比较好，冲突概率也低到忽略不计。

```python
id = models.UUIDField(primary_key=True, editable=False, default=uuid.uuid4, verbose_name='ID')
```

`verbose_name`描述为`<资源名称>ID`，比如`课程ID`。

## 租户内唯一标识字段`name`

建议命名为`name`，参考腾讯云的租户内唯一标识命名。

此字段在租户内唯一，是租户定义的唯一标识。
使用开发者自己清晰定义的标识，对于简化分布式系统的业务逻辑具有重要意义。

此字段常用在URL路径或参数代替ID，用以查询对应业务资源。比如`/courses/data-analytics-with-python`为数据分析课程资源的API。

此字段的Django定义为：

```python
name = models.CharField(max_length=128, unique=True, verbose_name='名称')
```

`verbose_name`描述为`<资源名称>名称`，比如`课程名称`。

64个字符略显拥挤。比如，腾讯云对象存储限制60个字符，再加上APPID写入存储桶名，就显得空间不够。
