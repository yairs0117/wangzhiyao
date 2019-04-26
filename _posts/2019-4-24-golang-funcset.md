---
layout:     post
title:      golang--方法集
category: blog
description: 方法集
---

```

package main

import (
	"reflect"
	"fmt"
)

type S struct {

}

type T struct {
	S
}

func (S) sVal(){
	fmt.Println("sVal")
}

func (*S) sPtr() {
	fmt.Println("sPtr")
}

func (T) tVal(){
	fmt.Println("tVal")
}

func(*T)tPtr(){
	fmt.Println("tPtr")
}

func MethodSet(a interface{}){
	t := reflect.TypeOf(a)
	fmt.Println(t.NumMethod())
	for i,n := 0, t.NumMethod(); i < n; i++{
		m := t.Method(i)
		fmt.Println(m.Name, m.Type)
	}

}

func main(){
	var t T
	MethodSet(t)
	fmt.Println("--------------")
	MethodSet(&t)
	//MethodSet(1)
	//t.sVal()
}




```