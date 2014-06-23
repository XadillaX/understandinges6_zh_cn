# 符号 (Symbols)

> 本章还在实施中。所以比其它章节会有更多的错别字或者内容错误。

ECMAScript 6 中符号开始作为一种创建私有对象成员的方式——一个 JavaScript 程序员所梦寐以求的特性。它着重于创建那些不是由字符串命名的属性。任何拥有字符串标识符的属性都是可以被轻而易举被外界访问到，即使它的名字破破烂烂的。最初的“私有名 (Private Names)”功能就是创建属性的非字符串名字。如此一搞，正常的科技（黑科技除外）是无法侦测到这些私有名的。

值得高兴的是，私有名的建议最终被采纳然后在 ECMAScript 6 中变成了符号 (Symbols)。它的细则实施仍然保持不变（属性标识符为一个非字符串的值），TC-39 放弃了这些属性要变成私有的需求——这些属性转而将会被另外分类，仍可被发现但是默认情况下不可被枚举。

符号 (Symbols) 实际上是一种新的基本值，加入字符串、数字、布尔类型、`null` 以及 `undefined`。它们在 JavaScript 基本类型中很特殊，因为他们没有文字形式。在 ECMAScript 6 标准中使用了一种特殊的形式来表示符号——使用 `@@` 作为标识符的前缀，如 `@@create`。为了便于理解，本书使用相同的约定。

> 尽管有前缀，符号并不确切映射到以 `@@` 开头的字符串。你不要妄想着在需要用符号的时候使用字符串的值来替代。

## 创建符号

TODO

## 检测符号类型

TODO

## 使用符号

TODO

## 共享符号

TODO

## 找到对象符号

TODO

## 广知符号

TODO

### @@toStringTag

TODO

### @@toPrimitive

TODO

### @@isConcatSpreadable

TODO

### @@unscopeables

TODO

### @@isRegExp

TODO

### @@iterator

TODO

### @@create

TODO

### @@hasInstance

TODO

## 摘要

TODO
