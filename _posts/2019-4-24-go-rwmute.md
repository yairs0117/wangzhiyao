---
layout:     post
title:      golang--锁
category: blog
description: Mutex RWMutex
---

sync包实现了两种锁

### Mutex 互斥锁
1.  Mutex 为互斥锁，Lock()加锁， Unlock()解锁；
2.  在一个goroutine获得Mutex后，其他goroutine只能等这个goroutine释放该Mutex
3.  使用Lock()加锁后，不能再继续对其加锁，直到利用Ulock()解锁后才能再加锁
4.  在Lock()之前使用Unlock()会导致panic异常
5.  已经锁定的Mutex并不与特定的goroutine相关联，这有可以使用一个goroutine对其加锁,再利用其他的goroutine对其解锁
6.  在同一个goroutine中的Mutex解锁之前在进行加锁，会导致死锁
7.  适用于读写不确定，并且只有一个读或写的场景

### RWMutex 读写锁 RWMutex基于Mutex实现
1.  RWMutex是单写多读锁,该锁可以加多个读锁或者一个写锁
2.  读锁占用的情况下会阻止写，不会阻止读，多个goroutine可以同时获取读锁
3.  写锁会阻止其他goroutine（无论读和写)进来，整个锁由该goroutine独占
4.  适用于读多写少的场景


### Lock()和Unlock()
1.  Lock()加写锁，Unlock()解写锁
2.  如果在加写锁之前已经由其他的读锁和写锁，则Lock()会阻塞直到该锁可用，为确保该锁可以用，已经阻塞的Lock()调用会从获得的锁中排除新的读取器，即写锁权限高于读锁，有写锁时优先进行写锁定。
3.  在Lock()之前使用Unlock()会导致panic异常

### RLock 和 RUnlock()
1.  RLock()加读锁，RUnlock()解读锁
2.  RLock()加读锁时，如果存在写锁，则无法加读锁，当只有读锁或着没有琐时，可以加读锁，读锁可以加载多个
3.  在没有读锁的情况下调用RUnlock()会导致panic错误
4.  RUnlock()的个数不得多余RLock(),否则会导致panic错误









