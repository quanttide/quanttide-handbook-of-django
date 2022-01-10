# Django Settings

## django-configuations

https://django-configurations.readthedocs.io/en/latest/patterns.html

通过为不同环境提供不同类、并且继承共同的模板的方式进行建模，
可以有效解决目前的业务系统里为调试和生产使用不同模式的问题。

并且还可以规范指定环境的语义，不必再通过人为规定标签的方式进行。

如果想对`settings.py`进行改造，是一个不错的备选。
不过改造的时候注意先在新应用上积累经验，然后再改造现有应用。
