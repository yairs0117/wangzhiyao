--- 
layout:     post 
title:      golang--数据类型--Pointer  
category: blog 
description: Pointer
---

1.  定义指针变量
2.  指针变量赋值
3.  访问指针变量中指向地址的值

```
package main
import "fmt"
func main(){
    var a int = 20
    var ip *int
    ip = &a
    fmt.Printf("%x", &a)
    fmt.Printf("%x", ip)
    fmt.Printf("%d", *ip)
}

```

### GO空指针
当一个指针被定义后没有分配到任何变量，它的值为nil。
nil指针也成为空指针
nil在概念上和其他语言的null，None，nil，Null一样，都指代零值和空值

### Go语言指针数组

```
package main
import "fmt"

const MAX int = 3

func main(){
    a := []int{10,100,200}
    var i int
    var ptr [MAX]*int

    for i=0; i<MAX; i++{
        ptr[i] = &a[i]
    }
    for i=0; i < MAX; i++{
        fmt.Printf("a[%d]=%d\n", i, *ptr[i])
    }
}


```

### 指向指针的指针

```
package main
import "fmt"

func main(){
    var a int
    var ptr *int
    var pptr **int

    a = 3000
    // 指向a地址
    ptr = &a
    //指向 指针ptr地址
    pptr = &ptr
    fmt.Printf("a=%d", a)
    fmt.Printf("*ptr=%d", *ptr)
    fmt.Printf("**ptr=%d", **pptr)
}
```



### 指针作为函数参数

```
package main
import "fmt"
func swap(x *int, y *int){
    var temp int
    temp = *x
    *x = *y
    *y = temp
}
func main(){
    var a int
    a = 100
    var b int = 200

    swap(&a, &b)
}
```




