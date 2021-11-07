# 有向无环图

总体来说，对于DAG的技术原理、使用场景、实现源码等方面还需要透彻了解以后才能决定方案。

用途：

- 课堂APP中表达课程和课程、课时和课时之间的前后依赖关系。
- 数据服务APP中表达项目内事项和事项的前后依赖关系。

现有第三方库：

- django-dag（https://github.com/elpaso/django-dag），只提供了两个方便使用的抽象类；
- django-postgresql-dag（https://github.com/OmenApps/django-postgresql-dag），功能相对完善、文档需要理解DAG才能懂，只兼容PostgreSQL，对MySQL的兼容性为止。
- django-dag-postgresql（https://github.com/worsht/django-dag-postgresql），只有一个model模块，没有文档、不清楚具体有哪些特性。
- django-treebeard-dag（https://pypi.org/project/django-treebeard-dag/），也是只有一个model模块，github链接还丢失了，不清楚具体特性。

现有方案：

- 一篇基于PostgreSQL的DAG原理介绍文章（ https://www.fusionbox.com/blog/detail/graph-algorithms-in-a-database-recursive-ctes-and-topological-sort-with-postgres/620/）

初步预估效果：

- 需要实现Edge（边）和Node（点）的Factory，具体是咋搞也不清楚、也不清楚需要多少Django底层原理。

备选方案：

- 基于django-postgresql-dag改一个MySQL版本。
- 参考这几个库从头开始定制，如果改MySQL版本不太可能。