---
title: 数
date: 2021-12-22
---

# Nat

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
