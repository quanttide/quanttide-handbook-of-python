# 文件模板

## `pyproject.toml`

```toml
[build-system]
requires = ["setuptools>=61", "setuptools.scm"]
build-backend = "setuptools.build_meta"

[project]
# name it as your package name
name = "<your-package-name>"
# semetric versions
version = "0.1.0-alpha.1"
# describe the package within one sentence
description = "<your-package-description>"
authors = [{name = "QuantTide Inc.", email = "opensource@quanttide.com"}]
license = {text = "<your-license>"}
classifiers = [
    "Programming Language :: Python :: 3",
]
requires-python = '>=3'
dependencies = [
]

[project.readme]
file = "README.md"
content-type = "text/markdown"

[tool.setuptools]
packages = ["<your_package_dir>"]
```