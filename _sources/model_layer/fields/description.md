# 名称和描述字段

- `verbose_name`: 名称。 `name`被唯一标识占用，因此使用此字段来表示**用户可读的名称**。

或者使用一组描述代替：

- `title`: 标题。一般是代替`verbose_name`。
- `description`: 详情。通常是一句话或者一段话，也可以是`TextField`，根据具体业务需求定义。

如果需要同时提供短名称和长名称，也可以同时提供`verbose_name`和`title`字段。
