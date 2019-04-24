---
layout:     post
title:      golang--类型转换
category: blog
description: 类型转换
---

### 字符串转整型
```
// 将字符串转换为int
strconv.ParseInt(str, base, bitSize)
//str: 要转换的字符
//base: 进位制(2进制 - 32进制）
//bitSize: 指定整数类型（0：int, 8:int8,16:int16, 32:int32,  64:int64)
```


```
strconv.ParseUint(str, base, bitSize)

strconv.Atio(str)
```

### 整型转字符串

```
FormatInt // int 型整形 i 转换为字符串形式
strconv.FormatInt(i, base)
strconv.FormatUint(i, base)
// base 进位制

Itoa 相当于 FormatInt(i, 10)

```


