---
title: 自然数
---

- [dialog]

  - 什么是数呢？

  - 数就是数数。

    一、二、三、……

    「数」这个概念，可能就是我们在生活中所识别出来的一个模式吧。

  - 没错，我们应该从零开始，然后数下一个，再下一个……

    下面的定义可以描述这种模式吗？

    ``` cicada
    datatype Nat {
      zero: Nat
      add1(prev: Nat): Nat
    }
    ```

  - `zero` 是「零」，`add1` 是「加一」也就是「数下一个」。

    但是 `datatype`、`Nat` 还有 `prev` 分别是什么意思呢？

  - 我们可以用 `datatype` 来定义数据类型。

    `Nat` 是数据类型名字，代表「自然数 / Natural number」。

    `prev` 代表「前一个 / previous」。

    这里 `zero: Nat` 读做「`zero` 是 `Nat`」。

    猜猜 `add1(prev: Nat): Nat` 怎么读？

  - 我猜它读做「如果 `prev` 是 `Nat`，那么 `add1(prev)` 也是 `Nat`」。

    也就是「如果前一个数是自然数，那么加一还得自然数」。
