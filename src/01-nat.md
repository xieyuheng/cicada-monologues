---
title: 第一章 自然数
---

- [dialog]

  - 欢迎来到数学与编程相交会的奇妙领域！

  - 很开心能知道这样一个领域，给我讲讲其中的故事和历险吧！

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

    `Nat` 是数据类型的名字，代表「自然数」，即 "Natural number"。

    `prev` 代表「前一个」，即 "previous"。

    这花括号中的第一行

    ``` plaintext
    zero: Nat
    ```

    读做「`zero` 是 `Nat`」。

    猜猜第二行

    ``` plaintext
    add1(prev: Nat): Nat
    ```

    怎么读？

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

    就像人有名有姓，构造子也是有名有姓的。
    `zero` 是这个构造子的名，`Nat` 是这个构造子的姓。
    同时用姓和名才能呼唤出这个构造子。

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

  - 是。

    因为 `add1` 是构造 `Nat` 的第二种方式。

  - 其实不是。

    因为 `add1` 代表「加一」，
    「一」是自然数，但是「加一」并不是自然数，
    它是一个对自然数的操作。

    下面这个是 `Nat` 吗？

    ``` cicada
    add1(zero)
    ```

  - 是。

    因为零加一等于一，一是自然数。

  - 这个是 `Nat` 吗？

    ``` cicada
    Nat.add1(Nat.zero)
    ```

  - 是。

    这和 `add1(zero)` 是一样的。

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

  - 是。

    因为 `add1(zero)` 是 `Nat`，
    而如果前一个数是 `Nat`，那么 `add1` 还是 `Nat`。

  - 这个是 `Nat` 吗？

    ``` cicada
    add1(twelve)
    ```

  - 是。

    因为 `twelve` 是 `Nat`，
    而如果前一个数是 `Nat`，那么 `add1` 还是 `Nat`。

    至于 `twelve` 为什么是 `Nat`，
    以此类推就可以了。

  - 像这样的句子

    ``` plaintext
    add1(add1(zero)) 是 Nat
    ```

    还有这样的句子

    ``` plaintext
    add1(twelve) 是 Nat
    ```

    叫做 **断言**。

  - 断言有什么用？

  - 人们通过 **下断言** 来表达自己所相信的事情。
    当我们知道了什么，就会以下断言的方式表达出来。

    关于 `add1(twelve)` 和 `Nat` 我们能断言些什么呢？

  - 我们可以说

    ``` plaintext
    add1(twelve) 是 Nat
    ```

  - 当这么说时，我们同时也在表达

    ``` plaintext
    我相信
      add1(twelve) 是 Nat
    是真的
    ```

  - 也就是说，断言是人对事物的态度。

    人在世界中经验和观察到一些模式，
    然后用语言和符号捕捉到这些模式，
    并且用断言表达出来自己所相信的、所知道的。

  - 不完整的断言，比如

    ``` plaintext
    ＿＿是＿＿
    ```

    叫做 **断言句式**。

    在空缺的部分填入具体的东西，
    就能形成一个具体的断言了。

  - 比如，我们在这两个空中分别填入了 `add1(twelve)` 和 `Nat`。

    填入空格的这些东西，我们也有什么术语可以称呼它们吗？

  - 有。

    我们管这些东西叫 **表达式**。

  - 那么，可以说，
    在不完整的断言中填入具体的表达式，
    就能形成一个具体的断言了。

    除了「＿＿是＿＿」之外，还有其他断言句式吗？

  - 另一个断言句式是

    ``` plaintext
    ＿＿与＿＿是相等的＿＿
    ```

    请问

    ``` cicada
    zero
    ```

    与

    ``` cicada
    zero
    ```

    是相等的

    ``` cicada
    Nat
    ```

    吗？

  - 是。

    它们显然是相等的 `Nat`。

  -
    ``` cicada
    zero
    ```

    与

    ``` cicada
    add1(zero)
    ```

    是相等的

    ``` cicada
    Nat
    ```

    吗？

  - 不是。

    前者是零后者是一，它们是不同的 `Nat`。

    看来这两句话也是断言。

    那么

    ``` plaintext
    add1(zero) 与 add1(zero) 是相等的 Nat
    ```

    也是断言，对吗？

  - 是的，并且我相信它是真的。

    你能看出

    ``` cicada
    "小草莓"
    ```

    与

    ``` cicada
    "小草莓"
    ```

    是相等的

    ``` cicada
    String
    ```

    吗？

  - 我觉得它们应该是相等的，但是 `String` 是什么？

    另外，为什么这两个词写在了英文的双引号中？

  - 当我们把一些字符写在英文双引号中，
    就得到了 **字符串**，即 `String`。

    下面这个是 `String` 吗？

    ``` cicada
    "小草莓"
    ```

  - 是。

    因为「小」、「草」、「莓」这三个字符，写在了英文双引号中。

  - 下面这个是 `String` 吗？

    ``` cicada
    "strawberry"
    ```

  - 也是。

    因为，英文字符也是字符。

  - 下面这些是 `String` 吗？

    ``` cicada
    "abc"
    ```

    ``` plaintext
    abc
    ```

    ``` cicada
    "  "
    ```

    ``` cicada
    ""
    ```

  -
    ``` cicada
    "abc"
    ```

    是 `String`，因为它写在双引号里；

    ``` plaintext
    abc
    ```

    不是 `String`，因为它没写在双引号里；

    ``` cicada
    "  "
    ```

    也是 `String`，因为空格也是字符，
    所以空格写在双引号里就是字符串；

    ``` cicada
    ""
    ```

    我不太确定，这里只有双引号，里面没写字符。

  -
    ``` cicada
    ""
    ```

    也是 `String`，并且我们管它叫 **空字符串**。

    请问

    ``` cicada
    "小草莓"
    ```

    与

    ``` cicada
    "小草莓"
    ```

    是相等的

    ``` cicada
    String
    ```

    吗？

  - 是。

    因为双引号中的字符是对应相等的。

  -
    ``` cicada
    "小草莓"
    ```

    与

    ``` cicada
    "冰淇淋"
    ```

    是相等的

    ``` cicada
    String
    ```

    吗？

  - 不是。

    因为双引号中的字符是不相等的。

- [reminder] 双引号之规则

  - 把一些字符写在英文双引号中，就得到了字符串，即 `String`。

    英文双引号中什么也不写也是字符串，并且叫做空字符串。

- [reminder] 双引号相等之规律

  - 如果两个英文双引号中的全部字符对应相等，
    那么它们就是是相等的 `String`。

- [dialog]

  - 「`"小草莓"` 与 `"冰淇淋"` 是相等的 `String`」是断言吗？

  - 它是断言，但是我不相信这个断言。

  - 你能看出

    ``` cicada inactive
    cons("小草莓", "冰淇淋")
    ```

    是

    ``` cicada
    Pair(String, String)
    ```

    吗？

  - 不能。

    我还不知道什么是 `Pair`，也不知道「＿＿是 `Pair`」意味着什么。

  - `Pair` 是「一对东西」的意思。

    「＿＿是 `Pair(String, String)`」就意味着，
    这对东西的前一个是 `String`，比如 `"小草莓"`，
    并且后一个也是 `String`，比如 `"冰淇淋"`。

    我们管这前一个叫 `car`，后一个叫 `cdr`，
    并且用 `cons` 来构造 `Pair(__, __)`。

  - 好的。

    也就是说 `Pair` 以 `cons` 开头，它有两部分，
    前一部分叫 `car`，后一部分叫 `cdr`。

    这么说来

    ``` cicada inactive
    cons("小草莓", "冰淇淋")
    ```

    确实是

    ``` cicada
    Pair(String, String)
    ```

    因为 `cons("小草莓", "冰淇淋")` 的 `car` 是 `String`，
    并且 `cdr` 也是 `String`。

    那么 `cons` 是 `Pair` 吗？

  - 不是。

    `cons` 是一个语言自带的构造子，它其实就是 "constructor" 缩写。
    我们可以用它来构造 `Pair(__, __)`。

    并且注意，和 `cons` 一样 `Pair` 也是需要两个参数才算完整。

    ``` cicada inactive
    cons("小草莓", "冰淇淋")
    ```

    与

    ``` cicada inactive
    cons("小草莓", "冰淇淋")
    ```

    是相等的

    ``` cicada
    Pair(String, String)
    ```

    吗？

  - 两个表达式是相等的 `Pair(String, String)` 意味着什么呢？

    我们还不知道这一点。

  - 意味着他们的 `car` 是相等的 `String`，
    并且 `cdr` 是相等的 `String`。

  - 这么说来

    ``` cicada inactive
    cons("小草莓", "冰淇淋")
    ```

    与

    ``` cicada inactive
    cons("小草莓", "冰淇淋")
    ```

    确实是相等的

    ``` cicada
    Pair(String, String)
    ```

  -
    ``` cicada inactive
    cons("小草莓", "小草莓")
    ```

    与

    ``` cicada inactive
    cons("小草莓", "冰淇淋")
    ```

    是相等的

    ``` cicada
    Pair(String, String)
    ```

    吗？

  -
    ``` cicada inactive
    cons("小草莓", "小草莓")
    ```

    的 `cdr` 是 `"小草莓"`，而

    ``` cicada inactive
    cons("小草莓", "冰淇淋")
    ```

    的 `cdr` 是 `"冰淇淋"`。

    所以我们不应该相信这个断言。

  - `car` 和 `cdr` 不光是 `Pair` 的前后两个位置名字，
    我们也可以用它们取出一个 `Pair` 前一个或后一个值。

    比如说

    ``` cicada inactive
    car(cons("小草莓", "冰淇淋"))
    ```

    与

    ``` cicada
    "小草莓"
    ```

    是相等的 `String`。

  - 那么

    ``` cicada inactive
    cdr(cons("小草莓", "冰淇淋"))
    ```

    与

    ``` cicada
    "冰淇淋"
    ```

    也是相等的 `String`。

  - 没错。

    关于

    ``` cicada inactive
    cdr(cons("小草莓", "冰淇淋"))
    ```

    我们可以描述些什么？

  - 首先它是一个表达式，并且我们还知道，它是 `String`。

  - `String` 也是一个表达式。

    可以用来描述别的表达式的表达式，叫做 **类型**。

    `Pair(String, String)` 是类型吗？

  - 是。

    因为它是一个表达式，
    并且它可以用来描述前后都是 `String` 的一对东西。

  - 另外，之前用 `datatype` 定义的数据类型，都算是特殊的类型。

    `Nat` 是类型吗？

  - 是。

    因为它是一个表达式，并且它是用 `datatype` 定义的。

  - 第三个断言句式就是

    ``` plaintext
    ＿＿是类型
    ```

  - 这意味着

    ``` plaintext
    String 是类型
    ```

    还有

    ``` plaintext
    Nat 是类型
    ```

    以及

    ``` plaintext
    Pair(String, String) 是类型
    ```

    都是断言。

- [reminder] `String` 之规则

  - `String` 是类型。

- [reminder] `Nat` 之规则

  - `Nat` 是类型。

- [dialog]

  - 「`"小草莓"` 是类型」是断言吗？

  - 它是断言，但是我们没有理由去相信它，
    因为 `"小草莓"` 作为表达式，不能描述别的表达式。

  - `String` 和 `String` 是相等的类型吗？

  - 是的，这很显然。

  - `Nat` 和 `Nat` 是相等的类型吗？

  - 是的，这也很显然。

  - 第四个，也是最后一个，断言句式就是

    ``` plaintext
    ＿＿与＿＿是相等的类型
    ```

  - 这么说

    ``` plaintext
    String 和 String 是相等的类型
    ```

    以及

    ``` plaintext
    Nat 和 Nat 是相等的类型
    ```

    都是断言了。

    并且我们应该相信这两个断言。

- [reminder] 四个断言句式

  - 一、＿＿是＿＿。

    二、＿＿是类型。

    三、＿＿与＿＿是相等的＿＿。

    四、＿＿与＿＿是相等的类型。


- [dialog]

  - 未完待续⋯⋯

  -

  - 还记得 `datatype` 吗？

    用它定义一个新的数据类型试试，好吗？

  - 我可以尝试定义中国文化中的五个主要颜色，
    我用 `Color` 命名这个数据类型，
    它有五个构造子。

    ``` cicada
    datatype Color {
      red: Color
      blue: Color
      yellow: Color
      black: Color
      white: Color
    }
    ```

    然后下面这些就都是 `Color` 了

    ``` cicada
    Color.red
    Color.blue
    Color.yellow
    Color.black
    Color.white
    ```



- [poem-vertical] 通灵者之歌 · 逻辑

  - 黄铜发现自己是唢呐、我有什么办法？
    写程序的人发现自己是通灵者、我也没有办法。

    <div style="display: inline; font-weight: 700; color: #ef4444;">与红、</div>
    <div style="display: inline; font-weight: 700; color: #0ea5e9;">或蓝、</div>
    <div style="display: inline; font-weight: 700; color: #facc15;">非黄、</div>
    <div style="display: inline; font-weight: 700; color: #1c1917;">任黑、</div>
    <div style="display: inline; font-weight: 700; color: #d6d3d1;">有白。</div>

    他声称自己发明了逻辑的色彩。

    <div style="display: inline; color: #ef4444;">
    与。朱红的宫墙外、醉妓胭脂妆面、梦与帝相伴。
    </div>

    <div style="display: inline; color: #0ea5e9;">
    或。故乡的海岸边、旅人初返、或默或语、出神回望天边。
    </div>

    <div style="display: inline; color: #facc15;">
    非。杨树林边的小沙滩、傻乎乎的小孩子嬉戏着沙丘、不惧暮色，也不想回家吃饭。
    </div>

    <div style="display: inline; color: #1c1917;">
    任。深山的道观前、侠客持剑拾级而上、誓要将所有作乱的妖魔斩于殿前。
    </div>

    <div style="display: inline; color: #d6d3d1;">
    有。安静的咖啡馆里、沐浴着午后的阳光、有位通灵者、嘴里含着甜甜的牛轧糖、轻轻地敲着键盘。
    </div>
