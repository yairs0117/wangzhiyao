---
layout:post
title: python--装饰器
category: blog
decription: python 装饰器
---

1. 作为一个函数

```
def mydecorator(func):
    def wrapped(*args, **kwargs):
        result = func(*args, **kwargs)
        return result
    return wrapped
```

2. 作为一个类

```
class DecoratorAsClass:
    def __init__(self, func):
        self.func = func

    def __call__(self, *args, **kwargs):
        result = self.func(*args, **kwargs)
        return result
```

3. 参数化装饰器 

```
def repeat(number=3):
    def actual_decorator(func):
        def wrapper(*args, **kwargs):
            result = None
            for _ in range(number):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return actual_decorator

@repeat(3)
def foo():
    print("foo")
```

4. 保存内省的装饰器

```
from functools import wraps
def preserving_decorator(function):
    @wraps(function)
    def wrapped(*args, **kwargs):
        return function(*args, **kwargs)
    return wrapped
```


#### 用法

1. 参数检查


2. 缓存

3. 代理

4. 上下文提供者

















