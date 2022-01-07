---
title: 第一章 自然数
---

- [dialog]

  - 什么是数呢？

  - 数就是数数。

    一、二、三、⋯⋯

    「数」这个概念，可能就是我们在生活中所识别出来的一个模式吧。

  - 没错，在很多的经验中，我们都会发现一个很自然的序关系。

    我们应该从零开始，然后数下一个，再下一个⋯⋯

    下面的定义可以描述这种模式吗？

    ``` cicada
    datatype Nat {
      zero: Nat
      add1(prev: Nat): Nat
    }
    ```

  - `zero` 代表「零」，`add1` 代表「加一」也就是「数下一个」。

    但是 `datatype`、`Nat` 还有 `prev` 分别是什么意思呢？

  - 我们可以用 `datatype` 来定义数据类型。

    `Nat` 是数据类型名字，代表「自然数 / Natural number」。

    `prev` 代表「前一个 / previous」。

    这花括号中的第一行 `zero: Nat` 读做「`zero` 是 `Nat`」。

    猜猜第二行 `add1(prev: Nat): Nat` 怎么读？

  - 我猜它读做「如果 `prev` 是 `Nat`，那么 `add1(prev)` 也是 `Nat`」。

    也就是说，如果前一个数是自然数，那么加一还得自然数。

- [reminder] 定义数据类型

  - 用 `datatype` 来定义数据类型，
    给所要定义的数据类型取个名字，
    然后在花括号中罗列构造数据的方式。

- [dialog]

  - 没错。

    构造数据的方式叫做 **构造子**。

    比如，`Nat` 有两个构造子，分别是 `zero` 和 `add1`。

    你能看出来，下面这个东西是 `Nat` 吗？

    ``` cicada
    Nat.zero
    ```

  - 为什么呢？

    不是说 `zero` 是 `Nat` 吗？

    为什么这里写的是 `Nat.zero` ?

  - 因为这个 `zero` 是就 `Nat` 而言的。

    就像人有名有姓，
    `zero` 是这个东西的名，
    `Nat` 是这个东西的姓。

    同时用姓和名才能呼唤出这个东西。

    就像我们人间世一样，人不只有名，还有姓，
    以帮助我们理解人和人之间的关系。

    在形式语言里，有时也是如此。

  - 这么说来，只有 `Nat.zero` 是 `Nat`，而 `zero` 不是 `Nat`？

  - 没错，`zero` 目前还没有意义。

    但是我们可以用 `let` 赋予它意义

    ``` cicada
    let zero = Nat.zero
    ```

    在这之后 `zero` 就是 `Nat` 了。

    我们还可以对 `add1` 做类似的赋值

    ``` cicada
    let add1 = Nat.add1
    ```

    `add1` 是 `Nat` 吗？

  - 是，因为 `add1` 是构造 `Nat` 的第二种方式。

  - 其实不是，因为 `add1` 代表「加一」，
    「一」是自然数，但是「加一」并不是自然数，
    它是一个对自然数的操作。

    下面这个是 `Nat` 吗？

    ``` cicada
    add1(zero)
    ```

  - 是，因为零加一是一，一是自然数。

  - 这个是 `Nat` 吗？

    ``` cicada
    Nat.add1(Nat.zero)
    ```

  - 是，这和 `add1(zero)` 是一样的。

- [reminder] 赋值

  - 用 `let` 来做赋值，首先给出所要赋值的名字，然后给出值。
    赋值之后，这个名字就可以代替这个值了。

- [dialog]

  - 像给 `zero` 赋值一样，给从一到十的数的英文名赋值。

  - 应该是这样

    ``` cicada
    let one = add1(zero)
    let two = add1(one)
    let three = add1(two)
    let four = add1(three)
    let five = add1(four)
    let six = add1(five)
    let seven = add1(six)
    let eight = add1(seven)
    let nine = add1(eight)
    let ten = add1(nine)
    let eleven = add1(ten)
    let twelve = add1(eleven)
    ```

    我还定义了 `eleven` 和 `twelve`，
    也许之后用得到呢！

  - 这个是 `Nat` 吗？

    ``` cicada
    add1(add1(zero))
    ```

  - 是，因为 `add1(zero)` 是 `Nat`，
    而如果前一个数是 `Nat`，那么 `add1` 还是 `Nat`。

  - 这个是 `Nat` 吗？

    ``` cicada
    add1(twelve)
    ```

  - 是，因为 `twelve` 是 `Nat`，
    而如果前一个数是 `Nat`，那么 `add1` 还是 `Nat`。

    至于 `twelve` 为什么是 `Nat`，
    以此类推就可以了。

  - 像这样的句子

    ``` plaintext
    add1(add1(zero)) 是 Nat
    ```

    还有

    ``` plaintext
    add1(twelve) 是 Nat
    ```

    叫做 **判断**。

  - 判断有什么用？

- [poem-vertical] 通灵者之歌 · 逻辑

  - 黄铜发现自己是唢呐，我有什么办法？
    写编程的人发现自己是通灵者，我也没有办法。

    <div style="display: inline; font-weight: 700; color: #ef4444;">与红、</div>
    <div style="display: inline; font-weight: 700; color: #0ea5e9;">或蓝、</div>
    <div style="display: inline; font-weight: 700; color: #facc15;">非黄、</div>
    <div style="display: inline; font-weight: 700; color: #1c1917;">任黑、</div>
    <div style="display: inline; font-weight: 700; color: #d6d3d1;">有白。</div>

    他声称自己发明了逻辑的色彩。

    <div style="display: inline; font-weight: 700; color: #ef4444;">与、朱红的宫墙外、醉妓胭脂装面、梦与帝相伴。</div>

    <div style="display: inline; font-weight: 700; color: #0ea5e9;">或、故乡的海岸边、旅人初返、或默或语、出神回望天边。</div>

    <div style="display: inline; font-weight: 700; color: #facc15;">非、杨树林边的小沙滩、傻乎乎的小孩嬉戏着沙丘、不惧暮色，也不想吃饭。</div>

    <div style="display: inline; font-weight: 700; color: #1c1917;">任、深山的道观前、侠客持剑拾级而上、誓要将所有作乱的妖魔斩于殿前。</div>

    <div style="display: inline; font-weight: 700; color: #d6d3d1;">有、安静的咖啡馆里、沐浴着午后的阳光、有位通灵者、嘴里含着甜甜的牛轧糖、轻轻地敲着键盘。</div>
