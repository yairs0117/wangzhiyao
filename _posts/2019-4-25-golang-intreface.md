---
layout:		post
title:      golang--interface
category: blog
description: interface
---

### interface

1. 不能有字段
2. 不能定义自己的方法
3. 只能声明方法
4. 可嵌入其他接口类型

接口通常以er作为名称后缀，方法名是声明组成部分，但参数名可不同或省略

```
type tester interface {
	test()
	string() string
}

type data struct{}

func (*data)test()
func (data) string() string{}


func main(){
	var d data
	var t tester = &d
	t.test()
	println(t.string())
}
```

```
type stringer interface {
	string()	string
}

type tester interface {
	stringer
	test()
}

type data struct {
	
}

func (*data) test()

func (data)




```

