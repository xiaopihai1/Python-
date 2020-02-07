## OS操作系统模块

1. 获取操作系统名称

```python
import os
os.name  # 导入的依赖特定操作系统的模块的名称, 在框架设计中可用于判断用户依赖的操作系统,目前已注册: 'posix', 'nt', 'java'.

```

2. 字符串环境的mapping 对象 

```python
OS.environ
# 获取第一次导入os模块时的环境mapping对象, 后续对环境的更改不会映射到os.environ上 除非直接对os.environ进行修改
# 在某些平台上，包括 FreeBSD 和 Mac OS X，设置 environ 可能导致内存泄露

```

3. 获取环境变量的值

```python
os.getenv(key, default=None)
# 如果存在，返回环境变量 key 的值，否则返回 default。key ，default 和返回值均为 str 字符串类型。
```

