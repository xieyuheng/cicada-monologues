---
title: 第一章 引子
date: 2021-12-16
---

「夏天。夏天来了吗？」

他轻轻把头从地里钻出来，一边环顾四周一边自言自语。

周围是一片杨树林。

他是一只蝉。

「还早呢，现在才一月。」

答他话的是一只褐色的蝴蝶，不仔细看还以为是一片枯叶。

# 说数

``` cicada
datatype Nat {
  zero: Nat
  add1(prev: Nat): Nat
}
```

``` cicada
Nat

Nat.zero
Nat.add1

Nat.add1(Nat.zero)
Nat.add1(Nat.add1(Nat.zero))
```
