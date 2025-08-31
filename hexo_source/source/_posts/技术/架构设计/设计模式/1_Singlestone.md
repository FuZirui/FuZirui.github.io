---
title: 单例模式
date: 2025-08-24 12:30:00
updated: 2025-08-24 12:30:00
categories:
- 读书笔记
tags:
- 架构设计
- 设计模式
description: 
author: fuzirui
---

# 类图

```
@startuml
class Singleton {
    - static Singleton* instance
    - Singleton()
    + static Singleton* getInstance()
    + void doSomething()
    - Singleton(const Singleton&)
    - Singleton& operator=(const Singleton&)
}
@enduml
```

# 实现

```
// Singleton.h
#pragma once

class Singleton {
private:
    static Singleton* instance;
    Singleton() {} // 私有构造函数

public:
    static Singleton* getInstance() {
        if (instance == nullptr) {
            instance = new Singleton();
        }
        return instance;
    }

    // 禁止拷贝和赋值
    Singleton(const Singleton&) = delete;
    Singleton& operator=(const Singleton&) = delete;

    void doSomething() {
        // 业务逻辑
    }
};

// 初始化静态成员
Singleton* Singleton::instance = nullptr;
```
