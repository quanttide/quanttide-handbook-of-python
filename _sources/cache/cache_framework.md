# 缓存框架选型

本文总结缓存框架方案的调研结论。

## 标准库`tempfile`

此库的high-level API提供了：

- 默认的临时文件根目录。
- 临时文件夹的生成和销毁。
- 临时文件的生成和销毁。

它的low-level API提供了：

- 手动管理创建和销毁临时文件和文件夹。

因此，在我们的需求下，使用low-level API结合pickle缓存数据不失为一个好办法。

## 社区缓存库`diskcache`等

受到[Django缓存框架](https://docs.djangoproject.com/en/3.2/topics/cache/#setting-up-the-cache)的启发，希望可以有一个类似的方案处理缓存。

Google搜索找到的社区缓存方案有：

- [fcache](https://fcache.readthedocs.io/en/stable/)：不成熟。17年最后更新，最新版本为0.x。
- [diskcache](http://www.grantjenks.com/docs/diskcache/tutorial.html)：成熟。Apache基金会的项目，有Django兼容特性。

因此选择`diskcache`。

### 隔离缓存文件

希望它可以使用系统临时文件目录，帮助我隔离缓存到安全区域。

文档里描述：
> When not specified, a temporary directory is automatically created.

[底层源码](https://github.com/grantjenks/python-diskcache/blob/master/diskcache/core.py#L436) 使用`tempfile`创建临时文件：

```python
directory = tempfile.mkdtemp(prefix='diskcache-')
```

因此`tempfile`具有的使用系统临时文件目录的特性是默认支持的。
