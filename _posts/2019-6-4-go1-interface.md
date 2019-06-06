---
layout:post
title: interface设计原则
category: blog
decription: golang--interface设计原则
---

1. interface 是方法声明的集合；
2. 任何类型的对象实现了在interface接口中声明的全部方法，则表明该类型实现了该接口；
3. interface 可以作为一种数据类型，实现了该接口的任何对象都可以给对应的接口类型变量赋值。

```
package main

import "fmt"

type Phone struct {
    call()
}

type ChrysanthemumPhone struct {

}

func (c Chrysanthemum) call() {
    fmt.Println("chrysanthemum)
}

func IPhone struct {

}

func (i Iphone) call() {
    fmt.Println("iphone)
}

func main() {
    var phone Phone
    phone = new(ChrysanthemumPhone)
    phone.call()
    phone = new(IPhone)
    phone.call()

}

```

一. 平铺的模块设计

```
package main

import "fmt"

type Banker struct {

}

func (b *Banker) Save() {
	fmt.Println("save")
}

func (b *Banker) Transfer() {
	fmt.Println("transfer")
}

func (b *Banker) Pay() {
	fmt.Println("pay")
}

func main() {
	banker := Banker{}
	banker.Save()
	banker.Pay()
	banker.Transfer()
}


```

```
type AbstractBanker interface {
    DoBuSi()
}

type SaveBanker struct {

}

func (s *SaveBanker)DoBuSi() {
    //todo
    println("save)
}

type TransferBanker struct {

}

func (t *TransferBanker)DoBuSi() {
    //
    println("transfer)
}

type PayBanker struct {

}

func (p *PayBanker)DoBuSi() {
    //
    println("pay")
}

func BankerBussiness (banker AbstractBanker) {
    banker.DoBuSi()
}

func main() {
    BankerBussiness(&SaveBanker{})
    BankerBussiness(&TransferBanker{})
    BankerBussiness(&PayBanker{})
}

```

二. 面向抽象层依赖倒转
```
type Car interface {
    Run()
}

type Driver interface {
    Dirve(car Car)
}

type BenZ struct {

}

func (benz *BenZ)Run(){

}

type Bmw struct {

}

func (bmw *Bmw)Run() {

}

type Zhang_3 struct {

}

func (z *Zhang_3)Drive(car Car) {
    car.Run()
}

func main(){
    var bmw Car
    bmw = &Bmw{}

    var zhang Driver
    zhang = &Zhang_3{}

    zhang.Drive(bmw)

}
```