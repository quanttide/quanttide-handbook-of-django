# 地理位置字段

总体来说还需要进一步广泛调研，看业界用的方案是怎么样的，Django现有的方案看起来还不够解决商业级的问题。

现有第三方库：

-  django-location-field（https://django-location-field.readthedocs.io/en/latest/ ），不需要精确定位的功能、需要接地图API比较麻烦。
-  django-cities（https://pypi.org/project/django-cities/） ，看起来比较完善，不过依赖文件比较大，不确定对中国本土化的支持如何。
- china-cities（ https://github.com/boeboe/china-cities） ，不可以直接用、数据源是维基百科不一定完全靠谱。

备选方案：

- django-cities。
- 自定义：国家、省、城市（、区），需要自己做和存城市列表且可能比较麻烦。
