# 零基础教程

> A language that doesn't affect the way you think about programming, is not worth knowing. --- Alan J. Perlis

> 如果一门语言无法对你的编程思想造成影响，那么它不值得你去了解 --- Alan J. Perlis

## 絮叨

在阅读本文之前，你可能已经学习过其它程序设计语言

Clojure 也许与你接触过的语言有很大的不同

无论如何，请忘记它们

## 为什么选择 Clojure

传奇语言 Lisp 的一门方言 ，简洁而优雅<span id="fn_link_lisp">[ [1] ](#lisp)</span>。

可以方便地与 Java 进行交互：

Clojure 运行于 JVM<span id="fn_link_jvm">[ [2] ](#jvm)</span> 之上<span id="fn_link_an">[ [3] ](#an)</span>，这表示你可以直接使用庞大丰富的 Java 库，而 Java 程序也可以反过来调用 Clojure 代码。使得你在 Java 平台上投入的精力不被浪费。

## Clojure 能做什么

虽然理论上来说，任何一个完备的程序设计语言，在功能上都是相等的<span id="fn_link_turing-equivalent">[ [4] ](#turing-equivalent)</span>，也就是说，A 语言可以做到的事情 B 语言一样可以做到。

但是每一种语言是有自己擅长的领域的，语言的特性决定了其领域。

C / C++ 就比较适合开发一些对效率要求很高的东西。（比如图形引擎，操作系统）

而 Java 则适合用来做后台服务器。（或者写一个 Android 程序，感谢 Android 实现了 Java ME<span id="fn_link_j2me">[ [5] ](#j2me)</span>未竟之事）

Clojure 则借助于 Lisp 得天独厚的优势，提供了解决复杂问题的优雅解决途径：

1. 使用函数式编程，来大大简化你的程序，提高开发效率。

1. 通过宏这种强大的工具，使得你可以编写属于你自己的领域特定语言。 (DSL <span id="fn_link_dsl">[ [6] ](#dsl)</span>)

1. 同时由于她的不可变特性，以及提供了一些处理多线程的操作，在处理并发时 Clojure 也能显露优势。

我们并不指望你可以一下子感受到语言之间的异同，但是大概的意思是想让你明白，Clojure 作为一门 Lisp 方言，以强大的表达能力著称， 使之能以更优雅的方式来解决问题。

并不是在贬低其它语言不够优雅，而是这是事实。（雾）（说完就被打了）在今后的学习中，你会逐渐感受到这种优势带给你的便捷。


## 为什么 Clojure / Lisp 没有流行

流行只代表着它的使用者很多，与它本身的优秀与否不存在简单的关联。

流行很大程度上与历史情况有关，在 Lisp 刚刚诞生的时候，计算机的运行速度很慢，这导致使用垃圾自动回收、动态特性的 Lisp 的运行速度非常缓慢。

在其之后的诞生的语言 --- 如C，其运行速度和其易用性的平衡，在当时的计算机上达 到了一个相当高的水平，从而成为了一种真正实用的程序设计语言。

而流行这种东西类似“滚雪球”，使用者越滚越多，一旦确立其地位就很难被取代。

原因可能是你的老板认为，招收使用人数较多的程序员更保险一些，或者随大流的使用别人使用的技术。

Java 的流行则得益于成功的商业运作（以及借用了一大堆 Lisp 系统的技巧和特性，还简化了 C++ 里一些晦涩的用法），虽然在当时 Java 的速度还远比不上 C 或者 C++。

随着计算机运行速度的提高，动态语言的执行速度已经可以接受，于是一批表达能力更强的语言诞生了（如Python，Ruby，JavaScript），牺牲了少许在可接受范围内的性能，而得到了更为自然流畅的编程体验，这些语言自然受到了程序员的欢迎。要知道程序员（可能）是地球上最懒的一群人。

而 Lisp 无论从思想上，还是形式上，都是程序语言界的奇葩。这导致了程序员在其它设计语言上投入的精力，无法直接帮助他们学习 Lisp 语言，从而大大的提高了 Lisp 语言的学习成本。（好吧，我承认你在其它函数式语言上的投入也许会帮助你）

由于刚才我们说过，程序员（可能）是地球上最懒的一群人，所以 Lisp 的流行障碍就非常之大了。（但事实上，了解 Lisp 思想对使用其它语言的程序员来说也有益处。）

Clojure 作为一门 Lisp 方言，上述讨论同样适用。


## 如何部署 Clojure 运行环境

最“傻瓜式”的方式是下载安装 Eclipse 或者 IDEA 之类的集成开发环境，然后再安装对应的插件，这样就可以一次性获得到一整套环境。

* Eclipse 插件 [Counterclockwise](https://marketplace.eclipse.org/content/counterclockwise)
* IDEA 插件 [Cursive](https://cursive-ide.com/)

如果你觉得 IDE 过于笨重，或者现在只是想简单的体验一把，不想做复杂的安装，那么你只需下载一个仅有几 MB 大小的 jar 包，执行一行指令，便可在命令行使用 Clojure。


## 如何运行 Clojure 程序

Clojure 与 其它 Lisp 方言一样，提供了一个称之为 REPL 的环境，即 Read-Eval-Print Loop --- “读取-求值-输出” 循环

* 读取：读取一段输入的代码
* 求值：求取这段代码的值
* 输出：显示出这个值
* 循环：继续等待下一段代码的输入

它是一个交互式的执行环境，使得你编写出一段 Clojure 代码之后，即可立即执行它！

而无需等到全部代码编写完毕之后运行

Clojure 程序是由一句一句的表达式构成的，你可以把一系列表达式写在文件里，在你需要的时候一次性执行完毕，也可以一句一句的输入进 `REPL` 里执行。

不用担心一句一句解释执行的效率不如一次性执行，两者的执行效率是相同的

## 文档

你可以访问 [http://clojuredocs.org/](http://clojuredocs.org/) 查阅 API 的小例子
也可以访问官方网站 [http://clojure.github.io/clojure/](http://clojure.github.io/clojure/) 来直接查阅官方 API 说明
英文苦手们可以访问官方 API 文档翻译项目
[http://clojure-api-cn.readthedocs.io/en/latest/](http://clojure-api-cn.readthedocs.io/en/latest/)


## 附录

<span id="lisp">[1]</span>: Lisp 黑客精神可以用两句话来概括：编程应该是有趣的。程序应该是优美的。（摘自[ANSI Common Lisp 中文版](http://acl.readthedocs.io/en/latest/zhCN/preface-cn.html#id2)） [↩](#fn_link_lisp)

<span id="jvm">[2]</span>: Java Virtual Machine，即 Java 虚拟机。简单来说就是运行在真实操作系统上的又一层操作系统。程序不直接在系统上运行，而是在虚拟的系统上运行，以此来实现跨平台。（想想电影 黑客帝国 中的场景） [↩](#fn_link_jvm)

<span id="an">[3]</span>: 也同时存在运行在其它平台上的 Clojure 版本，如 ClojureScript 是一个可以把 Clojure 代码编译成 JavaScript 可执行的编译器。Clojure CLR 是一个运行在 DLR 平台上的版本 [↩](#fn_link_an)

<span id="turing-equivalent">[4]</span>: 准确来说是“图灵等价”的。图灵等价的详细意义请点击[这里](http://www.cnblogs.com/lexus/archive/2012/08/21/2648810.html)查阅。 [↩](#fn_link_turing-equivalent)

<span id="j2me">[5]</span>: Java Platform, Micro Edition. 即 Java 精简版。被设计用于小型设备的 Java 环境。 [↩](#fn_link_j2me)

<span id="dsl">[6]</span>: 领域特定语言（domain-specific languages，简称[DSL](http://www.baike.com/wiki/%E9%A2%86%E5%9F%9F%E7%89%B9%E5%AE%9A%E8%AF%AD%E8%A8%80)），简单来说就是你可以自己设计一套语法，以适应你需要处理的问题。 [↩](#fn_link_dsl)

