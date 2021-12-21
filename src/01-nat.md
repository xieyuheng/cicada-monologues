---
title: 数
date: 2021-12-22
---

什么是数呢？

还记得很小很小的时候，在一个安静的夜里，和爷爷一起学数数。

一、二、三、四、五、六、七、八、九、十、十一……

我能数到一百，感觉自己好厉害。

上小学的时候，学会了加、减、乘、除，也知道了「零」也很重要。

大学读了数学专业，学到了很多更高阶、更抽象的概念，却还是时不时地自问，

> 什么是数呢？

「数」这个概念，可能就是我们在生活中所识别出来的一个模式吧。

在很多的经验中，我们都会发现一个很自然的序关系，从「零」开始，然后数下一个，再下一个……

我们可以在蝉语中，定义一个数据类型，来捕捉「自然数」这个概念试试。

- 我们用 `datatype` 这个语句来定义数据类型；
- 「自然数」的英文叫做 "Natural number"，所以我用 `Nat` 这个缩写来命名这个数据类型。

``` cicada
datatype Nat {
  zero: Nat
  add1(prev: Nat): Nat
}
```

定义好啦！

有两种方式来构造 `Nat` 的元素：

- 首先是「零 / `zero`」

  `zero: Nat` 的意思就是，`zero` 是一个自然数。

- 其次是「加一 / `add1`」

  `add1(prev: Nat): Nat` 的意思就是，如果前一个数是一个自然数，
  那么「加一」上去之后还是一个自然数。

  - 这里 "prev" 是英语 "previous" 的缩写，意思是「前一个」。

将「零、一、二、三」在蝉语中写出来试试，

``` cicada
Nat.zero
Nat.add1(Nat.zero)
Nat.add1(Nat.add1(Nat.zero))
Nat.add1(Nat.add1(Nat.add1(Nat.zero)))
```

上面的代码块是可以运行的。

点击右上角的按钮，然后按 "RUN" 就可以运行了。

不过这里还不涉及到任何运算，所以运行的结果，就是这些数本身。

下面，我们试试用 `let` 这个语句来做定义，来给一些常用到的数以名字。

``` cicada
let zero = Nat.zero
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

大家还记得英文数字的拼写吗？
有时候我会忘记「十二」是 "twelve"，还要查一下，哈哈哈。

定义好了之后，输入这些名字，就可以打印出来对应的值了，比如，

``` cicada
one
two
three
```

未完待续……