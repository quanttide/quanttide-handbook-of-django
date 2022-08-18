# `CharField`字段

## 常用字段命名

- `verbose_name`: `name`被唯一标识占用，因此使用此字段来表示**用户可读的名称**。

或者使用一组描述代替：

- `title`: 标题。直接代替`verbose_name`。
- `description`: 详情。通常是一句话或者一段话，也可以是`TextField`，根据具体业务需求定义。

## 常用选项

如果希望可为空，则填`null=True, blank=True, default=None,`这组变量。
