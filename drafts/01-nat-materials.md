---
title: 第一章 自然数 材料
---

```cicada
function add(x: Nat, y: Nat): Nat {
  return induction (x) {
    case zero => y
    case add1(_prev, almost) => add1(almost.prev)
  }
}
```

```cicada
function mul(x: Nat, y: Nat): Nat {
  return induction (x) {
    case zero => zero
    case add1(_prev, almost) => add(almost.prev, y)
  }
}

mul(two, two)
```

```cicada
// NOTE We need to keep the `target` the first argument,
//   because partial evaluation relys on it.

function power_of(x: Nat, y: Nat): Nat {
  return induction (x) {
    case zero => one
    case add1(_prev, almost) => mul(almost.prev, y)
  }
}

function power(base: Nat, n: Nat): Nat {
  return power_of(n, base)
}
```

```cicada
function gauss(n: Nat): Nat {
  return induction (n) {
    case zero => zero
    case add1(prev, almost) =>
      add(add1(prev), almost.prev)
  }
}

gauss(zero)
gauss(one)
gauss(two)
gauss(three)
gauss(four)
gauss(five)
gauss(six)
gauss(seven)
gauss(eight)
gauss(nine)
gauss(ten)
```

```cicada
function factorial(n: Nat): Nat {
  return induction (n) {
    case zero => one
    case add1(prev, almost) =>
      mul(add1(prev), almost.prev)
  }
}

factorial(zero)
factorial(one)
factorial(two)
factorial(three)
factorial(four)
factorial(five)
factorial(six)
```
