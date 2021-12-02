# 模拟环境变量

使用`unittest`的装饰器`mock.patch.dict(os.environ, {'<key>': 'value'})`。

方案来自：

- https://adamj.eu/tech/2020/10/13/how-to-mock-environment-variables-with-pythons-unittest/

在此基础上注意：

类级别的装饰器，会在`setUp`方法之后运行。如果`setUp`方法内运行的代码先使用了环境变量，则类装饰器这样写实际上无效。这种情况下需要把装饰器加在`setUp`方法上。例如[`qtclass-admin-cli`的测试`test_tutorial_parsers_course.py`](https://quanttide.coding.net/p/qtclass-app/d/qtclass-admin-cli/git/tree/master/tests/test_tutorial_parsers_course.py)的15行。(PS: 尚未阅读源码或者API文档确认是否如此，请读者谨慎验证，如有问题欢迎PR。)
