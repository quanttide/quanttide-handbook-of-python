# 配置文件

使用`pyproject.toml`。

主要原因：

- 有统一的、更现代化的标准。（TODO：具体PEP规范）
- 集中在一个配置文件，方便统一维护。

## `[project]`

### `version`选项

遵循语义化版本，从`0.1.0-alpha.1`开始计数。

### `classifiers`选项

示例：

```toml
classifiers = [
    "Programming Language :: Python :: 3",
    "Framework :: Django",
    "License :: OSI Approved :: BSD License",
    "Development Status :: 3 - Alpha",
]
```

说明：

- 编程语言选Python 3。
- 如果是Django项目，框架选Django。
- 证书填使用的。
- 开发状态默认从阶段3(Alpha)开始，即在内部有使用案例的Alpha阶段。

## `[tool.setuptools]`

规范详见[setuptools文档](https://setuptools.pypa.io/en/latest/userguide/pyproject_config.html)。

```toml
packages = ["<your_package_dir>"]
```

注意配置此项，避免`tests`和`exmaple`等文件夹被错误打包。
