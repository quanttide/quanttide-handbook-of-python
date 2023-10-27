# APIClient类设计

云SDK的核心类，用以在Python语言中与云API通信并处理异常。API设计思路如下：
1. 提供一个`BaseAPIClinet`类，包括传参和实例初始化（`__init__`方法）、密钥传递和身份认证（根据API机制命名，比如`access_token`）、通用API请求接口（`request_api`方法）。
2. 提供一系列子模块`Mixin`类，打包不同的接口。通常同一类接口拥有共同的path，甚至有一些通用的参数配置，可以用一个子Client实现。
3. 运用多重继承组合`APIClient`类。把通用`BaseAPIClient`和所有子模块的`Mixin`组合，即可成为一个通用的`APIClient`；通用`BaseAPIClient`和一个特定`Mixin`组合，即成为一个子模块的子`APIClient`。
